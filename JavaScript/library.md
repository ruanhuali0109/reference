## JavaScript Standard Library
  
### Arrays
  
There are different methods to manipulate an array. These are some of the
available methods to deal with arrays:Array, length, concat, indexOf, slice,
splice, join, toString, includes, lastIndexOf, isArray, fill, push, pop, shift,
unshift

#### Array Constructor
Array:To create an array.
```js
const arr = Array() // creates an an empty array
console.log(arr)

const eightEmptyValues = Array(8) // it creates eight empty values
console.log(eightEmptyValues) // [empty x 8]
```
  
#### Creating static values with fill
fill: Fill all the array elements with a static value
```js
const arr = Array() // creates an an empty array
console.log(arr)

const eightXvalues = Array(8).fill('X') // it creates eight element values filled with 'X'
console.log(eightXvalues) // ['X', 'X','X','X','X','X','X','X']

const eight0values = Array(8).fill(0) // it creates eight element values filled with '0'
console.log(eight0values) // [0, 0, 0, 0, 0, 0, 0, 0]

const four4values = Array(4).fill(4) // it creates 4 element values filled with '4'
console.log(four4values) // [4, 4, 4, 4]
```
  
#### Concatenating array using concat
concat:To concatenate two arrays.
```js
const firstList = [1, 2, 3]
const secondList = [4, 5, 6]
const thirdList = firstList.concat(secondList)

console.log(thirdList) // [1, 2, 3, 4, 5, 6]
const fruits = ['banana', 'orange', 'mango', 'lemon']                 // array of fruits
const vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot'] // array of vegetables
const fruitsAndVegetables = fruits.concat(vegetables)                 // concatenate the two arrays

console.log(fruitsAndVegetables)
["banana", "orange", "mango", "lemon", "Tomato", "Potato", "Cabbage", "Onion", "Carrot"]
Getting array length
Length:To know the size of the array

const numbers = [1, 2, 3, 4, 5]
console.log(numbers.length) // -> 5 is the size of the array
```
  
#### Getting index an element in arr array
indexOf:To check if an item exist in an array. If it exists it returns the index else it returns -1.
```js
const numbers = [1, 2, 3, 4, 5]

console.log(numbers.indexOf(5)) // -> 4
console.log(numbers.indexOf(0)) // -> -1
console.log(numbers.indexOf(1)) // -> 0
console.log(numbers.indexOf(6)) // -> -1
```
    
Check an element if it exist in an array.
  
+ Check items in a list
```js
// let us check if a banana exist in the array
const fruits = ['banana', 'orange', 'mango', 'lemon']
let index = fruits.indexOf('banana')  // 0
if(index === -1){
   console.log('This fruit does not exist in the array')  
} else {
    console.log('This fruit does exist in the array')
}
// This fruit does exist in the array
// we can use also ternary here
index === -1 ? console.log('This fruit does not exist in the array'): console.log('This fruit does exist in the array')
// let us check if an avocado exist in the array
let indexOfAvocado = fruits.indexOf('avocado')  // -1, if the element not found index is -1
if(indexOfAvocado === -1){
    console.log('This fruit does not exist in the array')  
} else {
    console.log('This fruit does exist in the array')
}
// This fruit does not exist in the array
```
  
#### Getting last index of an element in array
lastIndexOf: It gives the position of the last item in the array. If it exist,
it returns the index else it returns -1.
```js
const numbers = [1, 2, 3, 4, 5, 3, 1, 2]

console.log(numbers.lastIndexOf(2)) // 7
console.log(numbers.lastIndexOf(0)) // -1
console.log(numbers.lastIndexOf(1)) //  6
console.log(numbers.lastIndexOf(4)) //  3
console.log(numbers.lastIndexOf(6)) // -1
```
  
includes:To check if an item exist in an array. If it exist it returns the true
else it returns false.
```js
const numbers = [1, 2, 3, 4, 5]

console.log(numbers.includes(5)) // true
console.log(numbers.includes(0)) // false
console.log(numbers.includes(1)) // true
console.log(numbers.includes(6)) // false

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
] // List of web technologies

console.log(webTechs.includes('Node'))  // true
console.log(webTechs.includes('C'))     // false
```
  
