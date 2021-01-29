# Arrow Function

Arrow function เป็นรูปแบบการเขียน function อีกรูปแบบหนึ่ง แต่มันมีความสามารถพิเศษของมันอยู่ที่ไม่เหมือน function ปกติ แต่ตอนนี้เราจะฝึกให้คุ้นชินกับรูปแบบกันก่อนนะ

Function ปกติเราจะเขียนแบบนี้

```javascript
function showGreetingMessage() {
  console.log("Hello, All !");
}

showGreetingMessage();
```

มาเปลี่ยนให้เป็นรูปแบบของ Arrow function กัน

```javascript
const showGreetingMessage = () => {
  console.log("Hello, All !");
};

showGreetingMessage();
```

ลองมาดูตัวอย่างเพิ่มเติม

```javascript
function showMessage(message) {
  setTimeout(function showMessageLater() {
    console.log(message);
  }, 1000);
}

showMessage("Hi, Everyone !");
```

เปลี่ยนเป็น arrow function

```javascript
const showMessage = (message) => {
  setTimeout(() => {
    console.log(message);
  }, 1000);
};

showMessage("Hi, Everyone !");
```

## Exercises 🏅

เปลี่ยนรูปแบบของ function ปกติเหล่านี้ให้อยู่ในรูปแบบของ Arrow function

```javascript
function showStudentName(name) {
  console.log("Student name is " + name);
}
```

```javascript
const showListItems = function () {
  console.log("List items");
};
```

```javascript
let group = {
  title: "Our Group",
  students: ["John", "Pete", "Alice"],

  showList: function showList() {
    this.students.forEach(function (student) {
      // Error: Cannot read property 'title' of undefined
      console.log(this.title + ": " + student);
    });
  },
};
```
