# Learn JavaScript: Fundamentals

Date: September 19, 2026
Link: https://www.codecademy.com/courses/learn-javascript-fundamentals
Status: Done

# **JavaScript Fundamentals — Quick Reference**

## **Printing and Comments**

The `console` is a built-in object, and `.log()` is a method on it. Whatever we put inside the parentheses gets printed to the console.

```jsx
console.log('Learning JavaScript');
```

Comments are lines the computer ignores; they exist for human readers. A single-line comment starts with `//`, and a multi-line comment is wrapped between `/*` and `*/`.

```jsx
// This explains the next line
console.log(5);

/*
Everything in here
is ignored when the program runs.
*/
```

## **Data Types**

JavaScript has eight fundamental data types. The first seven are called **primitive types** — the simplest, most basic kinds of data. **Object** is the exception: it's a more complex type used to group related data together.

| **Type** | **Example** | **Note** |
| --- | --- | --- |
| Number | `42`, `3.14` | Covers both whole numbers and decimals — there's no separate "integer" type. |
| BigInt | `123456789012345n` | For numbers too large for the regular Number type; ends with `n`. |
| String | `'text'` or `"text"` | Single quotes are the more common convention. |
| Boolean | `true` / `false` | Only two possible values, written without quotes. |
| Null | `null` | Represents the *intentional* absence of a value. |
| Undefined | `undefined` | A variable that's been declared but never given a value. |
| Symbol | — | A unique identifier, rarely needed early on. |
| Object | `{}` | A collection of related data — not a primitive. |

> **Note:** `null` and `undefined` look similar but mean different things — `null` is a value a programmer deliberately assigned, while `undefined` means "nothing was assigned at all."
> 

## **Arithmetic Operators**

`+` `-` `*` `/` and `%` (the remainder, or *modulo*, operator).

```jsx
console.log(17 % 5); // 2 — because 5 fits into 17 three times, leaving 2 left over
```

## **Strings: Concatenation, Interpolation, Properties, and Methods**

The `+` operator also works on strings — it joins them together (*concatenation*):

```jsx
console.log('Good' + ' morning'); // 'Good morning'
```

