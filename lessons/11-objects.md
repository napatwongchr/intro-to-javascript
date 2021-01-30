## Object

นอกจาก Primitive data types ที่เราเรียนกันไปแล้ว เราลองมาดู Object กันบ้าง

## การสร้าง Object

Object จะสร้างด้วย **{ }** และข้างในจะเก็บข้่อมูลอยู่ในรูปแบบของ **Key-Value pairs**

```js
let employee = {
  name: "John",
  age: 20,
  occupation: "Software Developer",
  getAge: function getAge() {
    return this.age;
  },
};
```

จากโค้ด name คือ Key และ "John" คือ Value

🌟 **ส่วนใหญ่มักเรียก Key-Value เป็น Property**

### Value Accessing

เราสามาระที่่จะ Access Value ได้โดยวิธีนี้

```js
employee.name;
employee.age;
employee.getAge();

// or

employee["name"];
employee["age"];
employee["getAge"]();
```

### Value Mutating

เราสามารถที่จะเปลี่ยนแปลง Values ได้ดังนี้

```js
employee.name = "Jamie";
employee.age = 230;
employee.getAge = function getAge() {
  console.log("Reassigned employee values");
};

// or

employee["name"];
employee["age"];
employee["getAge"]();
```

**ถ้าเราเปลี่ยนแปลง value ของ key ที่ไม่มีอยู่ใน Object จะเป็นการสร้าง key value ตัวใหม่ขึ้นมา**

🌟 **เราสามารถสร้าง Key Values ด้วยตัวแปรได้ด้วยนะ เช่น**

```js
let animals = ["rat", "cat", "whale"];
let animalCount = {};

for (let animal of animals) {
  animalCount[animal] = 1;
}
```

### Removing Values

```js
delete employee.name;
```

### Loop Object

เราสามารถ Loop Object ด้วย For in **(อย่าสับสนกับ For of ที่ใช้ Loop Array)**

```js
let user = {
  name: "John",
  surname: "Smith",
};

user.age = 25;

for (let key in user) {
  console.log(key);
  console.log(user[key]);
}
```

จริง ๆ แล้วใน JS ยังมี Object อีกหลายตัว เช่น Array, Date, เป็นต้น

## Exercises 🏅

1. เขียนโค้่ดตามนี้

- สร้าง Food Order Object เปล่า ๆ
- สร้าง property orderNumber ขึ้นมาด้วย value เป็น `A0234`
- สร้าง property address ขึ้นมาด้วย value เป็นที่อยู่สักที่
- สร้าง property paymentType ขึ้นมาด้วย value เป็น "Cash"
- สร้าง property totalPrice ขึ้นมาด้วย value เป็น 4500
- สร้าง property restaurantName ขึ้นมาด้วย value เป็น "MK"
- เปลี่ยน property paymentType เป็น "Credit Card"
- เปลี่ยน property totalPrice เป็น 2500
- ลบ property restaurantName

2. ทำการ Sum `salaries` ทั้งหมด

```js
let salaries = {
  John: 100,
  Ann: 160,
  Pete: 130,
};

// Write your code here
```

3. ทำการนับจำนวนของของที่ซ้ำใน Array

```js
let items = ["hat", "socks", "gloves", "pan", "apple pencil", "socks", "hat"];

// Write your code here
```
