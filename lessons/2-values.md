## Values

Values ก็คือ ข้อมูล ซึ่งจะมีหลากหลาย Types เช่น ตัวเลข (Numbers), ตัวอักษรมาเรียงกัน (String), null, undefined, boolean เป็นต้น

ตัวอย่างพวกนี้คือ Values ใน JS

```javascript
340;
32.54 - 12;
0;
```

Values ข้างต้นเป็น ตัวเลข **(Numbers)** ตัวเลขสามารถเป็นค่าบวก ลบ ทศนิยม หรือ ศูนย์

```javascript
"MK Restaurant";
"MOMO Paradise";

```

Values ข้างบนตัวอักษรมาต่อ ๆ กันเป็นคำ **(String)**

```javascript
true;
false;
```

Values true และ false ข้างต้นเป็น values ที่บอกว่าจริง หรือเท็จ

```javascript
["Central", "The Mall", "Siam Paragon"]

{ name: "John", age: 20, hobbies: ["Football", "Playing Games"] }
```

JS สามารถเก็บ Values รวบกันไว้เป็น Collection ได้

- บรรทัดแรกเรียกว่า **"Array"**

  Array เป็น Collection ของข้อมูล ที่สามารถระบุตำแหน่งของข้อมูลได้ด้วย Index ข้อมูลตัวแรกที่อยู่ใน Array จะมี Index เป็น 0 ตัวต่อไปเป็น 1 2 และ 3 ไปเรื่อย ๆ

- บรรทัดต่อมาเราเรียก value แบบนี้ว่า **"Object"**

  Object เป็น Collection ของข้อมูลหลาย ๆ แบบที่เก็บไว้อยู่ในรูปแบบของ **{ key: values }** pair จากตัวอย่างข้างบนเรามี

  key name value เป็น "John"<br>
  key age value เป็น 20<br>
  key hobbies value เป็น array ของ hobby

```javascript
null;
undefined;
```

จากโค้ด ข้างบน **null** และ **undefined** เป็นค่าที่แสดงถึงความว่างเปล่า ไม่มีอยู่ ใน JS

<br><hr><br>

## ใน JS เราสามารถเช็ค types ของ values ได้ด้วย `typeof`

ยกตัวอย่างเช่น

```javascript
typeof 240;
typeof "Central";
```

<br><hr><br>

## Exercises 🏅

ให้ทำการเช็ค Types ของ Values เหล่านี้

```javascript
234 - 232;
0;

true;
false;

null;
undefined[(1, 2, 3, 4)];
{
  name: "Kenny";
}
```
