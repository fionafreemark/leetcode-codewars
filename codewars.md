# Codewars Notes

Codewars likes you to have the shortest code possible, and the fewer variable declarations the better. 
1. Pseudocode
2. Start to write out parts of the functions
3. Put it together 
4. Run the tests
5. Refactor

### Beginner - Lost Without a Map

### Abbreviate a Two Word Name
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


### Highest Lowest

### String ends with?

### Replace with Alphabet Position
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
### Credit Card Mask

### A Needle In the Haystack


### Even or Odd
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

### Opposite Number
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
