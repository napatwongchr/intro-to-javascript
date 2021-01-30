# Scope และ Closure

Scope คือ สถานที่ที่เราจะไปหาของ

```javascript
let message = "Hello, Codecamp";

console.log(message); // "Hello, Codecamp"
console.log(students); // ?
```

จากโค้ดข้างต้น

- เราสร้าง variable message จากนั้นเราเรียกใช้ function console.log แล้วส่ง message เข้าไปใน function

- จากนั้น JS จะวิ่งหา message ว่าเรามีการสร้างไว้ที่ไหนหรือเปล่า ในที่นี้เราเจออยู่ข้างบนตรงบรรทัดแรก

- จากนั้นเราเรียกใช้ function console.log แล้วส่ง students เข้าไปใน function
  
- JS ก็จะวิ่งหา students ว่าเรามีสร้างไว้ที่ไหนหรือเปล่า ในที่นี้เราไม่เจอ students สร้างไว้อยู่เลย JS ก็จะ throw error ออกมา

ลองมาดูอีกสักตัวอย่าง

```javascript
let name = "Jane";

function showGreetingMessage() {
  name = "Mary";
  let message = "Hello, " + name;
  console.log(message);
}

showGreetingMessage();
```

<br><hr><br>

## Nested Scope

```javascript
function initCounter() {
  let counter = 0

  function changeBy(val) {
    let message = "Change counter by " +  val
    console.log(message)

    counter = counter + val;
  }

  return {
    increment: function() {
      changeBy(1)
    },
    decrement: function() {
      changeBy(-1)
    },
    getCounter: function() {
      return counter
    }
  }
}
```

<br><hr><br>

## Closure

Closure คือคุณสมบัติของ function ที่ function สามารถจำ environment รอบ ๆ ตัวมันได้ ๆ

ลองมาดูตัวอย่าง

```javascript
function showGreetingMessage(message) {
  setTimeout(function showMessageLater() {
    console.log(message);
  }, 1000);
}

showGreetingMessage("Hi, Everyone !");
```

จากโค้่ดข้างบน

- จะเห็นได้ว่า function `showGreetingMessage` ถูกเรียกใช้งาน และส่ง string "Hi, Everyone !" เข้าไปใน function
  
- จากนั้นภายใน function จะเรียกใช้งาน function `setTimeout` ซึ่งเป็น function ที่รับ 2 parameters คือ function และ เวลา (ms) หน้าที่ของมันคือ function ที่ถูกส่งเข้าไปจะถูกทำงานภายในระยะเวลาที่กำหนด
  
- function `showMessageLater` จะถูกเรียกใช้หลังจาก 1000 ms ไปแล้ว คำถามคือ message ที่ถูกส่งเข้าไปใน console.log นั้นได้มาจากไหน ? คำตอบคือ function `showMessageLater` สามารถวิ่งไปหา message ที่ส่งเข้ามาผ่าน parameter ใน function `showGreetingMessage` ได้

## Closure มีประโยชน์ยังไง ?

Closure ทำให้เราสามารถบล็อกข้อมูลไว้ให้อยู่ใน Scope ที่แยกออกมาเป็นของตัวมันเอง แล้วก็แชร์ข้อมูลเท่าที่จำเป็น ลองดูตัวอย่างจาก Nested Scope

```javascript
function createCounter() {
  let counter = 0

  function changeBy(val) {
    counter = counter + val;
  }

  return {
    increment: function() {
      changeBy(1)
    },
    decrement: function() {
      changeBy(-1)
    },
    getCounter: function() {
      return counter
    }
  }
}

const counter = createCounter()

counter.increment()

counter.getCounter()

counter.increment()

counter.getCounter()
```