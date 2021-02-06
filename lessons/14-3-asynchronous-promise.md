# Promise

Promises คือ **Object พิเศษของ** JS ที่ถูก Return มาให้เราเวลาเราเรียกใช้ Web Browser APIs เช่น function `fetch`

- ให้นึกว่า **Promises เป็นเหมือนกล่องที่รอรับของ** ที่เราจะได้กลับมาจากการทำงาน Background ของ Web Browser

- เวลาที่ Background process ของ Web Browser ทำงานเสร็จมันจะส่ง **Completion Event** มาบอกเราว่ามันทำงานเสร็จแล้ว

- หรือถ้าการทำงานเกิด Error มันจะส่ง **Error Event** มาบอกเช่นเดียวกัน

🌟 **Promise แก้ไขปัญหา Inversion of Control**

Promise จะการันตีให้เราเลยว่า

- Promise จะ Resolve ได้แค่ครั้งเดียวเท่านั้น
- Promise ไม่ Resolve ก็ Reject อย่างใดอย่างหนึ่ง

<br><hr><br>

## Promise API

```js
let getPosts = new Promise(function (resolve, reject) {
  setTimeout(() => resolve("Posts data"), 1000);
});
```

```js
let getPosts = new Promise(function (resolve, reject) {
  setTimeout(() => reject(new Error("Error !")), 1000);
});
```

<br><hr><br>

## .then .catch

### มาดู .then กันก่อน

Promise Object จะมี method ที่เรียกว่า `then`

`then` คือ method ที่รับ Callback function เข้ามา และ Callback function นี้ จะถูกเรียกใช้งานก็ต่อเมื่อ **Promise resolve** ข้อมูลออกมา

```js
let getPosts = new Promise(function (resolve, reject) {
  setTimeout(() => resolve("Posts data"), 1000);
});

getPosts.then(function onCompleted(data) {
  console.log(data); // Posts data after 1 sec
});
```

### .catch

Promise Object จะมี method ที่เรียกว่า `catch`

`catch` คือ method ที่รับ Callback function เข้ามา และ Callback function นี้ จะถูกเรียกใช้งานก็ต่อเมื่อ **Promise reject** เนื่องจากเกิด error บางอย่าง

```js
let getPosts = new Promise(function (resolve, reject) {
  setTimeout(() => reject(new Error("Error !")), 1000);
});

getPosts.catch(function onError(error) {
  console.log(error); // Show error after 1 sec
});
```

<br><hr><br>

## Chaining .then

ในโลกของความเป็นจริงนั้น เราอาจจะมี Function การทำงานที่เราไม่รู้ว่ามันจะทำงานเสร็จเมื่อไหร่ มากกว่า 1 Functions แน่นอน คำถามเราคือ ถ้า Functions เหล่านั้นทำงานเสร็จ ในเวลาที่ไม่เท่ากัน เราจะเรียงการทำงานของ Function พวกนั้นให้เป็นลำดับยังไงตามที่เราอยากจะได้

ในตัวอย่างนี้เรามีเงื่อนไขว่า เราต้อง getUser ก่อน แล้วค่อย getPosts แล้วค่อย getComments

```js
let output = (data) => {
  console.log("Data: ", data);
  return data;
};

let getUser = (userId) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("User_1"), 3000);
  });
};

let getPosts = (user) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("Posts of User_1"), 1000);
  });
};

let getComments = (post) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("Comments of Post"), 1500);
  });
};

getUser()
  .then(output)
  .then(getPosts)
  .then(output)
  .then(getComments)
  .then(output);
```

<br><hr><br>

## Exercises 🏅

A) ให้สร้าง Promise ในการ Resolve ข้อมูล

```js
let data = [
  { id: 1, firstName: "John", age: 20, hobbies: ["Football", "Badminton"] },
  { id: 2, firstName: "Anny", age: 24, hobbies: ["Badminton"] },
  { id: 3, firstName: "Anny", age: 24, hobbies: ["Badminton"] },
];
```

<br><hr><br>

B)

```js
let output = (data) => {
  console.log("Data: ", data);
  return data;
};

let getUser = (userId) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("user_1_data"), 1000);
  });
};

let getOrders = (user) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("orders_of_user_1_data"), 1000);
  });
};

let getItems = (order) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("orders_items"), 1000);
  });
};

// Write promise flow here
```

<br><hr><br>
