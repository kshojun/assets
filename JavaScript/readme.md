# 配列
```js
const fruits = [1, 2];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

for (let fruit of fruits) {
  console.log(fruit);
}

fruits.forEach(function (fruit, index) {
  console.log(fruit, index);
});

fruits.forEach((fruit, index) => {
  console.log(fruit, index);
});

fruits.forEach((fruit, index) => console.log(fruit, index));

// 後ろに入れたり出したり
fruits.push(3, 4);
console.log(fruits);

fruits.pop();
console.log(fruits);

// 前に入れたり出したり（遅い）
fruits.unshift(5);
console.log(fruits);

fruits.shift();
console.log(fruits);

// １から１個消す
fruits.splice(1, 1);

// 1から1個消して、6,7を入れる
fruits.splice(1, 1, 6, 7);

const fruits2 = [10,11];
const newFruit = fruits.concat(fruits2);

// Searching
console.log(fruits.indexOf(10)); //  10のindex
console.log(fruits.indexOf(100)); //  -1

console.log(fruits.includes(10)); // true
console.log(fruits.includes(100)); // false

// lastIndexOf
fruits.push(11);
console.log(fruits.indexOf(1)); //  0
console.log(fruits.lastIndexOf(1)); // 6
```
