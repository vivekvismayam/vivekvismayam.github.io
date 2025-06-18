# 10 “Good to Know” JavaScript Tips You Probably Aren’t Using⚡


&nbsp;

These are few JS tips and that i use and few informations that suprised me when i came across.— thought I'd share them with you all!

---

## Destructure with Defaults

**🧠 What it does**: Allows you to provide fallbacks if properties are missing or null/undefined the object while extracting the values from objects.

```js
let user={name:"Vivek",phone:"12345"}
let { name = "Guest", age = 18 } = user || {};
console.log(name); // Vivek
console.log(age); // 18
```
&nbsp;

In this example, the name and age has been provided with default values

Destructuring lets you define default values. The `user || {}` .This ensures destructuring doesn’t crash if `user` is `null`.

You can use it while dealing with optional or partially loaded data from APIs or user input and want to avoid undefined values.

>Read More about [Destructuring with default value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring#default_value) in mdn web docs

---

## Object.freeze() to Lock Configs

**🧠 What it does**: Prevents changes to an object.A frozen object can no longer be changed: new properties cannot be added, existing properties cannot be removed, their enumerability, configurability, writability, or value cannot be changed, and the object's prototype cannot be re-assigned.

```js
const CONFIG = Object.freeze({ mode: "production" });
CONFIG.mode = "debug"; // ❌ No effect
console.log(CONFIG.mode); // 'production'
```

&nbsp;

In the above example, the mode property of CONFIG object does not get changed as the CONFIG is freezed. Freezing an object prevents extensions and makes existing properties non-writable and non-configurable.

`Object.freeze()` sets `writable` and `configurable` to `false` for all properties, locking their values.

Use it when you want to protect configuration or constant values from being changed anywhere in the code.

>Read More about [Object.freeze()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze) in mdn web docs

---

## Get Unique Items with Set

**🧠 What it does**: Removes duplicate values from an array using `Set`.

```js
const nums = [1, 2, 2, 3];
const unique = [...new Set(nums)];
console.log(unique); // [1, 2, 3]
```
&nbsp;

A `Set` stores only unique values. Spreading it back into an array gives you the result you want.

When you need a quick, clean deduplication — e.g., Ids,Selected Values etc

>Read More about [Removing duplicates from an array using sets](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set#remove_duplicate_elements_from_an_array) in mdn web docs

---

## Optional Chaining + Nullish Coalescing

Most of us might be already using this. But just wanted to call out this remembering how helpful this is.

**🧠 What it does**: Safely accesses deep object properties and assigns defaults if the value is `null` or `undefined`.

```js
const book = { author: null };
const bio = book?.author?.bio ?? "Not available";
console.log(bio); // 'Not available'
```

Optional chaining (`?.`) short-circuits if any part is `null` or `undefined`, and `??` ensures fallback only if the result is nullish (not `0`, `''`, or `false`).

Use this when you have complex objects — such as JSON APIs with missing fields.

> Read More about [Optional chaining](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) and [Nullish Coalescing](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing) in mdn web docs

---

## Locale-Aware Sorting

Ever came across scenario where you have to sort using names, and you have some special charecters in the name?

**🧠 What it does**: Sorts strings correctly based on language/locale rules.

```js
const names = ["Émile", "Anna", "Zo"];
names.sort((a, b) => a.localeCompare(b));
console.log(names); // ['Anna', 'Émile', 'Zoë']
```


`.localeCompare()` respects Unicode and diacritics, unlike default `sort()` which uses UTF-16 order.

You can use it for Sorting names or content in a multilingual app or user-facing UI.

>Read More about [localeCompare()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare) in mdn web docs

---

## Use `.at()` for Clean Indexing

**🧠 What it does**: Accesses array items from the front or back using positive or negative indices.

```js
const letters = ["a", "b", "c", "d"];
console.log(letters.at(-1)); // 'd'
console.log(letters.at(0)); // 'a'
```

instead of writing `arr[arr.length - 1]` , you can simply write a cleaner syntax arr.at(-1)

>Read More about [at()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at) in mdn web docs

---

## Labeled Loops for Nested Breaks

This is something i have never used. But it is good to know this is possible in JS

**🧠 What it does**: Lets you break or continue out of a specific outer loop from inside nested loops.

```js
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
];

outerLoop: for (let i = 0; i < matrix.length; i++) {
  innerLoop: for (let j = 0; j < matrix[i].length; j++) {
    if (matrix[i][j] === 5) {
      console.log(`Found at [${i}, ${j}]`);
      break outerLoop;
    }
  }
}
```

By labeling a loop (`outerLoop:`), you can directly break out of or continue to that loop — cleaner than using flags or extra functions.

>Read More about [Lableled Statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label) in mdn web docs

---

## Type Of NaN

We all know, NaN stands for “Not a number”. But do you know what `typeof(NAN)` returns??

Yes, NaN is of type number!!  
In JS NaN is considered as a special number and hence its type is 'number'.

>Read More about [NaN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label) in mdn web docs

---

## Objects Are Compared By Reference

Did you know that in JavaScript, `[2] == [2]` returns `false` — even though both arrays look identical!

Because arrays are objects, and in JavaScript, objects are compared by reference, not by value.  
Each [2] creates a new array in memory, so they're not the same object.

```js
console.log([2] == [2]); // false
```
🔁 Same contents ≠ same reference.


📌 Always remember: when comparing arrays (or objects), use reference equality only when you're sure they're the same instance — or compare contents manually.


---

## Null vs Undefined


Most of us know null and undefined are not the same.but what exactly is the difference?

The null value represents the intentional absence of any object value where A variable that has not been assigned a value is of type undefined.

the differences listed out below.

| Feature | `null` | `undefined` |
|:---|:---|---|
|Meaning	|"Intentional absence of value"	|"Value has not been assigned yet"|
|Type	|object	|undefined|
|Set |by	Developer (manually)	|JavaScript (automatically)|
|Typical use	|To reset or clear a value	|When a variable is declared but not assigned|
|Equality (==)	|null == undefined → true	|Same as null|
|Strict Equality |(===)	null === undefined → false	|Different types|


>did you know that undefined is not a reserved keyword in js. That means you can actually use undefined as a variable, but you should never do it, or your code will be too difficult to maintain and debug.
>```js
>function test(){
>  const undefined = "foo"; //🚫NEVER DO THIS🚫
>  console.log(undefined, typeof undefined); // foo string
>}
>test()
>``` 


> Read More about [null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/null) and [undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined) in mdn web docs

---

## ✅ Final Thoughts

This might’ve been a refresher for some of you — and that’s perfectly fine. Not every concept is life-changing or used daily, but keeping these little things in mind can make you a sharper developer over time. It’s the kind of knowledge that doesn’t always show up in your day-to-day coding, but when it does… you’ll be glad you remembered it. 😊

Do post down a comment if you support this 😊
