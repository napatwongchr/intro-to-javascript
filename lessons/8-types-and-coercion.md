# Types and Coercion

จากที่เราคุยกันไปข้างต้นว่า **JS ประกอบไปด้วย 3 ส่วนสำคัญ** ดังนี้

1. Types และ Coercion

2. Scope และ Closure

3. this และ Prototypes

<br><hr><br>

## เราจะมาดูตัวแรกกันก่อนก็คือ **Types และ Coercion**

JS จะแบ่ง Types ของข้อมูลออกเป็น **Primitives และ Objects**

1. **Primitives** ก็จะมี string, number, bigint, boolean, symbol, null and undefined

ตัวอย่างของ Primitive data types

```javascript
let values;

values = 12;
typeof values; // 'number'

values = "Hello All !";
typeof values; // 'string'

values = null;
typeof values; // 'object'

values = undefined;
typeof values; // 'undefined'

values = 2n ** 53n;
typeof values; // 'bigint'
```

2. **Objects** ก็จะหน้าตาประมาณนี้

```javascript
let employeeDetail = {
  name: "John",
  age: 20,
};

typeof employeeDetail; // 'object'

let studentNames = ["Jess", "Micky", "Anny"];

typeof studentNames; // 'object'
```

<br><hr><br>

## Type conversion (Coercion)

เราสามารถที่จะเปลี่ยนแปลง types ของ values ได้

เราสามารถเปลี่ยนแปลงได้ทั้งหมด 3 รูปแบบหลัก ๆ

1. เปลี่ยนไปเป็น String
2. เปลี่ยนไปเป็น Number
3. เปลี่ยนไปเป็น Boolean

<br><hr><br>

## ลองมาดูตัวอย่างเคสเปลี่ยนไปเป็น String กัน

```javascript
let value = true;
console.log(typeof value); // boolean

value = String(value);
console.log(typeof value); // string
```

จากตัวอย่าง เป็นการเปลี่ยน boolean ให้เป็น string ด้วย `String`

ลองดูเคสที่น่าสนใจอีก 1 เคสที่ค่อนข้างเป็นที่พูดถึงกันเยอะมาก คือ ทำไม 1 + "1" เป็น "11"

```javascript
let value = 1 + "1";
console.log(value);
```

เนื่องจาก การทำงานของ "+" ถ้า JS เห็นว่าเราพยายามจะบวก number เข้ากับ string มันจะทำการเปลี่ยน type number ให้เป็น string ดังนั้นมันเลยเอา string 1 มาต่อกับ string 1

```javascript
1 + "1";

String(1) + "1";

("11");
```

<br><hr><br>

## ตัวอย่างต่อไปเราลองดูการเปลี่ยนให้ Number บ้าง

```javascript
let foodPrice = "250";

typeof foodPrice; // 'string'

foodPrice = Number(foodPrice);

typeof foodPrice;
```

ลองดูเคสนี้หน่อยว่าเกิดอะไรขึ้่นถ้าเราใส่ string ที่ไม่ใช่ตัวเลขเข้าไปใน `Number()`

```javascript
let message = "Hello, everyone";

message = Number(message);

console.log(message);
```

ผลลัพธ์คือมันจะออกมาเป็น `NaN`

NaN ย่อมาจาก **N**ot **A** **N**umber คือ values นั้น ๆ ไม่ใช่ Number

<br><hr><br>

## ตัวสุดท้ายมาดูการเปลี่ยนให้เป็น Boolean กัน

```javascript
Boolean(1); // true
Boolean(0); // false

Boolean("hello"); // true
Boolean(""); // false
```

เราจะใช้เคสนี้ค่อนข้างเยอะในการเช็คเงื่อนไข เช่น

```javascript
let newStudents = ["John"];

if (newStudents.length) {
  let newStudent = newStudents.pop();
  registerStudentToCourse();
}
```

จากโค้ดข้างบน

- `if (newStudents.length)` คือ if (1)
- เนื่องจาก if statement จะทำการเปลี่ยน 1 เป็น true
- เงื่อนไขจึงเป็นจริง ทำให้โค้ดอยู่ตรง body ของ if ทำงาน

<br><hr><br>

## Exercises 🏅

1. ผลลัพธ์ของโปรแกรมนี้เป็นอย่างไร

```javascript
function calculateElectricBill(balance) {
  let overdueBalance = 3500;
  return balance + overdueBalance;
}

let totalPrice = calculateElectricBill("2000");
console.log(totalPrice);
```