#### Checking array
Array.isArray:To check if the data type is an array
```js
const numbers = [1, 2, 3, 4, 5]
console.log(Array.isArray(numbers)) // true

const number = 100
console.log(Array.isArray(number)) // false
```
  
#### Converting array to string
toString:Converts array to string
```js
const numbers = [1, 2, 3, 4, 5]
console.log(numbers.toString()) // 1,2,3,4,5

const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
console.log(names.toString()) // Asabeneh,Mathias,Elias,Brook
```
  
#### Joining array elements
join: It is used to join the elements of the array, the argument we passed in
the join method will be joined in the array and return as a string. By default,
it joins with a comma, but we can pass different string parameter which can be
joined between the items.
```js
const numbers = [1, 2, 3, 4, 5]
console.log(numbers.join()) // 1,2,3,4,5

const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']

console.log(names.join()) // Asabeneh,Mathias,Elias,Brook
console.log(names.join('')) //AsabenehMathiasEliasBrook
console.log(names.join(' ')) //Asabeneh Mathias Elias Brook
console.log(names.join(', ')) //Asabeneh, Mathias, Elias, Brook
console.log(names.join(' # ')) //Asabeneh # Mathias # Elias # Brook

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
] // List of web technologies

console.log(webTechs.join())       // "HTML,CSS,JavaScript,React,Redux,Node,MongoDB"
console.log(webTechs.join(' # '))  // "HTML # CSS # JavaScript # React # Redux # Node # MongoDB"
```
  
#### Slice array elements
Slice: To cut out a multiple items in range. It takes two parameters:starting
and ending position. It doesn't include the ending position.
```js
const numbers = [1,2,3,4,5]

console.log(numbers.slice()) // -> it copies all  item
console.log(numbers.slice(0)) // -> it copies all  item
console.log(numbers.slice(0, numbers.length)) // it copies all  item
console.log(numbers.slice(1,4)) // -> [2,3,4] // it doesn't include the ending position
```
  
#### Splice method in array
Splice: It takes three parameters: Starting position, number of times to be
removed and number of items to be added.
```js
const numbers = [1, 2, 3, 4, 5]
numbers.splice()
console.log(numbers)                // -> remove all items
const numbers = [1, 2, 3, 4, 5]
numbers.splice(0,1)
console.log(numbers)            // remove the first item
const numbers = [1, 2, 3, 4, 5, 6]
numbers.splice(3, 3, 7, 8, 9)
console.log(numbers.splice(3, 3, 7, 8, 9))  // -> [1, 2, 3, 7, 8, 9] //it removes three item and replace three items
```
  
#### Adding item to an array using push
Push: adding item in the end. To add item to the end of an existing array we use the push method.
```js
// syntax
const arr  = ['item1', 'item2','item3']
arr.push('new item')
console.log(arr)
// ['item1', 'item2','item3','new item']
```
  
```js
const numbers = [1, 2, 3, 4, 5]
numbers.push(6)
console.log(numbers) // -> [1,2,3,4,5,6]

numbers.pop() // -> remove one item from the end
console.log(numbers) // -> [1,2,3,4,5]
```
  
```js
let fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.push('apple')
console.log(fruits)    // ['banana', 'orange', 'mango', 'lemon', 'apple']

fruits.push('lime')
console.log(fruits)   // ['banana', 'orange', 'mango', 'lemon', 'apple', 'lime']
```
  
#### Removing the end element using pop
pop: Removing item in the end.
```js
const numbers = [1, 2, 3, 4, 5]
numbers.pop() // -> remove one item from the end
console.log(numbers) // -> [1,2,3,4]
```
  
#### Removing an element from the beginning
shift: Removing one array element in the beginning of the array.
```js
const numbers = [1, 2, 3, 4, 5]
numbers.shift() // -> remove one item from the beginning
console.log(numbers) // -> [2,3,4,5]
```
  
#### Add an element from the beginning
unshift: Adding array element in the beginning of the array.
```js
const numbers = [1, 2, 3, 4, 5]
numbers.unshift(0) // -> add one item from the beginning
console.log(numbers) // -> [0,1,2,3,4,5]
```
  
