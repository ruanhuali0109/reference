# Nix package manager language
  
Learn Nix can help you control Nix package manager and NixOS in easy way
that you can ever dream. Throw other things like Docker, Snap, portage,
Flatpak away, you have free thing. It is called Nix.
  
## Data Types

### Primitives

+ String: start and end with `"` or double quote `''`
  
Some examples
```nix
"--with-freetype2-library=" + freetype + "/lib"

"--with-freetype2-library=${freetype}/lib"

  configureFlags = "
    -system-zlib -system-libpng -system-libjpeg
    ${if openglSupport then "-dlopen-opengl
      -L${mesa}/lib -I${mesa}/include
      -L${libXmu}/lib -I${libXmu}/include" else ""}
    ${if threadSupport then "-thread" else "-no-thread"}
  ";

  postInstall =
    ''
      mkdir $out/bin $out/etc
      cp foo $out/bin
      echo "Hello World" > $out/etc/foo.conf
      ${if enableBar then "cp bar $out/bin" else ""}
    '';
```

+ Number: integers like `123` or floating point `123.43` or `.27e13`
  
+ Path: A path must contain at least one slash to be recognised.
  
For example `/home/nixuser` or `~/`. `/home/nixuser` is equal to `~/`.
  
It can also be specified between angle brackers `<nixpkgs>`. This means that
the directories listed in the environment variable `NIX_PATH` will be searched
for the given file or directory name.
 
Antiquotation is supported in any paths except those in angle brackets.
`./${foo}-${bar}.nix` is a more convenient way of writing
`./. + "/" + foo + "-" + bar + ".nix"` or `./. + "/${foo}-${bar}.nix"`.
At least one slash must appear before any antiquotations for this to be
recognized as a path. `a.${foo}/b.${bar}` is a syntactically valid division
operation. `./a.${foo}/b.${bar}` is a path.

+ Boolean: `true` or `false`
  
+ Null: mean nothing, denoted as `null`

### List
  
Lists are formed by enclosing a whitespace-separated list of values between
square brackets. For example
```nix
[ 123 ./foo.nix "abc" (f { x = y; }) ]
```
defines a list of four elements, the last being the result of a call to the
function f. Note that function calls have to be enclosed in parentheses.
If they had been omitted, e.g.,
```nix
[ 123 ./foo.nix "abc" f { x = y; } ]
```
the result would be a list of five elements, the fourth one being a function
and the fifth being a set.

Note that lists are only lazy in values, and they are strict in length.
  
### Attribute Set
  
An attribute set is a collection of name-value-pairs (called attributes)
enclosed in curly brackets (`{ }`).
  
Names and values are separated by an equal sign (`=`). Each value is an
arbitrary expression terminated by a semicolon (`;`).
  
Attributes can appear in any order. An attribute name may only occur once.
  
Example:
```nix
{
  x = 123;
  text = "Hello";
  y = f { bla = 456; };
}
```
  
This defines a set with attributes named `x`, text, `y`.
  
Attributes can be selected from a set using the . operator. For instance,
  
```nix
{ a = "Foo"; b = "Bar"; }.a
```
  
evaluates to `"Foo"`. It is possible to provide a default value in an
attribute selection using the `or` keyword. For example,
  
```nix
{ a = "Foo"; b = "Bar"; }.c or "Xyzzy"
```
  
will evaluate to `"Xyzzy"` because there is no `c` attribute in the set.
  
You can use arbitrary double-quoted strings as attribute names:
  
```nix
{ "foo ${bar}" = 123; "nix-1.0" = 456; }."foo ${bar}"
```
  
This will evaluate to `123` (Assuming `bar` is antiquotable). In the case
where an attribute name is just a single antiquotation, the quotes can be
dropped:
  
```nix
{ foo = 123; }.${bar} or 456
```
  
This will evaluate to `123` if `bar` evaluates to `"foo"` when coerced to a
string and 456 otherwise (again assuming bar is antiquotable).
  
In the special case where an attribute name inside of a set declaration
evaluates to `null` (which is normally an error, as null is not antiquotable),
that attribute is simply not added to the set:
  
```nix
{ ${if foo then "bar" else null} = true; }
```
  
This will evaluate to `{}` if foo evaluates to `false`.

A set that has a `__functor` attribute whose value is callable (i.e. is itself
a function or a set with a `__functor` attribute whose value is callable) can
be applied as if it were a function, with the set itself passed in first, e.g.,
  
```nix
let add = { __functor = self: x: x + self.x; };
    inc = add // { x = 1; };
in inc 1
```
  
evaluates to `2`. This can be used to attach metadata to a function without the
caller needing to treat it specially, or to implement a form of object-oriented
programming, for example.

## Language Constructs
  
### Recursive sets
  
Recursive sets are just normal sets, but the attributes can refer to each
other. For example,
```nix
rec {
  x = y;
  y = 123;
}.x
```
evaluates to `123`. Note that without `rec` the binding `x = y;` would refer to
the variable `y` in the surrounding scope, if one exists, and would be invalid
if no such variable exists. That is, in a normal (non-recursive) set,
attributes are not added to the lexical scope; in a recursive set, they are.
  
Recursive sets of course introduce the danger of infinite recursion.
For example, the expression
```nix
rec {
  x = y;
  y = x;
}.x
```
will crash with an `nfinite recursion encountered` error message.
  
## Let-expressions
  
A let-expression allows you to define local variables for an expression.
For instance,
```nix
let
  x = "foo";
  y = "bar";
in x + y
```
evaluates to `"foobar"`.
  
## Inheriting attributes
  
When defining a set or in a let-expression it is often convenient to copy
variables from the surrounding lexical scope (e.g., when you want to
propagate attributes). This can be shortened using the `inherit` keyword.
For instance,
```nix
let x = 123 in
{ inherit x;
  y = 456;
}
```
is equivalent to
```nix
let x = 123; in
{ x = x;
  y = 456;
}
```
and both evaluate to `{ x = 123; y = 456; }`. (Note that this works because
x is added to the lexical scope by the `let` construct.) It is also possible to
inherit attributes from another set. For instance, in this fragment from
`all-packages.nix`,
```nix
graphviz = (import ../tools/graphics/graphviz) {
  inherit fetchurl stdenv libpng libjpeg expat x11 yacc;
  inherit (xlibs) libXaw;
};

xlibs = {
  libX11 = ...;
  libXaw = ...;
  ...
}

libpng = ...;
libjpg = ...;
...
```
  
the set used in the function call to the function defined in
`../tools/graphics/graphviz` inherits a number of variables from the
surrounding scope (`fetchurl` ... `yacc`), but also inherits `libXaw` (the
X Athena Widgets) from the `xlibs` (X11 client-side libraries) set.
  
Summarizing the fragment
```nix
...
inherit x y z;
inherit (src-set) a b c;
...
```
  
is equivalent to
```nix
...
x = x; y = y; z = z;
a = src-set.a; b = src-set.b; c = src-set.c;
...
```
  
when used while defining local variables in a let-expression or while defining
a set.
      

## Functions
  
Functions have the following form:
```
pattern: body
```
  
The pattern specifies what the argument of the function must look like, and
binds variables in the body to (parts of) the argument. There are three kinds of patterns:

+ If a pattern is a single identifier, then the function matches any argument.
Example:
```nix
let negate = x: !x;
    concat = x: y: x + y;
in if negate true then concat "foo" "bar" else ""
```

  
## Comments
  
Comments can be single-line, started with a `#` character, or
inline/multi-line, enclosed within `/* ... */`.

## Reference
  
[Nix language](https://nixos.org/manual/nix/stable/language/index.html)
