# Loops

Loops คือ การทำงานวนๆ ซ้ำ ๆ

<br><hr><br>

## Loop for

```javascript
for (let i = 0; i < 10; i++) {
  console.log("Count: " + i);
}
```

ลองมาดูกันทีละส่วน

- `i = 0` คือ ส่วนทำงานครั้งแรกตอนเข้า loop โดยการเซ็ทค่า i เป็น 0
- `i < 10` คือ เงื่อนไขที่จะทำให้ loop หยุด
- `i++` คือ ส่วนที่ทำงานทุกครั้งของ loop ในที่นี้คือ + ค่า i ขึ้นไปทีละ 1
- `console.log("Count: " + i);` คือ ส่วน body ของตัว loop

Loop สามารถนำถอยหลังได้นะ

```javascript
for (let i = 10; i > 0; i--) {
  console.log("Count: " + i);
}
```

🌟 ที่ใช้เยอะ ๆ คือเคส Loop array

```javascript
let students = ["Jamie", "Nut", "Anny"];

for (let i = 0; i < students.length; i++) {
  console.log("Students: " + students[i]);
}
```

และรูปแบบ Loop ที่น่าสนใจอีกรูปแบบนึงคือ `for of`

```javascript
let students = ["Jamie", "Nut", "Anny"];

for (student of students) {
  console.log("Students: " + student);
}
```

## Break and Continue

<br><hr><br>

## Loop while

```javascript
let i = 0;
while (i < 10) {
  console.log(i);
  i++;
}
```

<br><hr><br>

## Exercises 🏅

1. เขียน Loop ที่แสดงชื่อร้านอาหารทั้งหมดที่อยู่ใน array restaurants ด้วย loop for ธรรมดา และ for of

```javascript
let restaurants = ["MK", "KFC", "MOMO PARADISE"];

// Write your code here
```

2. ใช้ while แทนที่การใช้ loop for ในข้อ 1
3. เขียน loop หาค่าที่น้อยที่สุดใน array

```javascript
let numbers = [100, 20, 3, 1000];

// Write your code here
```
