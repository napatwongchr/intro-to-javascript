# Object Oriented JavaScript

## this

🌟 this นั้นเป็น variable ตัวนึงที่จะ refer ถึง execution context นั้น ๆ **เราสามารถบอกได้ว่า this คืออะไรให้ดูที่ว่า function ถูกเรียกใช้อย่างไร**

**ตัวอย่าง**

```js
const user2 = {
  name: "Micky",
  score: 0,
  increaseScore() {
    this.score += 1;
  },
};

user2.increaseScore();

// this.score คือ users2.score
```

🌟 โดยปกติแล้ว **this ใน JS จะไม่เหมือนภาษาอื่น ๆ this สามารถใช้ได้ทุก function ของ JS** แต่ this จะเป็นอะไรนั้น ขึ้นอยู่กับว่า function นั้นถูกเรียกใช้ยังไง

ลองมาดูอีกสักตัวอย่าง

```js
let user = { name: "John" };
let admin = { name: "Admin" };

function sayHi() {
  console.log(this.name);
}

user.sayHi = sayHi;
admin.sayHi = sayHi;

user.sayHi();
admin.sayHi();
```

<br><hr><br>

## OOP

Object Oriented Programming (OOP) คือ รูปแบบการเขียนโปรแกรมอย่างหนึ่ง ที่ทำการจัดกลุ่ม Variables และ Functions ที่เกี่ยวข้องกันให้มาอยู่ด้วยกันเป็นก้อนเดียวกัน ก้อน นี้เราจะเรียกว่า Object ใน Object เราจะเรียก Variables ว่า Properties และ Functions ว่า Methods

มาลองดูตัวอย่าง Code กันสักหน่อย

```js
const user1Name = "John";
const user2Name = "Micky";

let user1Score = 0;
let user2Score = 0;

user1Score = user1Score + 1;
user2Score = user2Score + 1;
```

ลองนึกภาพว่าเวลามี user ในระบบเยอะ ที่ต้องทำการ update score โค้ดข้างบนจะค่อนข้างซ้ำซ้อน และไม่เป็นระเบียบ

เพราะฉะนั้นเราต้องหาวิธีจัดระเบียบให้มันหน่อย **เราจะจัดระเบียบมันด้วย Object**

```js
const user1 = {
  name: "John",
  score: 0,
  increaseScore() {
    this.score += 1;
  },
};

const user2 = {
  name: "Micky",
  score: 0,
  increaseScore() {
    this.score += 1;
  },
};

const user3 = {
  name: "G",
  score: 0,
  increaseScore() {
    this.score += 1;
  },
};

user1.increaseScore();
user1.increaseScore();
user1.increaseScore();
user1.score;

user3.increaseScore();
user3.score;
```

จะสังเกตว่าถ้าเราสร้าง Object ของ user แต่ละคนมันจะเริ่มมี functions ที่ซ้ำซ้อนกันอยู่ เราในฐานะ programmer ก็อาจจะไม่ชอบสักเท่าไหร่ เราก็จะ follow ตาม concept ของ **DRY** (**D**on't **R**epeat **Y**our self)

<br><hr><br>

## Prototypes

สืบเนื่องจากด้านบนเราสามารถที่จะ Refactor โค้ดได้ประมาณนี้

```js
function createUser(name, score) {
  const newUser = {};
  newUser.name = name;
  newUser.score = score;
  newUser.increaseScore = function () {
    newUser.score += 1;
  };
  return newUser;
}

const user1 = createUser("John", 0);
const user2 = createUser("Micky", 0);

user1.increaseScore();
user2.increaseScore();
```

เราจะเห็นว่ามันก็ดูโอเคนะ แต่เราเรียกใช้งาน `createUser` function เราจะต้องเก็บข้อมูล และ functions ต่าง ๆ ลงใน memory มันมีวิธีการที่สามารถ optimise ตรงนี้อีกได้ด้วยการใช้ **Prototype Chain**

โดยปกติแล้ว JS Object จะมี Property ลับซ่อนอยู่คือ `[[Prototypes]]` จะมีค่าเป็น null หรือ reference ไปหา Object ตัวอื่น ตัว Property ตัวนี้เราเรียกว่า `Prototype`

### ตัวอย่าง

```js
let animal = {
  eats: true,
};

let rabbit = {
  jumps: true,
};

rabbit.__proto__ = animal; // sets rabbit.[[Prototype]] = animal

rabbit.eats; // true
```

การที่เราสามารถ get key eats ออกมาได้จาก rabbit โดยที่ rabbit ไม่มี key eats อยู่เลย เป็นเพราะ rabbit มี prototype property ที่ link ไปหา animal อยู่ ตรงนี้เราเรียกว่า **"Prototype Chain"**

<br><hr><br>

## Using Prototypes

```js
function createUser(name, score) {
  const newUser = Object.create(userFunctionStore);
  newUser.name = name;
  newUser.score = score;
  return newUser;
}

const userFunctionStore = {
  increaseScore: function () {
    this.score += 1;
  },
};

const user1 = createUser("John", 0);
const user2 = createUser("Micky", 0);

user1.increaseScore();
user2.increaseScore();
```

<br><hr><br>

## Using new Keyword

new Keyword สามารถลดรูปในการที่เราจะเขียน link object เข้าด้วยกัน

```js
function createUser(name, score) {
  this.name = name;
  this.score = score;
}

createUser.prototype.increaseScore = function () {
  this.score += 1;
};

const user1 = new createUser("John", 0);
const user2 = new createUser("Micky", 0);

user1.increaseScore();
user1.increaseScore();
user2.increaseScore();

user1.score; // 2
```

🌟 **__proto__ ต่างกับ prototype ยังไง ?**

- __proto__  เป็น Internal Property ใน Object ที่จะชี้ไปหา Prototype ของมัน

- prototype เป็น Prototype ของ Objects ที่สร้างด้วย Function ของมันเอง เพราะฉะนั้น prototype property จะไม่มีอยู่ใน Object ที่ได้มาจากการ new

## Class Keyword

Class ใน JS เป็น **Synthetic Sugar** ที่สร้างขึ้นมาเพื่อให้เขียน prototype ได้ง่ายมากยิ่งขึ้น ไม่ต้องไปเขียนแยกกันแบบด้านบน

```js
class User {
  constructor(name, score) {
    this.name = name;
    this.score = score;
  }

  increment() {
    this.score++;
  }

  decrease() {
    this.score--;
  }
}

const user1 = new User("John", 20);
const user2 = new User("Micky", 20);

user1.increment();
user2.decrement();
```

## Exercises 🏅

A) What is **this** ? และให้อธิบายการทำงานของ this

```js
let order1 = { customerName: "John", totalPrice: 4500 };
let order2 = { customerName: "Anny", totalPrice: 2500 };

function getTotalPrice() {
  console.log(this.totalPrice);
}

order1.getTotalPrice = getTotalPrice;
order2.getTotalPrice = getTotalPrice;

order1.getTotalPrice();
order2.getTotalPrice();
```

<br><hr><br>

B) สร้าง Object calculator ที่มี 4 methods

- divide
- sum
- subtract
- multiply

<br><hr><br>
