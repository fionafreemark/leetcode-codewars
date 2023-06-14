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

## Remove First and Last Character
```
function removeChar(str){
//  const newArray = [...str];
//   newArray.pop();
//   newArray.shift();
//   return(newArray.join(''));

  return str = [...str].slice(1, -1).join('');
  <!-- first number starts from the beginning of the array -->
  <!-- negative number starts from the end of the array -->
  <!-- slice returns all of the values in the array between those numbers. -->
  <!-- YOU CAN SLICE A STRING without converting it to an array and back. -->
};
```

## Convert string to Camel Case
```
function toCamelCase(str){
//   If str is an empty array return error message
  if (str === '') {
    return str;
};
//   Isolate the words we want and put them in an array
//   At the same time, erase non-alphanumeric symbols
  const words = str.split(/[^a-z0-9]/i);
//   Based on that position, toUpperCase the position after the deletion
//   Loop through each word and uppercase the first letter/index[0]
  for (let i = 1; i < words.length; i++) {
    words[i] = words[i][0].toUpperCase() + words[i].slice(1);
  }
//   Join the array back together and return
  return words.join('');
}
```
```
function toCamelCase(str){
//   If str is an empty array return error message
  if (str === '') {
    return str;
};
//   Isolate the words we want and put them in an array
//   At the same time, erase non-alphanumeric symbols
  const words = str.split(/[^a-z0-9]/i);
//   Based on that position, toUpperCase the position after the deletion
//   Loop through each word and uppercase the first letter/index[0]
  for (let i = 1; i < words.length; i++) {
    words[i] = words[i][0].toUpperCase() + words[i].slice(1);
  }
//   Join the array back together and return
  return words.join('');
}
```
## Sum of odd numbers
```
function rowSumOddNumbers(n) {
//   Figure out which numbers are in row n
//    In the nth row, there will be n numbers
//    Figure out what the first number of row n is
//    eg. 4th row, n = 4, (n - 1)
//   Add all of the numbers in row n together
//   Return sum of row n (integer)
//   Row Breakdown
//   Row 1: 1 number [1]
//   Row 2: 2 numbers [3, 5]
//   Row 3: 3 numbers [7, 9, 11]
//   Row 4: 4 numbers [13, 15, 17, 19]
//   Row 5: 5 numbers [21, 23, 25, 27, 29]
//   [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
//   Create starting variables for our arrays and incrementing value
  let numArray = [];
  let val = 1;
//   1st loop, we're creating rows to loop through
  for (let row = 1; row <= n; row++) {
//    Clear out previous row data
      numArray = [];
//    If it's row one, just push
      if (row === 1) {
        numArray.push(val);
      } else {
        //   For each number in the row, add 2 to the value and push into array
        for (let i = 1; i <= row; i++) {
          val += 2;
          numArray.push(val);
        }
      };
};
// Return all numbers in the right row added together
   return numArray.reduce((acc, cur) => acc + cur);
}
```
Final Answer
```
function rowSumOddNumbers(n) {
  let numArray = [];
  let val = 1;
  for (let row = 1; row <= n; row++) {
      numArray = [];
      if (row === 1) {
        numArray.push(val);
      } else {
        for (let i = 1; i <= row; i++) {
          val += 2;
          numArray.push(val);
        }
      };
    };
  return numArray.reduce((acc, cur) => acc + cur);
}
```
Notes
The mathematical way to solve this is:
```
function rowSumOddNumbers(n) {
  return n * n * n; //or n**3
}
We solved by manipulating the arrays. We build each row of the array from scratch on each loop. Then in our return we reduced the nth row.
```
## Your order, please
```
function order(words){
    // split the string into words
    //   sorting: comparing a and b inside of the array.
    //   a.match(/\d/) isolates the number inside of the word
    //   If a > b, we don't change the position, but if its < b, we send it backwards in the array. 
return words.split(' ').sort((first, second) => {
    //     find a number inside of a and b, then if a > b, a comes after b (& vice versa)
  return first.match(/\d/)[0] > second.match(/\d/)[0] ? 0 : -1;
}).join(' ');
}
```
FINAL
```
function order(words){
 return words.split(' ').sort((first, second) => first.match(/\d/)[0] > second.match(/\d/)[0] ? 0 : -1).join(' ');
}
```
.sort() compares the two values and then moves the first value accordingly to the result. if a > b it stays in the same spot. If its less, the index is moved -1 position to the left. Then it compares b with c, etc.

