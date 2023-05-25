# Codewars Notes

Codewars likes you to have the shortest code possible, and the fewer variable declarations the better. 
- Pseudocode
- Start to write out parts of the functions
- Put it together 
- Run the tests
- Refactor

### Beginner - Lost Without a Map

### Abbreviate a Two Word Name

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
``` const legend = "abcdefghijklmnopqrstuvwxyz";
const textArray = text.split("").filter(char => (/[a-zA-Z]/).test(char)).map(letter => {return legend.indexOf(letter.toLowerCase()) + 1});
return textArray.join(" ");
<!-- console.log(text-Array); -->
```
Refactored to:
```
function alphabetPosition(text) {
  const legend = "abcdefghijklmnopqrstuvwxyz"; 
  return text.split("").filter(char => (/[a-zA-Z]/).test(char)).map(letter => legend.indexOf(letter.toLowerCase()) + 1).join(" ");
}
```
### Credit Card Mask

### A Needle In the Haystack