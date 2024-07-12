# Comprehensive JavaScript Guide: Strings, Arrays, Objects, and Classes

This repository serves as a comprehensive demonstration of JavaScript's core features, focusing on strings, arrays, objects, and classes. It covers a wide range of methods and functionalities, providing clear examples and explanations for each.

## Table of Contents

- [String Creation and Manipulation](#string-creation-and-manipulation)
- [Basic String Methods](#basic-string-methods)
- [Case Conversion Methods](#case-conversion-methods)
- [Trimming and Padding Methods](#trimming-and-padding-methods)
- [Repeat, Search, and Match Methods](#repeat-search-and-match-methods)
- [Replace, Split, Join, and Sort Methods](#replace-split-join-and-sort-methods)
- [Localize and Raw Methods](#localize-and-raw-methods)
- [Array Methods with Strings](#array-methods-with-strings)
- [Object Methods and Class Definitions](#object-methods-and-class-definitions)
- [Object Freezing, Sealing, and Preventing Extensions](#object-freezing-sealing-and-preventing-extensions)
- [Array Methods in JavaScript](#array-methods-in-javascript)
- [Object Iteration Methods](#object-iteration-methods)

## String Creation and Manipulation

### String Creation

```javascript
// Array of Unicode values
const uniCodes = [
  73, 32, 108, 111, 118, 101, 32, 74, 97, 118, 97, 115, 99, 114, 105, 112, 116,
];

// Various ways to create strings
const strOne = String("Hello world");
const strTwo = new String("Hi, Samir.");
const strThree = String.fromCharCode(...uniCodes);
const strFour = String.fromCodePoint(...uniCodes);
```

### Basic Methods of String

```javascript
const str = "Hello World!";

console.log("String length:", str.length);
console.log("First character:", str.charAt(0));
console.log("Unicode of first character:", str.charCodeAt(0));
console.log("Slice (0, 5):", str.slice(0, 5));
console.log("Substring (6 to second last):", str.substring(6, str.length - 1));
console.log("Substr (0, 5):", str.substr(0, 5));
console.log("String representation:", str.toString());
console.log("Code point at index 1:", str.codePointAt(1));
console.log("Concatenated string:", str.concat(" ", "How you doing?"));
console.log("From char codes:", String.fromCharCode(...uniCodes));
console.log("From code points:", String.fromCodePoint(...uniCodes));
console.log("Value of string:", str.valueOf());
```

### Case Conversion Methods

```javascript
console.log("Lowercase:", str.toLowerCase());
console.log("Uppercase:", str.toUpperCase());
console.log("Locale Lowercase (Turkish):", "Açık Kapı".toLocaleLowerCase("tr"));
console.log("Locale Uppercase (Turkish):", "Açık Kapı".toLocaleUpperCase("tr"));
```

### Trim Methods

```javascript
const strSeven = "    Hello World       ";
console.log("Trimmed:", strSeven.trim());
console.log("Trimmed Start:", strSeven.trimStart());
console.log("Trimmed End:", strSeven.trimEnd());
```

### Padding Methods

```javascript
const strEight = "Hello";
console.log("Pad Start:", strEight.padStart(10, "*"));
console.log("Pad End:", strEight.padEnd(10, "*"));
```

### Repeat Method

```javascript
const strNine = "Hello ";
console.log("Repeated string:", strNine.repeat(5));
```

### Search Methods

```javascript
const strTen = "Hello World!";
console.log("Starts with 'Hello':", strTen.startsWith("Hello"));
console.log("Ends with 'World!':", strTen.endsWith("World!"));
console.log("Includes 'Hello':", strTen.includes("Hello"));
console.log("Index of 'Hello':", strTen.indexOf("Hello"));
console.log("Last index of 'World!':", strTen.lastIndexOf("World!"));
console.log("Search 'hello' (case insensitive):", strTen.search(/hello/i));
```

### Match Methods

```javascript
const strA = "Hello World";
let regex = /(Hello)/g;
console.log("Match 'h' (case insensitive):", strA.match(/h/i));
console.log(
  "MatchAll results:",
  [...strA.matchAll(regex)].map((match) => match[1])
);
console.log("MatchAll objects:", [...strA.matchAll(regex)]);
```

### Replace Method

```javascript
const strB = "Hi, Samir.\nHi, Rifat";
regex = /HI/i;
console.log("Replace 'Hi' with 'Hey':", strB.replace("Hi", "Hey"));
console.log(
  "Replace regex 'HI' (case insensitive):",
  strB.replace(regex, getNewString())
);
console.log("Replace all 'Hi' with 'Hey':", strB.replaceAll("Hi", "Hey"));

function getNewString() {
  return "Hey";
}
```

### Split, Join, and Sort Methods

```javascript
const strC = "Cba";
console.log("Reversed and capitalized:", reverseAndCapitalize(strC));

function reverseAndCapitalize(str) {
  const reversed = str.split("").reverse().join("");
  return reversed.at(0).toUpperCase() + reversed.slice(1).toLowerCase();
}

console.log("sort :", strC.toLowerCase().split("").sort().join(""));
```

### Localize Method

```javascript
console.log("'a' compared to 'b':", "a".localeCompare("b"));
console.log("'b' compared to 'a':", "b".localeCompare("a"));
console.log("'a' compared to 'a':", "a".localeCompare("a"));
```

### Raw Method

```javascript
const strD = String.raw`Hello\tworld!`;
console.log("Raw string:", strD);
```

### Array Methods with String

```javascript
console.log("Array from string:", Array.from("Hello World"));
console.log(
  "Array of numbers from string:",
  Array.from("12345", (num) => Number(num))
);
console.log("Array of numbers:", Array.from("12345", Number));
console.log(
  "Array of values:",
  Array.of("Hi", "Samir,", " ", "How", "Are", "you")
);
console.log("Array of mixed values:", Array.of("1", "3", 5, "3"));
```

## Object Methods and Class Definition

### Demonstrating Built-in Object Methods

```javascript
const exampleObject = { name: "Arafat", id: 1 };
console.log(exampleObject.toString());
console.log(exampleObject.toLocaleString());
console.log(exampleObject.valueOf());
console.log(exampleObject.hasOwnProperty("name"));
```

### Class Definition and Usage

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hi, ${this.name}`);
  }
}

const samir = new Person("Samir");
samir.greet();
console.log(Person.prototype.isPrototypeOf(samir));
console.log(samir instanceof Person);
```

### Object Creation and Manipulation using Object.create

```javascript
const proto = {
  greet() {
    console.log(`Hi, ${this.name}`);
  },
};

const ob = Object.create(proto, {
  name: {
    value: "Rifat",
    writable: true,
    enumerable: true,
    configurable: true,
  },
});

ob.greet();
```

### More Complex Example with Object.create

```javascript
const PrototypeOfStudent = {
  greet() {
    console.log(`${this.name} is ${this.age} years old`);
  },
  getName() {
    return this.name;
  },
  setName(name) {
    this.name = name;
  },
};

const Student = Object.create(PrototypeOfStudent, {
  age: {
    value: 27,
    writable: true,
    enumerable: true,
    configurable: true,
  },
  getAge: {
    value: function () {
      return this.age;
    },
    writable: true,
    enumerable: true,
    configurable: true,
  },
  setAge: {
    value: function (newAge) {
      this.age = newAge;
    },
    writable: true,
    enumerable: true,
    configurable: true,
  },
});

const rifat = Object.create(Student, {
  name: {
    value: "Rifat",
    writable: true,
    enumerable: true,
    configurable: true,
  },
});

rifat.greet();
console.log(rifat.getAge());
rifat.age = 22;
console.log(rifat.getAge());
console.table(rifat);
```

### Object.assign Example

```javascript
const obOne = {};
const obTwo = { name: "rifat", age: 22 };
const obThree = { id: 5, country: "USA" };
const obFour = { id: 6, name: "samir" };

console.log(Object.assign(obOne, obTwo));
console.log(Object.assign(obOne, obTwo, obThree));
console.log(Object.assign(obOne, obTwo, obThree, obFour));
```

### Object.defineProperty Example

```javascript
const personObject = {};
Object.defineProperty(personObject, "name", {
  value: "samir",
  writable: true,
  enumerable: true,
  configurable: true,
});
console.log(personObject);

// Modify property attributes
let internalName = personObject.name;
Object.defineProperty(personObject, "name", {
  get() {
    return internalName;
  },
  set(value) {
    internalName = value;
  },
  enumerable: false,
  configurable: false,
});

console.log(personObject.name);
personObject.name = "rifat";
console.log(personObject.name);
```

### Object.defineProperties Example

```javascript
const studentObject = {};
Object.defineProperties(studentObject, {
  name: {
    value: "arafat",
    writable: true,
    enumerable: true,
    configurable: true,
  },
  id: {
    value: 5,
    writable: true,
    enumerable: true,
    configurable: true,
  },
});

console.log(studentObject);
```

### Object.entries Example

```javascript
const o = { name: "arafat", id: 5, age: 22 };
for (const [key, value] of Object.entries(o)) {
  console.log(`${key} -> ${value}`);
}
console.log(Object.entries(o));
console.log(Object.keys(o));
console.log(Object.values(o));
```

## Object Freezing, Sealing, and Prevent Extensions

### Freezing an Object

```javascript
const newObjectOne = { name: "arafat", id: 5 };
Object.freeze(newObjectOne);
newObjectOne.name = "Li"; // Will not change
newObjectOne.country = "USA"; // Will not add
delete newObjectOne.id; // Will not delete
console.log(newObjectOne);
```

### Sealing an Object

```javascript
const newObjectTwo = { name: "rifat", id: 6 };
Object.seal(newObjectTwo);
newObjectTwo.name = "Lui"; // Will change
newObjectTwo.country = "USA"; // Will not add
delete newObjectTwo.id; // Will not delete
console.log(newObjectTwo);
```

### Preventing Extensions on an Object

```javascript
const newObjectThree = { name: "samir", id: 7 };
Object.preventExtensions(newObjectThree);
newObjectThree.name = "CA"; // Will change
newObjectThree.country = "USA"; // Will not add
delete newObjectThree.id; // Will delete
console.log(newObjectThree);
```

### Object Comparison and Type Checking

```javascript
console.log(Object.is(5, 5)); // true
console.log(Object.is(5, "5")); // false
console.log(Object.is({}, {})); // false
```

### Checking Freeze, Seal, and Extensible States

```javascript
console.log(Object.isFrozen(newObjectOne)); // true
console.log(Object.isSealed(newObjectTwo)); // true
console.log(Object.isExtensible(newObjectThree)); // false
```

### Other Utility Methods

```javascript
const newObjectFour = { name: "arafat" };
console.log(Object.hasOwn(newObjectFour, "name"));
```

## Array Methods in JavaScript

### Array Initialization

```javascript
const arrOne = [1, 1, 3, 3, 5];
const arrOfOb = [
  { name: "Arafat", age: 27, id: 5 },
  { name: "Rifat", age: 20, id: 8 },
  { name: "Samir", age: 27, id: 10 },
];
```

### ForEach Method

```javascript
console.group("%cForEach method", "color: blue; font-size: 20px;");

// Log values where the value equals the index
arrOne.forEach((num, index) => {
  if (num === index) {
    console.log(`Value of index ${index} = ${num}`);
  }
});

// Log details of specific objects in a table
arrOfOb.forEach(({ name, age, id }) => {
  if (name.toLowerCase() === "arafat" && age === 27) {
    console.table([{ name, age, id }]);
  }
});

console.groupEnd();
```

### Map Method

```javascript
console.group("%cMap method", "color: blue; font-size: 20px;");

console.log(arrOne.map((num, i) => num * i));
console.log(["1", "2", "3", "4"].map(Number));
console.table(
  arrOfOb.map(({ name, age }) => ({
    name,
    age,
  }))
);

console.groupEnd();
```

### Filter Method

```javascript
console.group("%cFilter method", "color: blue; font-size: 20px;");

console.log(arrOne.filter((num) => num > 2));
console.log(arrOfOb.filter(({ id }) => id !== 5));

console.groupEnd();
```

### Reduce Method

```javascript
console.group("%cReduce method", "color: blue; font-size: 20px;");

console.log(
  "Sum of array: ",
  arrOne.reduce((acc, num) => acc + num, 0)
);

console.log(
  "Max value from array: ",
  arrOne.reduce((acc, num) => (acc < num ? num : acc), arrOne[0])
);

console.log(
  "Min value from array: ",
  arrOne.reduce((acc, num) => (num < acc ? num : acc), arrOne[0])
);

console.log(
  "Product of age and id: ",
  arrOfOb.reduce((acc, { age, id }) => acc + age * id, 0)
);

console.groupEnd();
```

### Slice Method

```javascript
console.group("%cSlice method", "color: blue; font-size: 20px;");

console.log(arrOne.slice(2));
console.log(arrOne.slice(1, 3));
console.log(arrOne.slice(-2));

console.groupEnd();
```

### Splice Method

```javascript
console.group("%cSplice method", "color: blue; font-size: 20px;");

const arrTwo = [1, 2, 3, 4, 5];
const arrThree = [1, 2, 3, 4, 5];

arrTwo.splice(1, 2, 4, 5);
arrThree.splice(1, 2);

console.log(arrTwo);
console.log(arrThree);

console.groupEnd();
```

### Sort Method

```javascript
console.group("%cSort method", "color: blue; font-size: 20px;");

const strOfArr = ["gold", "apple", "cow", "love"];

console.log(strOfArr.sort());
console.log(arrOne.sort((a, b) => a - b));
console.log(arrOne.sort((a, b) => b - a));
console.log("1314".split("").sort().join(""));

console.groupEnd();
```

### Reverse Method

```javascript
console.group("%cReverse method", "color: blue; font-size: 20px;");

console.log(arrOne.reverse());
console.log(strOfArr.reverse());
console.log("cba".split("").reverse().join(""));

console.groupEnd();
```

### Concat Method

```javascript
console.group("%cConcat method", "color: blue; font-size: 20px;");

console.log(arrOne.concat(7, 8, [2, 3, 4], arrThree));
console.log(["Hi", "Hello"].concat("Hey", "Bye"));

console.groupEnd();
```

### Fill Method

```javascript
console.group("%cFill method", "color: blue; font-size: 20px;");

console.log([1, 2, 3, 4].fill(0));
console.log([1, 2, 3, 4].fill(0, 1, 3));
console.log([1, 2, 3, 4].fill(0, 2));
console.log([1, 2, 3, 4].fill(2, 1, 3));

console.groupEnd();
```

### Includes Method

```javascript
console.group("%cIncludes method", "color: blue; font-size: 20px;");

console.log([1, 3, 4, 5].includes(3));
console.log(["Hi", "Hello", "Hey"].includes("Hello"));
console.log(["Hi", "Hello", "Hey"].includes("Ei"));

console.groupEnd();
```

### IndexOf Method

```javascript
console.group("%cIndexOf method", "color: blue; font-size: 20px;");

console.log([6, 5, 4, 3, 2, 2].indexOf(2));
console.log(["Hi", "Hello", "Hey", "Hello"].indexOf("Hello"));
console.log(["Hi", "Hello", "Hey"].indexOf("Ei"));

console.groupEnd();
```

### LastIndexOf Method

```javascript
console.group("%cLastIndexOf method", "color: blue; font-size: 20px;");

console.log([6, 5, 4, 3, 2, 2].lastIndexOf(2));
console.log(["Hi", "Hello", "Hey", "Hello"].lastIndexOf("Hello"));
console.log(["Hi", "Hello", "Hey"].lastIndexOf("Ei"));

console.groupEnd();
```

### Every Method

```javascript
console.group("%cEvery method", "color: blue; font-size: 20px;");

console.log([1, 2, 3, 4].every((num) => num > 0));
console.log([1, 2, 3, 4].every((num) => num > 2));

console.groupEnd();
```

### Some Method

```javascript
console.group("%cSome method", "color: blue; font-size: 20px;");

console.log([1, 2, 3, 4].some((num) => num > 0));
console.log([1, 2, 3, 4].some((num) => num > 2));
console.log([1, 2, 3, 4].some((num) => num > 4));

console.groupEnd();
```

### Find Method

```javascript
console.group("%cFind method", "color: blue; font-size: 20px;");

console.log([1, 2, 3, 4].find((num) => num === 2));
console.log(arrOfOb.find(({ name }) => name.toLowerCase() === "arafat"));

console.groupEnd();
```

### FindIndex Method

```javascript
console.group("%cFindIndex method", "color: blue; font-size: 20px;");

console.log([1, 2, 3, 4].findIndex((num) => num === 2));
console.log(arrOfOb.findIndex(({ name }) => name.toLowerCase() === "arafat"));

console.groupEnd();
```

### Array.from Method

```javascript
console.group("%cArray.from method", "color: blue; font-size: 20px;");

console.log(Array.from({ length: 5 }, (_, index) => index + 1));
console.log(Array.from("Hello"));
console.log(Array.from("1234", Number));
console.log(Array.from("1234", (num) => Number(num)));
console.log(Array.from(new Set([1, 2, 3, 3, 3])));

console.groupEnd();
```

### Array.of Method

```javascript
console.group("%cArray.of method", "color: blue; font-size: 20px;");

console.log(Array.of(1, 2, 3, 4));
console.log(Array.of("Hi", "Hello", "Hey"));

console.groupEnd();
```

### Array.isArray Method

```javascript
console.group("%cArray.isArray method", "color: blue; font-size: 20px;");

console.log(Array.isArray([1, 2]));
console.log(Array.isArray(["Hi"]));
console.log(Array.isArray(1, 3));
console.log(Array.isArray("Hi"));

console.groupEnd();
```

### Join Method

```javascript
console.group("%cJoin method", "color: blue; font-size: 20px;");

console.log(["Hi", " Samir"].join(","));

console.groupEnd();
```

### Flat Method

```javascript
console.group("%cFlat method", "color: blue; font-size: 20px;");

const arrFive = [[[[[[[[[2]]], 4]]], 5], 6], 7];

console.log(arrFive.flat());
console.log(arrFive.flat(1));
console.log(arrFive.flat(2));
console.log(arrFive.flat(Infinity));

console.groupEnd();
```

### At Method

```javascript
console.group("%cAt method", "color: blue; font-size: 20px;");

console.log([1, 2, 3].at(2));
console.log(["Hi", "Hello", "Hey"].at(0));

console.groupEnd();
```

### CopyWithin Method

```javascript
console.group("%cCopyWithin method", "color: blue; font-size: 20px;");

console.log([1, 2, 3, 4, 5].copyWithin(1, 2, 4));
console.log([1, 2, 3, 4, 5].copyWithin(1, 2));

console.groupEnd();
```

### ToString Method

```javascript
console.group("%cToString method", "color: blue; font-size: 20px;");

console.log([1, 2, 3].toString());

console.groupEnd();
```

## Object Iteration Methods

### Iterating over an Object

```javascript
const obj = {
  name: "Samir",
  id: 1,
  country: "USA",
  courses: ["English", "Math", "Higher Math"],
};

function iterateObject(obj) {
  // Using for...in loop
  for (const key in obj) {
    if (Object.hasOwnProperty.call(obj, key)) {
      console.log(`${key} : ${obj[key]}`);
    }
  }

  // Using Object.keys()
  Object.keys(obj).forEach((key) => {
    console.log(`${key} : ${obj[key]}`);
  });

  // Using Object.values()
  Object.values(obj).forEach((value) => {
    console.log(value);
  });

  // Using Object.entries()
  Object.entries(obj).forEach(([key, value]) => {
    console.log(`${key} : ${value}`);
  });

  // Using for...of loop
  for (const [key, value] of Object.entries(obj)) {
    console.log(`${key} : ${value}`);
  }
}
```

### Demonstrating Map Function

```javascript
function demonstrateMap(obj) {
  const arrOne = Object.keys(obj).map((key) => [key, obj[key]]);
  console.log(arrOne);

  const arrTwo = Object.values(obj).map((value) => typeof value === "string");
  console.log(arrTwo);

  const arrThree = Object.entries(obj).map(
    ([key, value]) => `${key}: ${value}`
  );
  console.log(arrThree);
}
```

### Demonstrating Filter Function

```javascript
function demonstrateFilter(obj) {
  const arrFour = Object.keys(obj).filter((key) => key !== "id");
  console.log(arrFour);

  const arrFive = Object.values(obj).filter(
    (value) => typeof value !== "string"
  );
  console.log(arrFive);

  const arrSix = Object.entries(obj)
    .filter(([key, value]) => Array.isArray(value))
    .flat();
  console.log(arrSix);
}
```

### Demonstrating Reduce Function

```javascript
function demonstrateReduce(obj) {
  const arrSeven = Object.keys(obj).reduce((acc, key) => {
    if (Array.isArray(obj[key])) {
      return key;
    }
    return acc;
  }, "");
  console.log(arrSeven);

  const arrEight = Object.values(obj).reduce((acc, value) => {
    if (Number.isInteger(value)) {
      return value;
    }
    return acc;
  }, 0);
  console.log(arrEight);

  const arrNine = Object.entries(obj).reduce((acc, [key, value]) => {
    if (key === "courses") {
      acc[key] = value;
    }
    return acc;
  }, {});
  console.log(arrNine);
}
```

### Main Execution

```javascript
iterateObject(obj);
demonstrateMap(obj);
demonstrateFilter(obj);
demonstrateReduce(obj);
```

## Contributing

Feel free to fork this repository, open issues, and submit pull requests.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

```

This `README.md` file includes sections for string creation, basic methods, case conversion, trimming, padding, repeating, searching, matching, replacing, splitting, joining, sorting, localizing, raw methods, array methods, object methods, class definitions, and object manipulation. Each section includes code snippets that demonstrate the corresponding methods and their usage.
```

```

```