Longer Explanation:
This function called order takes a sentence as input. It then looks at each word in the sentence and checks if there is a number in it. If there is a number, it uses that number to put the words in a specific order. For example, if the sentence is "apple2 banana1 orange3", the function will put the words in the order "banana1 apple2 orange3".

Now, let's look at the sort part. sort is a special action in programming that arranges things in a certain order. In this case, it's arranging the words based on their numbers. When we use sort, we give it a way to compare two things and decide which one should come first. In our function, we're comparing the numbers in the words.

The sort part of the function compares each pair of words. Using match, it looks at the numbers in the words and decides if one is bigger or smaller than the other. If a number is bigger, it means it should come later in the sorted list. If a number is smaller, it means it should come earlier.

After comparing all the pairs of words, the sort part of the function rearranges the words based on the comparisons it made. Finally, the function puts all the words back together into a sentence and gives us the result.

## Does my number look big in this?
```
function narcissistic(value) {
//   Find the length of the number
  const strVal = value.toString();
//   Split number
  const arrVal = strVal.split('');
//   Raise each number to the power of value.length
  const raisedArr = arrVal.map((num) => {
   return num ** strVal.length;
  });
//   Add up the sum of each result
 const sum = raisedArr.reduce((acc, cur) => acc + cur);
//   Compare sum to original value
  // if same = return true else false
  return value === sum
}
```
In trying to refactor the code, Haley realized that the .map was doing essentially the same thing that the .reduce was doing (in cycling through each item in the array) and so she determined that we could combine the two within the .reduce. In order for it to work (it was skipping the first number), we had to indicate that it would start at 0.
FINAL
```
function narcissistic(value) {
 const valStr = value.toString();
 const sum = valStr.split('').reduce((acc, cur) => {
    cur **= valStr.length;
    return acc + cur;
 }, 0);
  return value === sum
}
```

## Sum of positive
```
function positiveSum(arr) {
// filter the array to remove numbers < 0.
  posArr = arr.filter((num) => num >= 0 ? num : 0);
//   console.log(posArr);
// .reduce the new array
  return posArr.reduce((arr, cur) => arr + cur, 0);
}
```
FINAL
```
function positiveSum(arr) {
  return posArr = arr.filter((num) => num >= 0 ? num : 0).reduce((arr, cur) => arr + cur, 0);
}
```
Other:
```
function positiveSum(arr) {
  var total = 0;    
  for (i = 0; i < arr.length; i++) {    // setup loop to go through array of given length
    if (arr[i] > 0) {                   // if arr[i] is greater than zero
      total += arr[i];                  // add arr[i] to total
    }
  }
  return total;                         // return total
}
```
This is what I attempted to refactor to, but I had trouble making it work. In this instance, they put b in brackets with a ternary, whereas I had tried to complete that first before the addition expression.
```
function positiveSum(arr) {
   return arr.reduce((a,b)=> a + (b > 0 ? b : 0),0);
}
```

## Basic Mathematical Operations
This question tripped me up because the operation variable is considered a string. I could concatenate them into a string but was having trouble figuring out how to get them to evaluate to a total. 
First attempt: Discovered eval(), but learned it is a huge security risk, so afterwards opted to find another solution.
```
function basicOp(operation, value1, value2)
// operation is a string
// value is a number
{
//   This is one solution, but eval() is a huge security risk. 
return total = eval(`${value1} ${operation} ${value2}`);
}
```
FINAL
Its suggested that one way to refactor the following is to use a switch statement instead.
```
function basicOp(operation, value1, value2)
{
  if (operation === "+") {
    return value1 + value2;
  } else if (operation === "-") {
    return value1 - value2;
  } else if (operation === "*") {
    return value1 * value2;
  } else if (operation === "/") {
    return value1 / value2;
  } else {
    return "invalid operation";
  }
}
```
Switch Version
```
function basicOp(operation, value1, value2) {
    switch (operation) {
        case '+':
            return value1 + value2;
        case '-':
            return value1 - value2;
        case '*':
            return value1 * value2;
        case '/':
            return value1 / value2;
        default:
            return 0;
    }
}
```
