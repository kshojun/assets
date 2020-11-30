# Basic Template
```c++
#include <iostream>
using namespace std;

int main () {
    cout << "Hello World" << endl;
    return 0;
}
```

# Standard Input / Output
```c++
int x, y;
cin >> x;
cin >> x >> y; // xとyに順番に入る
cout << "hello" << endl; // endl = new line
```

# 浮動小数
```c++
int a = 3, b = 2;
int r = a / 2; // 1  整数どうしの計算は小数点以下が切り捨てられる
double d = a * 1.0 / 2 // 1.5 精度の高い実数へ変換される 
printf("%.8lf\n", d); // 1.00000005
```

# PI
```c++
#include <bits/stdc++.h>
M_PI
```

# switch ~ case
stringは使えないので以下のようにする
```c++
enum stringCode {
    eFred,
    eBarney,
    eWilma,
};

string_code h(std::string const& s) {
    if (s == "Fred") return eFred;
    if (s == "Barney") return eBarney;
}

void foo() {
    switch (h(stringValue)) {
    case eFred:
        ...
    case eBarney:
        ...
    }
}
```
