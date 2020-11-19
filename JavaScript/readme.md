### Table of Contents  
- [配列](#array)

# 参照渡し・値渡し
- オブジェクトと配列は参照渡し、それ以外は値渡し（他の言語のそれとは違う）
- 配列はslice, concatしてから渡すと値渡しになる

<a name="array" />
# 配列
```js
// declare
const fruits = [1, 2];

// for
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

// for...of
for (let fruit of fruits) {
  console.log(fruit);
}

// forEach
fruits.forEach((fruit, index) => {
  console.log(fruit, index);
});

// forEach
fruits.forEach((fruit, index) => console.log(fruit, index));

// 後ろから入れる
fruits.push(3, 4);

// 後ろから取り出す
fruits.pop();

// 前に入れたり出したり（遅い）
fruits.unshift(5);

fruits.shift();

// １から１個消す
fruits.splice(1, 1);

// 1から1個消して、6,7を入れる
fruits.splice(1, 1, 6, 7);

// 配列をつなげる
const arr = [1,2];
const arr2 = [3,4];
const newArr = arr.concat(arr2);

// Searching
console.log(fruits.indexOf(10)); //  10のindex
console.log(fruits.indexOf(100)); //  -1

// Check if including
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

// find(array)
const arr = [
  { "type": "abc", "value": "1" },
  { "type": "abc", "value": "2" },
]
const result = arr.find((v) => { return v.value == 1 })

// find(object)
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

# JSON
```js
// Object to JSON
let json = JSON.stringfy(['apple', 'banana']);

const rabbit = {
  name: 'abc',
  color: 'white',
  birthDate: new Date(),
  jump: () => {console.log('jump')} // methodはJSONに含まれない
};
let json = JSON.stringfy(rabbit);// {"name": "abc", "color": "white"}

let json = JSON.stringfy(rabbit, ['name']);// {"name": "abc"}

let json = JSON.stringfy(rabbit, (key, value) => {
  return key === 'name' ? 'aaaa' : value;
});// {"name": "aaaa", "color": "white"}

// JSON to Object
const obj = JSON.parse(json);

const obj = JSON.parse(json, (key, value) => {
  return key === 'birthDate' ? new Date(value) : value;
});
```

# Callback
```js
// 1 3 2
console.log(1);
setTimeout(() => console.log(2), 1000);
console.log(3);

// sync callback
function printCallback(print) {
  // そのまま実行
  print();
}

printCallback(() => console.log('hello'));

// async callback
function printDelay(print, second) {
  setTimeout(print, second);
}

printDelay(() => console.log('delayed'), 1000);
```

# Callback Hell Example
```js
class UserStorage {
  loginUser(id, password, onSuccess, onError) {
    setTimeout(() => {
      if (id === 'abc') {
        onSuccess(id);
      } else {
        onError(new Error('not found'));
      }
    }, 2000);
  }
  
  getRoles(user, onSuccess, onError) {
    setTimeout(() => {
      if (user === 'abc') {
        onSuccess({name: 'abc', role: 'admin'});
      } else {
        onError(new Error('no access'));
      }
    }, 1000);
  }
}

// arrow funcは引数ひとつのときは省略可能
const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your password');
userStorage.loginUser(
  id, 
  password, 
  user => {
    userStorage.getRoles(
      user,
      userWithRole => {
        alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`);
      },
      error => {
        console.log(error);
      }
    );
  },
  error => {
    console.log(error);
  }
);

# Promise
```js
// new Promiseの瞬間、実行されるので注意が必要
const promise = new Promise((resolve, reject) => {
  console.log('Executed immediately');
  setTimeout(() => {
    // resolve('abc');
    reject(new Error('no network'));
  }, 2000);
});

// consumer: then, catch, finally
promise
  .then((value) => {
    console.log(value);
  })
  .catch(error => {
    console.log(error);
  })
  .finally(() => {
    console.log('finally')
  )};

// promise chaining
const fetchN = new Promise((resolve, reject) => {
  setTimeout(() => resolve(1), 1000);
});

fetchN
.then(num => num * 2)
.then(num => num * 3)
.then(num => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(num - 1), 1000)
  });
})
.then(num => console.log(num));
```

```javascript
// Resolving callback hell using promise
class UserStorage {
  loginUser(id, password) {  
    return new Promise(resolve, reject) => {
      setTimeout(() => {
        if (id === 'abc') {
          resolve(id);
        } else {
          reject(new Error('not found'));
        }
      }, 2000);
    }
  }
  
  getRoles(user) {
    return new Promise(resolve, reject) => {
      setTimeout(() => {
        if (user === 'abc') {
          resolve({name: 'abc', role: 'admin'});
        } else {
          reject(new Error('no access'));
        }
      }, 1000);
    }
  }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your password');
userStorage.loginUser(id, password)
.then(userStorage.getRoles) //.then(user => userStorage.getRoles(user)) 省略可能
.then(user => alert(`Hello ${user.name}, you have a ${user.role} role`))
.catch(console.log);

// async, await: Promiseをもっと簡単に
function fetchUser() {
  // network request in 10 secs
  return 'abc';
}

// 10秒待たないといけない
const user = fetchUser();
console.log(user);

// async, awaitを使った構文
async function fetchUser() {
  return 'abc';// returnするとresolve
}

fecthUser().then(value => {
  console.log(value);
});

async function fetchUser() {
  throw new Error('reject!');// reject
}

fetchUser().catch(error => {
  console.log(error);
});
```
