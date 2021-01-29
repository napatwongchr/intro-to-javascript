# Scope และ Closure

Scope คือ สถานที่ที่เราจะไปหาของ

```javascript
let message = "Hello, Codecamp";

console.log(message); // "Hello, Codecamp"
console.log(students); // ?
```

จากโค้ดข้างต้น

- เราสร้าง variable message จากนั้นเราเรียกใช้ function console.log แล้วส่ง message JS จะวิ่งหา message ว่าเรามีการสร้างไว้ที่ไหนหรือเปล่า ในที่นี้เราเจออยู่ข้างบนตรงบรรทัดแรก

- จากนั้นเราเรียกใช้ function console.log แล้วส่ง students เข้าไป JS ก็จะวิ่งหา students ว่าเรามีสร้างไว้ที่ไหนหรือเปล่า ในที่นี้เราไม่เจอ students สร้างไว้อยู่เลย JS ก็จะ throw error ออกมา

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

## Closure

Closure คือคุณสมบัติของ function ที่ function สามารถจำ environment รอบ ๆ ตัวมันได้ ถึงแม้ว่าเราส่ง function เข้าไปที่ไหนสักที่

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