#### Reversing array order
reverse: reverse the order of an array.
```js
const numbers = [1, 2, 3, 4, 5]
numbers.reverse() // -> reverse array order
console.log(numbers) // [5, 4, 3, 2, 1]

numbers.reverse()
console.log(numbers) // [1, 2, 3, 4, 5]
```
  
#### Sorting elements in array
sort: arrange array elements in ascending order. Sort takes a call back function, we will see how we use sort with a call back function in the coming sections.
```js
const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
]

webTechs.sort()
console.log(webTechs) // ["CSS", "HTML", "JavaScript", "MongoDB", "Node", "React", "Redux"]

webTechs.reverse() // after sorting we can reverse it
console.log(webTechs) // ["Redux", "React", "Node", "MongoDB", "JavaScript", "HTML", "CSS"]
```
  
### Datetime
  
#### getFullYear() method
Let's extract or get the full year from a time object.
```js
const now = new Date()
console.log(now.getFullYear()) // 2020
```
  
#### getMonth() method
Let's extract or get the month from a time object.
```js
const now = new Date()
console.log(now.getMonth()) // 0, because the month is January,  month(0-11)
```
  
#### getDate() method
Let's extract or get the date of the month from a time object.
```js
const now = new Date()
console.log(now.getDate()) // 4, because the day of the month is 4th,  day(1-31)
```
  
#### getDay() method
Let's extract or get the day of the week from a time object.
```js
const now = new Date()
console.log(now.getDay()) // 6, because the day is Saturday which is the 7th day
//  Sunday is 0, Monday is 1 and Saturday is 6
// Getting the weekday as a number (0-6)
```
  
#### getHours() method
Let's extract or get the hours from a time object.
```js
const now = new Date()
console.log(now.getHours()) // 0, because the time is 00:56:41
```
  
#### getMinutes() method
Let's extract or get the minutes from a time object.
```js
const now = new Date()
console.log(now.getMinutes()) // 56, because the time is 00:56:41
```
  
#### getSeconds() method
Let's extract or get the seconds from a time object.
```js
const now = new Date()
console.log(now.getSeconds()) // 41, because the time is 00:56:41
```
  
#### getTime() method
This method give time in milliseconds starting from January 1, 1970.
It is also know as Unix time. We can get the unix time in two ways:

1. Using getTime()
```js
const now = new Date() //
console.log(now.getTime()) // 1578092201341, this is the number of seconds passed from January 1, 1970 to January 4, 2020 00:56:41
```
  
2. Using Date.now()
```js
const allSeconds = Date.now() //
console.log(allSeconds) // 1578092201341, this is the number of seconds passed from January 1, 1970 to January 4, 2020 00:56:41
const timeInSeconds = new Date().getTime()
console.log(allSeconds == timeInSeconds) // true
```
  
Let us format these values to a human readable time format. Example:
```js
const now = new Date()
const year = now.getFullYear() // return year
const month = now.getMonth() + 1 // return month(0 - 11)
const date = now.getDate() // return date (1 - 31)
const hours = now.getHours() // return number (0 - 23)
const minutes = now.getMinutes() // return number (0 -59)

console.log(`${date}/${month}/${year} ${hours}:${minutes}`) // 4/1/2020 0:56
```
  
### String
  
1. toUpperCase(): this method changes the string to uppercase letters.

```js
let string = 'JavaScript'
console.log(string.toUpperCase())     // JAVASCRIPT
let firstName = 'Asabeneh'
console.log(firstName.toUpperCase())  // ASABENEH
let country = 'Finland'
console.log(country.toUpperCase())    // FINLAND
```
  
2. toLowerCase(): this method changes the string to lowercase letters.
```js
let string = 'JavasCript'
console.log(string.toLowerCase())     // javascript
let firstName = 'Asabeneh'
console.log(firstName.toLowerCase())  // asabeneh
let country = 'Finland'
console.log(country.toLowerCase())   // finland
```
  
3. substr(): It takes two arguments, the starting index and number of
characters to slice.
```js
let string = 'JavaScript'
console.log(string.substr(4,6))    // Script
let country = 'Finland'
console.log(country.substr(3, 4))   // land
```
  
