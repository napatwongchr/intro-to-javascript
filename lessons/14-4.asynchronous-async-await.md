# ASYNC AND AWAIT

Async Await เป็น Syntax ที่เกิดขึ้นมาทำให้เราเขียน และเข้าใจ Promise ได้ง่ายมากยิ่งขึ้น

## ASYNC

Async เราจะใส่ไว้ข้างหน้า function ที่เราต้องการจะ return Promise ออกไป

```js
async function getCustomerDetails() {
  return {
    firstName: "Moby",
    age: 40,
    hobbies: ["Playing mobile games"],
  };
}

getCustomerDetails().then(function (data) {
  console.log("Data: ", data);
});
```

## AWAIT

Await เป็นตัวบอกว่าให้ JS รอจนกว่า Promise จะ Resolve ข้อมูล

🌟 **แต่การรอมันไม่ได้เป็นการไป Block Thread ดังนั้น JS จะสามารถไปทำงานส่วนอื่น ๆ ต่อได้**

### ลองมาดูตัวอย่าง

```js
async function getCustomerDetails() {
  return {
    firstName: "Moby",
    age: 40,
    hobbies: ["Playing mobile games"],
  };
}

const data = await getCustomerDetails();
console.log("Data: ", data);
```

⚠️ โค้ดทำงานปกติมั้ย ?​ แน่นอนว่าไม่ การใช้ await เราจำเป็นที่จะต้องใช้ภายใต async เราจะทำการเปลี่ยนแปลงโค้ดสักหน่อย

```js
async function getCustomerDetails() {
  return {
    firstName: "Moby",
    age: 40,
    hobbies: ["Playing mobile games"],
  };
}

async function main() {
  const data = await getCustomerDetails();
  console.log("Data: ", data);
}

main();
```

## Exercises 🏅

A) ให้แก้ไข Code ชุดนี้ให้อยู่ในรูปแบบ async await

```js
let output = (data) => {
  console.log("Data: ", data);
  return data;
};

let getUser = (userId) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("User_1"), 1000);
  });
};

let getPosts = (user) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("Posts of User_1"), 1000);
  });
};

let getComments = (post) => {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve("Comments of Post"), 1000);
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

B) ให้ทำการ log data จาก `getCustomerDetails` โดยไม่ใช้ await

```js
async function getCustomerDetails() {
  return new Promise(function (resolve, reject) {
    setTimeout(
      () =>
        resolve({
          firstName: "Moby",
          age: 40,
          hobbies: ["Playing mobile games"],
        }),
      1000
    );
  });
}

// Write your code here
```