A cleaner alternative is **string interpolation** using template literals — strings wrapped in backticks (```) instead of regular quotes, with variables inserted using `${}`:

```jsx
const lang = 'JavaScript';
console.log(`Currently learning ${lang}`); // 'Currently learning JavaScript'
```

> **Note:** Template literals only work with backticks. Regular single or double quotes will just print `${lang}` literally as text.
> 

Every data type instance has **properties** (stored information, accessed without parentheses) and **methods** (actions, called with parentheses):

```jsx
console.log('hello'.length);        // 5 — a property
console.log('hello'.toUpperCase()); // 'HELLO' — a method
```

## **Built-in Objects**

Besides `console`, JavaScript ships with other useful objects, like `Math`:

```jsx
Math.random();                    // a random decimal from 0 (inclusive) to 1 (exclusive)
Math.floor(4.9);                  // 4 — always rounds down, never to the nearest whole number
Math.floor(Math.random() * 50);   // a random whole number from 0 to 49
```

---

## **Variables**

A variable is a named container that stores a value in memory. There are three keywords used to declare one:

| **Keyword** | **Reassignable?** | **Must have a value on declaration?** | **Note** |
| --- | --- | --- | --- |
| `var` | Yes | No | The pre-ES6 way of declaring variables; rarely used in modern code. |
| `let` | Yes | No (defaults to `undefined`) | The default choice whenever the value will change later. |
| `const` | **No** | **Yes** | Reassigning throws a `TypeError`; declaring without a value throws a `SyntaxError`. |

> **Note:** `const` prevents the *variable itself* from being reassigned — it doesn't freeze the value inside it. A `const` array or object can still have its contents modified; you just can't point that variable name at a completely different value.
> 

### **Assignment Shorthand**

```jsx
let n = 10;
n += 5;  // same as n = n + 5  → 15
n -= 2;  // → 13
n *= 2;  // → 26
n /= 2;  // → 13
n++;     // increment by 1 → 14
n--;     // decrement by 1 → 13
```

### **typeof**

```jsx
typeof 'text';   // "string"
typeof 42;       // "number"
typeof true;     // "boolean"
```

`typeof` always returns a *string* describing the type — never the type itself.

### **A Bit of History**

ES6 (also called ES2015) is the biggest update JavaScript has ever had. It introduced `let`, `const`, template literals, arrow functions, and classes — features so central that ES6 is often nicknamed "Modern JavaScript."

---

## **Control Flow**

By default, a program executes top-to-bottom, left-to-right. Conditional statements let the program make decisions and skip or run blocks of code based on whether something is true.

### **if / else / else if**

```jsx
if (score > 90) {
  console.log('Excellent');
} else if (score > 70) {
  console.log('Good');
} else {
  console.log('Needs more practice');
}
```

> **Note:** In an `if / else if` chain, JavaScript runs the code for the **first condition that evaluates to true**, top to bottom, and skips every condition after it — even if more than one of them would have been true.
> 

### **Comparison Operators**

| **Operator** | **Meaning** |
| --- | --- |
| `===` | strictly equal (same value **and** same type) |
| `!==` | strictly not equal |
| `>` `<` `>=` `<=` | greater than / less than (or equal to) |

> **Note:** `1 === '1'` evaluates to `false`. `===` checks type as well as value, so a number is never strictly equal to a string that merely looks the same.
> 

### **Truthy and Falsy Values**

Any value gets converted to `true` or `false` when evaluated inside a condition. Only these values are **falsy**:

```
false   0   -0   0n   ""   null   undefined   NaN
```

Everything else — including an empty array `[]` or empty object `{}` — is **truthy**.

### **Logical Operators**

| **A** | **B** | **`A && B`** | **`A || B`** |
| --- | --- | --- | --- |
| false | false | false | false |
| false | true | false | true |
| true | false | false | true |
| true | true | true | true |
- `&&` (AND) returns `true` only when **both** sides are true.
- `||` (OR) returns `true` when **at least one** side is true.
- `!` (NOT) flips a value: `!true` becomes `false`.

> **Important note:** `&&` and `||` don't always return a plain `true`/`false` — they return the actual value of whichever side decided the result (this is called *short-circuit evaluation*):
> 
> 
> ```jsx
> let username = '';
> let displayName = username || 'Guest'; // '' is falsy, so || returns the right-hand value
> console.log(displayName); // 'Guest' — not the boolean true
> ```
> 
> This pattern is a common shorthand for assigning default values.
> 

### **Ternary Operator**

A compact stand-in for an `if...else` with exactly two outcomes:

```jsx
let fee = isMember ? 0 : 20;
// if isMember is true, fee = 0; otherwise, fee = 20
```

### **switch**

```jsx
switch (day) {
  case 'Fri':
    console.log('Almost the weekend');
    break;
  case 'Sat':
  case 'Sun':
    console.log('Weekend');
    break;
  default:
    console.log('Just a regular day');
}
```

> **Note:** Without `break`, execution doesn't stop at the matching case — it *falls through* and keeps running every case after it (including `default`) until it hits a `break` or reaches the end of the block. This is different from `if/else`, which only ever runs one block.
> 

---

## **Review — Easy-to-Mix-Up Points**

- `===` checks type and value together; always prefer it over `==`.
- `&&` and `||` return one of the original operand values, not just literal `true`/`false`.
- In an `if/else if` chain, only the first true condition runs — order matters.
- `switch` without `break` falls through to later cases.
- `const` blocks reassigning the variable, not editing the contents of an object or array it holds.
- The falsy list is short and fixed: `false, 0, -0, 0n, "", null, undefined, NaN`. Anything else — even a seemingly "empty" `[]` or `{}` — is truthy.

# 📘 Learning Notes — رحلتي في تعلم البرمجة

مستودع لتوثيق ملخصات الكورسات والتعلم الذاتي في رحلتي للانتقال إلى تطوير الويب — **منفصل عن ريبو كورس JavaScript Everywhere الرسمي**، ومخصص للكورسات والمصادر الخارجية المكمّلة.

## 🎯 الهدف من الريبو

- توثيق التعلم أولًا بأول بدل ما يضيع.
- بناء سجل عملي وقابل للمراجعة لكل مفهوم اتعلمته.
- مصدر حقيقي أربطه في بروفايلي المهني (LinkedIn) كإثبات تقدم فعلي.

## 🗂️ هيكل الريبو

```
└── external-courses/          # كورسات منفصلة مكمّلة (مثل Codecademy)
    └── codecademy-js-fundamentals.md
```

> ملحوظة: ممكن يتضاف فولدر مخصص لملخصات JavaScript Everywhere هنا لاحقًا لو قررت كده، لكنه دلوقتي منفصل تمامًا عن الريبو الرسمي للكورس.
> 

## 📝 شكل كل ملف ملخص

كل ملف بيتبع نفس القالب عشان يبقى الريبو متّسق وسهل المراجعة:

```markdown
# Session X — [العنوان]
**Date:** YYYY-MM-DD
**Course:** [اسم الكورس]

## اللي اتعلمته
- ...

## حاجة استغربتها أو فهمتها لأول مرة
...

## كود مهم / Snippet
\`\`\`js
// كود توضيحي
\`\`\`

## أسئلة لسه محتاجة إجابة
- ...
```

## 📌 السياق

- المسار الرئيسي (**JavaScript Everywhere**، بدأ 5 سبتمبر 2026) له ريبو خاص به منفصل عن هذا المستودع.
- خلفية سابقة: تطوير ووردبريس (Gutenberg / drag-and-drop).

## 🔗 روابط

- [LinkedIn](https://claude.ai/chat/38dc96d1-cf68-477d-83a1-20bd8f4fccb3#)