4. substring(): It takes two arguments, the starting index and the stopping
index but it doesn't include the character at the stopping index.
```js
let string = 'JavaScript'
console.log(string.substring(0,4))     // Java
console.log(string.substring(4,10))    // Script
console.log(string.substring(4))       // Script
let country = 'Finland'
console.log(country.substring(0, 3))   // Fin
console.log(country.substring(3, 7))   // land
console.log(country.substring(3))      // land
```
  
5. split(): The split method splits a string at a specified place.
```js
let string = '30 Days Of JavaScript'
console.log(string.split())     // Changes to an array -> ["30 Days Of JavaScript"]
console.log(string.split(' '))  // Split to an array at space -> ["30", "Days", "Of", "JavaScript"]
let firstName = 'Asabeneh'
console.log(firstName.split())    // Change to an array - > ["Asabeneh"]
console.log(firstName.split(''))  // Split to an array at each letter ->  ["A", "s", "a", "b", "e", "n", "e", "h"]
let countries = 'Finland, Sweden, Norway, Denmark, and Iceland'
console.log(countries.split(','))  // split to any array at comma -> ["Finland", " Sweden", " Norway", " Denmark", " and Iceland"]
console.log(countries.split(', ')) //  ["Finland", "Sweden", "Norway", "Denmark", "and Iceland"]
```
  
6. trim(): Removes trailing space in the beginning or the end of a string.
```js
let string = \'   30 Days Of JavaScript   '
console.log(string)
console.log(string.trim(' '))
let firstName = ' Asabeneh '
console.log(firstName)
console.log(firstName.trim())  // still removes spaces at the beginning and the end of the string
```
  
7. includes(): It takes a substring argument and it checks if substring
argument exists in the string. includes() returns a boolean. If a substring
exist in a string, it returns true, otherwise it returns false.
```js
let string = '30 Days Of JavaScript'
console.log(string.includes('Days'))     // true
console.log(string.includes('days'))     // false - it is case sensitive!
console.log(string.includes('Script'))   // true
console.log(string.includes('script'))   // false
console.log(string.includes('java'))     // false
console.log(string.includes('Java'))     // true
let country = 'Finland'
console.log(country.includes('fin'))     // false
console.log(country.includes('Fin'))     // true
console.log(country.includes('land'))    // true
console.log(country.includes('Land'))    // false
```
  
8. replace(): takes as a parameter the old substring and a new substring.
```js
let string = '30 Days Of JavaScript'
console.log(string.replace('JavaScript', 'Python')) // 30 Days Of Python
let country = 'Finland'
console.log(country.replace('Fin', 'Noman'))       // Nomanland
```
  
9. charAt(): Takes index and it returns the value at that index
```js
let string = '30 Days Of JavaScript'
console.log(string.charAt(0))        // 3
let lastIndex = string.length - 1
console.log(string.charAt(lastIndex)) // t
```
  
10. charCodeAt(): Takes index and it returns char code (ASCII number) of the
value at that index
```js
let string = '30 Days Of JavaScript'
console.log(string.charCodeAt(3))        // D ASCII number is 68
let lastIndex = string.length - 1
console.log(string.charCodeAt(lastIndex)) // t ASCII is 116
```
  
11. indexOf(): Takes a substring and if the substring exists in a string it
returns the first position of the substring if does not exist it returns -1
```js
let string = '30 Days Of JavaScript'
console.log(string.indexOf('D'))          // 3
console.log(string.indexOf('Days'))       // 3
console.log(string.indexOf('days'))       // -1
console.log(string.indexOf('a'))          // 4
console.log(string.indexOf('JavaScript')) // 11
console.log(string.indexOf('Script'))     //15
console.log(string.indexOf('script'))     // -1
```
  
12. lastIndexOf(): Takes a substring and if the substring exists in a string
it returns the last position of the substring if it does not exist it
returns -1
```js
let string = 'I love JavaScript. If you do not love JavaScript what else can you love.'
console.log(string.lastIndexOf('love'))       // 67
console.log(string.lastIndexOf('you'))        // 63
console.log(string.lastIndexOf('JavaScript')) // 38
```
  
13. concat(): it takes many substrings and joins them.
```js
let string = '30'
console.log(string.concat("Days", "Of", "JavaScript")) // 30DaysOfJavaScript
let country = 'Fin'
console.log(country.concat("land")) // Finland
```

