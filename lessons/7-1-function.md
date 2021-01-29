# Function

Function คือ Block ของโค้ดส่วนหนึ่งของโปรแกรม ที่สามารถที่จะเรียกใช้ได้หลายครั้ง

<br><hr><br>

## การสร้าง Function ใน JS

```javascript
function showGreetingMessage() {
  console.log("Hello, All !");
}

// เราสามารถเรียกใช้ function ด้วย " ( ) "
showGreetingMessage();
```

ข้างบนนี้เราเรียกว่า **"Function declaration"**

เราสามารถสร้าง Function ได้อีกแบบนึง

```javascript
let sayHi = function () {
  console.log("Hello");
};
```

แบบนี้เราเรียกว่า **"Function expression"**

<br><hr><br>

## Function as a Values

ใน JS function สามารถเป็น value ตัวนึงได้ เราสามารถที่จะ assign ใส่เข้าไปในตัวแปร เพื่อเอาไปทำอะไรสักอย่างต่อได้

```javascript
function calculateBill() {
  console.log("Your balance is 3230 Baht.");
}

let calculate = calculateBill;

calculateBill();
calculate();
```

เรายังสามารถที่จะส่งผ่านเข้าไปใน function กันเองได้ด้วย เนื่องจากมันเป็น value ตัวนึง

```javascript
let sayHi = function (sayBye) {
  console.log("Hello");
  sayBye();
};

let sayBye = function () {
  console.log("Bye.");
};

sayHi(sayBye);
```

<br><hr><br>

## Local and Global Variables

เราสามารถสร้าง variable ใน function ได้ เราจะเรียก variable ที่อยู่ใน function นี้ว่า **"Local Variables"**

```javascript
function showGreetingMessage() {
  let message = "Hello, All !";
  console.log(message);
}

showGreetingMessage();
```

เราสามารถสร้าง variable ข้างนอก function ได้ และสามารถเรียกใช้ variable ข้างนอกได้

```javascript
let name = "Jane";

function showGreetingMessage() {
  let message = "Hello, " + name;
  console.log(message);
}
```

ข้างใน function สามารถเปลี่ยนแปลง variable ที่อยู่ข้างนอก function ได้

```javascript
let name = "Jane";

function showGreetingMessage() {
  name = "Mary";
  let message = "Hello, " + name;
  console.log(message);
}

console.log("Name before call function: " + name);

showGreetingMessage();

console.log("Name after call function: " + name);
```

⚠️ Variables ที่อยู่ข้างนอก function เราจะเรียกว่า **"Global Variables"** Global Variables นั้นสามารถเข้าถึงได้จากข้างใน function ซึ่งเป็นสิ่งที่อันตราย เราควรลดการใช้ Global Variables

แต่บางที Global Variables ก็ดีตรงที่ว่าเราสามารถเอาไว้ใช้เก็บข้อมูลที่ใช้ร่วมกันของ software ได้นะ

<br><hr><br>

## Parameters

เราสามารถส่งข้อมูลเข้าไปใน Function ได้ผ่าน Parameters

```javascript
function showGreetingMessage(name) {
  let message = "Hello, " + name;
  console.log(message);
}

showGreetingMessage("Jane");
```

เราสามารถ Set ค่า Default ให้กับ Parameter ได้เมื่อเราไม่ส่งเข้ามา

```javascript
function showGreetingMessage(name = "Jemmy") {
  let message = "Hello, " + name;
  console.log(message);
}

showGreetingMessage();
```

<br><hr><br>

## Return Values

Function จะมี Input แล้วก็ Output ออกไปเสมอ ๆ

```javascript
function add(a, b) {
  return a + b;
}

let results = add(20, 10);
console.log(results);
```

🌟 **เมื่อ function return เมื่อไหร่ function นั้นจะหยุดทำงานทันที**

```javascript
function checkPermission(age) {
  if (age >= 18) {
    return true;
  } else {
    return confirm("Do you have permission to enter ?");
  }
}

let age = prompt("How old are you?", 18);
let hasPermission = checkPermission(age);

if (hasPermission) {
  alert("Ok you can enter !");
} else {
  alert("No you can not enter");
}
```

🌟 **ถ้า Function ไม่มี return statement มันจะ return undefined**

<br><hr><br>

## Exercises 🏅

1. เขียน function ในการคำนวณเลขด้วยการ + - \* /

2. เขียน function `min(a, b)` ในการหาเลขน้อยที่สุดรหว่างตัวเลขสองตัว

Hint: ใช้ built-in function จาก [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/min) ที่ JS มีมาให้

3. เขียน function `calculateStudentGrade` ในการตัดเกรดนักเรียน

เงื่อนไขคือ

- คะแนน 0 - 59 ได้เกรด F
- คะแนน 60 - 69 ได้เกรด D
- คะแนน 70 - 79 ได้เกรด C
- คะแนน 80 - 89 ได้เกรด B
- คะแนน 90 - 100 ได้เกรด A

4. เขียน function `addFavoriteBook(bookName)` ที่รับ parameter `bookName`

เงื่อนไขคือ

- ชื่อหนังสือต้องมีคำว่า "Beauty" ถึงจะถูก add เข้าไปเป็น Favorite books ได้

```javascript
let favoriteBooks = [];

function addFavoriteBook(bookName) {
  // start write code here
}

addFavoriteBook("Let Me Tell You What I Mean");
addFavoriteBook("Life Among the Terranauts");
addFavoriteBook("The Beauty of Living Twice");
addFavoriteBook("Black Beauty");
addFavoriteBook("Monstrous Beauty");
```

**Hint:**

- เราสามารถเช็ค String ว่ามีคำนี้อยู่ใน String มั้ยได้ ด้วย `string.includes(someString")`
- เราสามารถ add ของเข้าไปใน array ได้ด้วย `array.push(item)`
