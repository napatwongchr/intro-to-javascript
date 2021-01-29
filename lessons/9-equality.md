# Equality

เป็นการตรวจสอบความเท่ากันของ values

ใน JS เราจะเช็คการเท่ากันของทั้งสอง values ได้จาก **==**(Double Equal) และ **===** (Triple Equal)

ยกตัวอย่างเช่น

```javascript
let year = 2021;
let myBirthYear = 1994;

console.log(year == myBirthYear);
```

<br><hr><br>

## == ต่างจาก === ยังไงบ้าง ?​

- == สามารถให้ JS ทำ Coercion ของค่าที่เอามาเปรียบเทียบได้
- === สามารถให้ JS ทำ Coercion ของค่าที่เอามาเปรียบเทียบได้

```javascript
let value = true;
let someNumber = 1;

console.log(value == someNumber); // true
console.log(value === someNumber); // false
```
