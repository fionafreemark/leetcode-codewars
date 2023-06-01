# Codewars Notes

Codewars likes you to have the shortest code possible, and the fewer variable declarations the better. 
1. Pseudocode
2. Start to write out parts of the functions
3. Put it together 
4. Run the tests
5. Refactor

## Beginner - Lost Without a Map

## Abbreviate a Two Word Name
```
//.split(" ") the two names into an array of 2 words
// map through them to grab the first index of each word. -> I used .split("") to 
// join the two letters with a .join"."  
function abbrevName(name){
return name.split(" ").map(name => name.split("")[0]).join(".").toUpperCase();
}
```
Final Answer
```
const abbrevName = (name) => {
return name.split(" ").map(name => name[0]).join(".").toUpperCase();
}
```
.toUpperCase() could also go after name[0] inside the smooth bracket. 


## Highest Lowest

## String ends with?

## Replace with Alphabet Position
<!-- Create a legend (a string with every letter in the alphabet) -->
<!-- Reference the letters against the legend to find its index -->
<!-- Split the string into an array of letters -->
<!-- text.split("").filter(char => {char.includes([A-Za-z])}) -->
<!-- If ! a letter, ignore, don't return anything -->
<!-- Loop through the array and cross reference against the legend (map a new array of numbers) -->
<!-- Find letter in legend, return index + 1 -->
<!-- .indexOf() -->
<!-- text.map(letter => {return legend.indexOf(letter) + 1}) -->
<!-- Create a new string from the array of the numbers, with spaces between.
.join(" ") -->
<!-- Return the string  (text) -->
``` 
function alphabetPosition(text) {
const legend = "abcdefghijklmnopqrstuvwxyz";
const textArray = text.split("").filter(char => (/[a-zA-Z]/).test(char)).map(letter => {return legend.indexOf(letter.toLowerCase()) + 1});
return textArray.join(" ");
<!-- console.log(textArray); -->
}
```
Refactored to:
```
function alphabetPosition(text) {
  const legend = "abcdefghijklmnopqrstuvwxyz"; 
  return text.split("").filter(char => (/[a-zA-Z]/).test(char)).map(letter => legend.indexOf(letter.toLowerCase()) + 1).join(" ");
}
```
Notes:
.split()
- splits a string into an array of words / characters / a string. 
- syntax is split(separator) or split(separator, limit)
- .split('') splits string into individual characters
- .split(' ') splits string into individual words
- .split() puts entire string into an array (i.e. only one index)

.test()
- executes a search for a match between a regular expression and a specified string. returns true if match, false if not
- ex: regex.test(stringToTestAgainst)
-     (/[a-zA-Z]/).test(char)   ------> In the codewars problem we are testing the individual characters of a string (char) against the regex expression to make sure they include only letters a-z and A-Z.

.indexOf()
.toLowerCase()
.join()
## Credit Card Mask

## A Needle In the Haystack


## Even or Odd
```
const evenOrOdd = (number) => {
// use the % modulo function to determine if the number is even or odd
// odd numbers will have a remainer, even wont.
// use an if/else statement initially and then refactor into ternary
//   if (number % 2 === 0) {
//     return "Even"
//   } else {
//     return "Odd"
//   }
  return number % 2 === 0 ? "Even" : "Odd";
}
```
Final Answer
```
const evenOrOdd = (number) => {
  return number % 2 === 0 ? "Even" : "Odd";
}
```
The top result removed the "=== 0" from the ternary, I suppose its assumed that if you ask number % 2 ? that the default answer is 0. 

## Opposite Number
Initial
```
const opposite = (number) => {
  //if number > 0, * -1.
  //if number < 0, * -1
  //if number === 0, return 0;
  if (number > 0 ){
    return number * -1;
  } else if (number < 0) {
    return number * -1;
  } else if (number === 0) {
    return 0;
  }
}
```
Final Answer
```
const opposite = (num) => { return num === 0 ? 0 : num * -1; }
```
Best Solution
```
const opposite = (num) => { return(-num); }
```

## Two to One
- combine 2 strings (s2.concat(s2))
- make lowercase
- split into array, sort
- use SET (Haley's suggestion), find unique elements in an array
```
return s1.concat(s2).toLowerCase().split("").sort();
return Array.from[new Set].join("");
or
return [...new Set].join("");
```
Final Answer
```
return [...new Set(s1 + s2).sort()].join('');
```
- Set is its own data type and needs to be converted back to an array to be manipulated ([...Set]).
- Can use basic + operator instead of .concat()


## Growth of a Population
```
function nbYear(p0, percent, aug, p) {
<!-- Run a while loop that runs the algorithm as long as p0 < p; -->
counter = 0;
while (p0 < p) {
  p0 += Math.floor(p0(percent / 100) + aug );
  <!-- Error we were getting was "3 expected to equal 4". We were returning a number w/ a decimal so it wasn't looping enough times. We used Math..floor to lower the decimal to an integer, forcing it to run once more, equaling 4 loops -->
  counter ++;
}
return counter;
<!-- We want to know how many years it will take to be >= p -->
}
```
Final Answer
```
function nbYear(p0, percent, aug, p) {
  counter = 0;
  while (p0 < p) {
    p0 += Math.floor(p0 * (percent / 100) + aug);
    counter ++;
  }
  return counter;
}
```

## Find the Parity Outlier
<!-- You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N. -->
<!-- Examples

[2, 4, 0, 100, 4, 11, 2602, 36]
Should return: 11 (the only odd number)

[160, 3, 1719, 19, 11, 13, -21]
Should return: 160 (the only even number)
 -->
 ```
function findOutlier(integers) {
  <!-- Filter over the array to make an array of even numbers -->
const evenArray = integers.filter((int) => {
  return int % 2 === 0;
});
<!-- if evenArray.length > 1, find the odd number and return, ELSE return the sole element in evenArray -->
if (evenArray.length > 1) {
  return integers.find((num) => % 2 > 0);
} else {
  return evenArray[0];
}
}
 ```
 FINAL
 ```
function findOutliers(integers) {
  const evenArray = integers.filter((int) => {
    return in % 2 === 0;
  });
  return evenArray.length > 1 ? integers.find((num) => num % 2 !== 0) : evenArray[0];
}
 ```
 - .find() takes a callback function

 ## Take a 10 Minutes Walk
 <!-- You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). You always walk only a single block for each letter (direction) and you know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

    Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).

 -->


 ## Reversed Strings
The .reverse() is an array method, so you have to spread the string into an array [...str], so you can apply reverse, and then join it back together.
 ```
const solution = (str) => {
  return [...str].reverse().join('');
}
 ```

## Convert a Number to a String!
```
const numberToString = num => num.toString();
```
or 
```
const numberToString = num => String(num);
```
or
```
const numberToString = num => `${num}`;
```
```
const numberToString = num => ''+num;
```

## Convert boolean values to strings "Yes" or "No"
```
const boolToWord = (bool) => { return bool ? "Yes" : "No"; }
```

## Even or Odd
```
const evenOrOdd = (number) => { return number % 2 === 0 ? "Even" : "Odd"; }
```

## Convert a String to a Number
```
const stringToNumber = str => Number(str);
```
or
```
const stringToNumber = str => parsInt(str);
```