# Callback Functions

ก่อนอื่นเรามารู้จักกับ setTimeout กันก่อน

## setTimeout

setTimeout คือ Built-in JS function ที่ทำให้สามารถ delay การทำงานของ function ที่ส่งเข้าไปตามระยะเวลาที่กำหนดได้เป็น millisecond (ms)

```js
function showGreetingMessage() {
  console.log("Hello John !");
}

setTimeout(showGreetingMessage, 1000);

console.log("I am going to run first !");
```

<br><hr><br>

## Callback Function

เมื่อเราเจอ Code ที่มันรันแล้วไม่รู้ว่าจะเสร็จตอนไหนเราไม่สามารถบอกได้ ถ้านานมันก็จะ Block การทำงานของ Code บรรทัดต่อไปแน่นอน ดังนั้นเราจะมี Concept ของ Callback Function เข้ามาช่วย

**ตัวอย่าง**

```js
let getFacebookPosts = function (userId, onFinished) {
  setTimeout(function () {
    onFinished("Facebook posts data");
  }, 1300);
};

getFacebookPosts("A001", function onFinished(postsData) {
  console.log(postsData);
});

doOtherThings();
processSomething();
```

จาก Code ข้างบน

เราสมมุติว่า getFacebookPosts เป็น function ที่ทำการขอข้อมูลจาก Facebook Server เราไม่รู้ว่ามันจะทำงานเสร็จเมื่อไหร่ ซึ่งเราจะทำการจำลองด้วย `setTimeout` ถ้า getFacebookPosts resolve ข้อมูลสำเร็จ มันทำการเรียกใช้ Callback Function `onFinished` และส่งข้อมูลที่ได้มาผ่านเข้าไปใน parameter `postsData`

⚠️ แต่ในโลกของความเป็นจริงนั้น เราอาจจะมี Function การทำงานที่เราไม่รู้ว่ามันจะทำงานเสร็จเมื่อไหร่ มากกว่า 1 Functions แน่นอน คำถามเราคือ **ถ้า Functions เหล่านั้นทำงานเสร็จ ในเวลาที่ไม่เท่ากัน เราจะเรียงการทำงานของ Function พวกนั้นให้เป็นลำดับยังไงตามที่เราอยากจะได้**

สิ่งที่เราต้องทำก็คือ Callback Function ซ้อน Callback Function จากตัวอย่างต้านล่าง สมมุติว่าเรามี Function ที่ทำงานไม่รู้จะเสร็จเมื่อไหร่อยู่ 3 ตัว ก็คือ

- `getUser` เป็น function ที่รับ userId และ Callback Function ที่ชื่อว่า onFinished ที่มันจะถูกเรียกใช้เมื่อเวลาผ่านไป 3000 ms
- `getPosts` เป็น function ที่รับ user และ Callback Function ที่ชื่อว่า onFinished ที่มันจะถูกเรียกใช้เมื่อเวลาผ่านไป 1000 ms
- `getComments` เป็น function ที่รับ post และ Callback Function ที่ชื่อว่า onFinished ที่มันจะถูกเรียกใช้เมื่อเวลาผ่านไป 1500 ms

เราอยากจะเรียงลำดับตามนี้ เราจะต้อง getUser ก่อน ถึงจะเอาข้อมูล User แล้วไป getPosts จากนั้นเอาข้อมูล Post ไป getComments สิ่งที่เราต้องทำก็คือ

- เราจะต้อง getUser แล้วเรียกใช้ getPosts ข้างใน onFinished ของ getUser
- จากนั้น เราจะเรียกใช้ getComments ข้างใน onFinished ของ getPosts ซ้อนกันไปเรื่อย ๆ เพื่อให้มันทำงานเป็นลำดับต่อ ๆ กันไป

**ตัวอย่าง**

```js
let getUser = (userId, onFinished) => {
  setTimeout(() => {
    onFinished("user data");
  }, 3000);
};

let getPosts = (user, onFinished) => {
  setTimeout(() => {
    onFinished("posts data");
  }, 1000);
};

let getComments = (post, onFinished) => {
  setTimeout(() => {
    onFinished("comments data");
  }, 1500);
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

<br><hr><br>

## ปัญหาของ Callback functions

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

เพราะเหตุนี้ เราจึงต้องการเครื่องมือที่ทำให้เราอ่านโค้ดได้ง่ายขึ้น ในรูปแบบของ **Synchronous, Sequential, และ Blocking**
