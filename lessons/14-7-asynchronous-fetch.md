# FETCH

JS สามารถที่จะ request ขอข้อมูลจาก server ได้เพื่อที่จะเอาข้อมูลนั้น ๆ ไปทำอะไรสักอย่าง หรือทำธุรกรรมต่าง ๆ

ยกตัวอย่างเช่น

- เราสามารถที่จะ Login เพื่อเข้าระบบ
- กด Submit ข้อมูลเพื่อสมัครสมาชิก
- Etc.

การที่เราจะทำ request ได้เราจะใช้ function `fetch`

```js
async function main() {
  let url = "https://dog.ceo/api/breeds/list/all";
  let response = await fetch(url);

  if (response.ok) {
    let json = await response.json();
    console.log(json);
  } else {
    console.log("HTTP-Error: " + response.status);
  }
}

main();
```
