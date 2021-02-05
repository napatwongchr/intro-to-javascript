# Callback Functions & Web Browser API

## setTimeout

setTimeout คือ Built-in JS function ที่ทำให้สามารถ delay การทำงานของ function ที่ส่งเข้าไปตามระยะเวลาที่กำหนดได้เป็น millisecond (ms)

```js
function showGreetingMessage() {
  console.log("Hello John !");
}

setTimeout(showGreetingMessage, 1000);

console.log("I am going to run first !");
```

⚠️ **ปัญหาของ Callback functions**

- **Inversion of Control** คือ การที่เรามีโค้ดที่เรารันเองส่วนหนึ่ง แล้วมีโค้ดอีกส่วนหนึ่งโยนให้คนอื่นไปรันให้

```js
trackCheckout(orderInfo, function finishCheckout() {
  chargeCreditCard(orderInfo);
  goToHomePage();
});
```

ปัญหาหลัก ๆ ของ Inversion of Control คือ **"Trust Issues"**

เราต้องมั่นใจว่า Callback ที่ส่งเข้าไปนั้นมันจะไม่ถูกเรียกหลายครั้ง

- **Callback hell** - Response data จะสามารถ Access ได้จาก Callback function เท่านั้น และ Callback hell ยังทำให้เราอ่านโค้ดได้ยาก เพราะว่ามันไม่สอดคล้องกับการทำงานของสมองเรา 🤯

**ตัวอย่าง**

```js
let getUser = (userId, onFinished) => {
  setTimeout(() => {
    onFinished("user data");
  }, 1000);
};

let getPosts = (user, onFinished) => {
  setTimeout(() => {
    onFinished("posts data");
  }, 1000);
};

let getComments = (post, onFinished) => {
  setTimeout(() => {
    onFinished("comments data");
  }, 1000);
};

getUser("user_1", function onFinished(userData) {
  console.log("User data: ", userData);
  getPosts(userData, function onFinished(postData) {
    console.log("Posts data: ", postData);
    getComments(postData, function onFinished(commentData) {
      console.log("Comments data: ", commentData);
    });
  });
});
```

เพราะเหตุนี้ เราจึงต้องการเครื่องมือที่ทำให้เราอ่านโค้ดได้ง่ายขึ้น ในรูปแบบของ **Synchronous, Sequential, และ Blocking**
