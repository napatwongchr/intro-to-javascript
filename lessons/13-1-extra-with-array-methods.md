## More on Array methods

Array methods ที่น่าสนใจ และใช้บ่อยมาก ๆ คือ

- Array.map()
- Array.filter()
- Array.reduce()

<br><hr><br>

## Array.map()

เป็น method ที่ทำการเปลี่ยนแปลงของแต่ละชิ้นใน array ให้อยู่ในรูปแบบใหม่

**ตัวอย่าง #1** เราจะทำการ x2 กับตัวเลขทุกตัวที่อยู่ใน Array

```js
const numbers = [1, 2, 3, 4];

numbers.map(function multiplyNumberBy2(number) {
  return number * 2;
});
```

**ตัวอย่าง #2** เราจะติด Tag ห้องเรียนให้กับชื่อนักเรียนที่อยู่ใน Array

```js
const studentList = ["Anny", "James", "Nan"];

studentList.map(function concatStudentRoomTag(student) {
  return student + "-201";
});
```

🌟 **ตัวอย่าง #3** เราจะลอง Map ข้อมูลใน Array ให้เป็น HTML Element ดูกัน

```js
const studentList = ["Anny", "James", "Nan"];

studentList.map(function createListItemElement(student) {
  return `<li class="student-name">${student}</li>`;
});
```

<br><hr><br>

## Array.filter()

เป็น method ที่ทำการกรองของที่อยู่ใน array ออกมาจามเงื่อนไขที่เรากำหนด

**ตัวอย่าง #1** ทำการกรองตัวเลขที่น้อยกว่า 30

```js
const numbers = [100, 2000, 10, -20, 6, 1500];

numbers.filter(function checkNumberLessThan30(number) {
  return number < 30;
});
```

**ตัวอย่าง #2** ทำการกรองหนังสือที่มีคำว่า "Beauty" อยู่ใน String

```js
const bookNames = [
  "Let Me Tell You What I Mean",
  "Life Among the Terranauts",
  "The Beauty of Living Twice",
  "Black Beauty",
  "Monstrous Beauty",
];

bookNames.filter(function containBeautyWord(bookName) {
  return bookName.includes("Beauty");
});
```

🌟 **ตัวอย่าง #3** ทำการกรอง bill ที่จ่ายเงินด้วยเงินสด

```js
const bills = [
  {
    orderId: "A001",
    paymentType: "Cash",
    totalPrice: 2500,
  },
  {
    orderId: "A002",
    paymentType: "Credit Card",
    totalPrice: 4000,
  },
  {
    orderId: "A003",
    paymentType: "Credit Card",
    totalPrice: 6000,
  },
];

bills.filter(function getPayByCash(bill) {
  return bill.paymentType == "Cash";
});
```

<br><hr><br>

## Array.reduce()

เป็น method ที่ทำให้เรารวมของใน array เป็นค่าค่าเดียว

**ตัวอย่าง #1**

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

numbers.reduce(function (accumulator, currentValue) {
  return accumulator + currentValue;
}, 0);
```

🌟 **ตัวอย่าง #2** ทำการ Sum totalPrice ของ Bill ทั้งหมด

```js
const bills = [
  {
    orderId: "A001",
    totalPrice: 2500,
  },
  {
    orderId: "A002",
    totalPrice: 4000,
  },
  {
    orderId: "A003",
    totalPrice: 6000,
  },
];

bills.reduce(function (accumulator, bill) {
  return accumulator + bill.totalPrice;
});
```
