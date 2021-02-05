# How JavaScript Executes Code

ในบทเรียนนี้เรามามองการทำงานของ JS ในเชิงลึกกันว่า JS นั้นรันโค้ดยังไงกัน

```js
let a = 2;
let b = 4;

function add(inputA, inputB) {
  const result = inputA + inputB;
  return result;
}

let output = add(a, b); // output is 6
let anotherOutput = (4, 10); // anotherOutput is 14
```

จากโค้ด

- JS จะเก็บ value 2 และ 4 เข้าไปใน variables a และ b ตามลำดับใน Memory ของ Computer
- ต่อมา เราได้ declare function `add` จากนั้น JS จะเก็บ function `add` ไว้ใน memory เช่นเดียวกัน
- จากนั้นมีการสร้าง variable ชื่อว่า output แล้ว assign ผลลัพธ์ของการรัน function `add` ที่มี arguments เป็น a และ b
- function `add` ก็จะทำงาน และ return `result` ออกมาใส่ output แล้วจากนั้น function add ก็จะเคลียร์ตัวเองทิ้งโดยที่ไม่สามารถจำอะไรใน function `add` ได้เลย

🌟 JS สามารถที่จะรับทำแค่คำสั่งเดียว ณ เวลานั้น ๆ ซึ่งเป็นการทำงานแบบ **"Single Threaded"**

🌟 JS ทำงานแบบ **"Synchronously"** หมายความว่าทำงานเรียงบรรทัดของโค้ดตามที่เห็น

⚠️ ตรงนี้ให้ลองคิดดูว่า ถ้าเรามีโค้ดส่วนหนึ่ง ที่ ทำอะไรสักอย่างนาน ๆ จะเกิดอะไรขึ้น ?​ แน่นอนครับว่าโค้ดส่วนอื่น ๆ จะไม่ได้ทำงานต่อเลย เพราะว่า **JS สามารถทำได้แค่คำสั่งเดียวในเวลานั้น ๆ**

**ตัวอย่าง**

```js
const posts = getFacebookPosts("http://facebook.com/posts");

showPosts(posts);

showFriendList();

// More code to run
```

จากโค้ด

- ถ้าเรามี function นึง ทำหน้าที่ไปขอข้อมูล Posts จาก Facebook JS จะรับคำสั่ง `getFacebookPosts` ไปทำงาน

- ถ้า `getFacebookPosts` ใช้เวลานานมาก ๆ `showPosts(posts)` จะไม่สามารถที่จะทำงานได้แน่นอน เนื่องจาก JS สามารถที่จะทำงานได้แค่ทีละคำสั่งในเวลานั้น ๆ

**JS เลยจำเป็นต้องมีส่วนประกอบอื่น ๆ ที่มาแก้ไขปัญหานี้**

1. Web Browser APIs / Node Background APIs
2. Promises
3. Event loop, Callback/Task queue และ micro task queue

<br><hr><br>

## Exercises 🏅

A) ลองอธิบายการทำงานของ JS ของโค้ดตัวนี้

```js
let number = 200;

multiplyBy10(number);

function multiplyBy10(inputNumber) {
  return inputNumber * 10;
}
```

<br><hr><br>

B) ลองอธิบายการทำงานของ JS ของโค้ดตัวนี้

```js
let number = 200;

let multiplyBy10 = multiplyBy(10);
let multiplyBy20 = multiplyBy(20);

multiplyBy10(number);
multiplyBy20(number);

function multiplyBy(value) {
  return function calculateMultiplyValue(number) {
    return number * value;
  };
}
```
