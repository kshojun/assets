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

# Array APIs
```js
// join
const fruits = [1, 2, 3];
const string = fruits.join('|'); // 1|2|3

// split
const fruits = '1,2,3';
const array = fruits.split(','); // [1,2,3]
const array = fruits.split(',', 2); // [1,2]

// reverse
const fruits = [1, 2, 3];
const result = fruits.reverse(); // [3,2,1] 返却値もfruits自体も変わる

// splice
const fruits = [1, 2, 3, 4, 5];
const result = fruits.splice(2); // result [3,4,5]  fruits [1,2]

// slice
const result = fruits.slice(2, 5); // result [3,4,5] fruits [1,2,3,4,5]

// find
class Student {
  constructor(name, age, enrolled, score) {
    this.name = name;
    this.age = age;
    this.enrolled = enrolled;
    this.score = score;
  }
}

const students = [
  new Student('A',29,true,45),//1 
  new Student('B',28,false,80),//2
  new Student('C',30,true,90),//3
];

const result = students.find(function(item, index) {
  return item.score === 90;
});

// find
// arrow function
const result = students.find((item) => item.score === 90); // 3要素

// filter
const result = students.filter((student) => student.enrolled); // 1と3要素

// map
const result = students.map((student) => student.score);// 45,80,90

// some
const result = students.some((student) => student.score < 50);// ひとつでも満たす true

// every
const result = students.every((student) => student.score < 50);// すべて満たす false

// reduce
const result = students.reduce((prev, curr) => prev + curr.score, 0);// prevには前回入れた値がくる
const avg = result / students.length;

// chain
const result = students
.map((student) => student.score)
.filter((score) => score >= 50)
.sort((a, b) => a - b)
.join();
```