14. startsWith(): it takes a substring as an argument and it checks if the
string starts with that specified substring. It returns a
boolean(true or false).
```js
let string = 'Love is the best to in this world'
console.log(string.startsWith('Love'))   // true
console.log(string.startsWith('love'))   // false
console.log(string.startsWith('world'))  // false
let country = 'Finland'
console.log(country.startsWith('Fin'))   // true
console.log(country.startsWith('fin'))   // false
console.log(country.startsWith('land'))  //  false
```
  
15. endsWith(): it takes a substring as an argument and it checks if the string
ends with that specified substring. It returns a boolean(true or false).
```js
let string = 'Love is the most powerful feeling in the world'
console.log(string.endsWith('world'))         // true
console.log(string.endsWith('love'))          // false
console.log(string.endsWith('in the world')) // true
let country = 'Finland'
console.log(country.endsWith('land'))         // true
console.log(country.endsWith('fin'))          // false
console.log(country.endsWith('Fin'))          //  false
```
  
16. search(): it takes a substring as an argument and it returns the index of the
first match. The search value can be a string or a regular expression pattern.
```js
let string = 'I love JavaScript. If you do not love JavaScript what else can you love.'
console.log(string.search('love'))          // 2
console.log(string.search(/javascript/gi))  // 7
```
  
17. match: it takes a substring or regular expression pattern as an argument
and it returns an array if there is match if not it returns null. Let us see
how a regular expression pattern looks like. It starts with / sign and ends
with / sign.
```js
let string = 'love'
let patternOne = /love/     // with out any flag
let patternTwo = /love/gi   // g-means to search in the whole text, i - case insensitive
```
  
Match syntax
```js
let string = 'I love JavaScript. If you do not love JavaScript what else can you love.'
console.log(string.match('love'))

// ["love", index: 2, input: "I love JavaScript. If you do not love JavaScript what else can you love.", groups: undefined]

let pattern = /love/gi
console.log(string.match(pattern))   // ["love", "love", "love"]
```
  
Let us extract numbers from text using a regular expression. This is not the regular expression section, do not panic! We will cover regular expressions later on.
```js
let txt = 'In 2019, I ran 30 Days of Python. Now, in 2020 I am super exited to start this challenge'
let regEx = /\d+/

// d with escape character means d not a normal d instead acts a digit
// + means one or more digit numbers,
// if there is g after that it means global, search everywhere.

console.log(txt.match(regEx))  // ["2", "0", "1", "9", "3", "0", "2", "0", "2", "0"]
console.log(txt.match(/\d+/g)) // ["2019", "30", "2020"]
```

18. repeat(): it takes a number as argument and it returns the repeated version of the string.
```js
let string = 'love'
console.log(string.repeat(10)) // lovelovelovelovelovelovelovelovelovelove
```
  
### Math
Some basic math methods
```js
console.log(Math.round(PI))                // 3 to round values to the nearest number
console.log(Math.round(9.81))              // 10
console.log(Math.floor(PI))                // 3 rounding down
console.log(Math.ceil(PI))                 // 4 rounding up
console.log(Math.min(-5, 3, 20, 4, 5, 10)) // -5, returns the minimum value
console.log(Math.max(-5, 3, 20, 4, 5, 10)) // 20, returns the maximum value

// Absolute value
console.log(Math.abs(-10))      // 10

//Square root
console.log(Math.sqrt(100))     // 10

console.log(Math.sqrt(2))       // 1.4142135623730951

// Power
console.log(Math.pow(3, 2))     // 9

console.log(Math.E)             // 2.718

// Logarithm
// Returns the natural logarithm with base E of x, Math.log(x)
console.log(Math.log(2))        // 0.6931471805599453
console.log(Math.log(10))       // 2.302585092994046

// Returns the natural logarithm of 2 and 10 respectively
console.log(Math.LN2)           // 0.6931471805599453
console.log(Math.LN10)          // 2.302585092994046

// Trigonometry
Math.sin(0)
Math.sin(60)

Math.cos(0)
Math.cos(60)
```
  
#### Random numbers
```js
const randNum = Math.random() // creates random number between 0 to 0.999999
console.log(randNum)

const num = Math.floor(Math.random () * 11) // creates random number between 0 and 10
console.log(num)
```