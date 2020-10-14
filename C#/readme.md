# Data Types
```c#
// sbyte -128 ~ +127 1byte
// byte 0 ~ 255 1byte

// short -30000 ~ +30000 2byte  ushort  0 ~ +60000
// int -20億 ~ +20億 4byte  uint  0 ~ +40億
// long  8byte  ulong 

// float < double < decimal 誤差が少なくなる
// float f = 4.1f;
// double d = 1.1;   
// decimal m = 4.3333m;   

// bool a = true; // false

// string s = "aaaa";
// char c = 'A';// 0065

int a = 100;
string s = a.ToString();

int a;
string b = "100";

a = int.Parse(b);
// double.Parse() など数字→文字列はParse使う
```

# 関数
```c#
// CamelCase
void FloatToInt(float f, string d = "default") {
   print((int)f);
   print(d);
}

int FloatToInt(float f, string d = "default") {
   return (int)f;
}
```

# アクセサー
```c#
public class Test2 {
  private int a;
  public int b; 
  public static int c;// 静的変数、インスタンス化不要
  
  public void A() {
  }
  private void B() {
  }
}

public class Test: MonoBehaviour {
  Test2 a1;
  Test2 a2;
  Test2 a3;
  
  void A() {
    a1.b = 1;
    a2.b = 5;
    a3.b = 10;
    
    print(a1.b);
    print(a2.b);
    print(a3.b);
    
    a1.c = 100;// インスタンス化不要
    
    a1.A();
    a1.B();// error
  }
  
  void Start() {
    A();
  }
}
```

# 演算子、条件文、三項演算子(他の言語と同じ)
```c#
// 演算子
+ - * / %  ++ -- += -= == != >= <= > < && || ! << >>

// 三項演算子
int a = a == b ? a : b;

// if
if (true) {
} else if (false) {
} else {
}

// switch
switch(input) {
  case 10:
    print(10);
    break;
  default:
    break; 
}
```

# 反復文
```c#
for (int i = 0; i < 10; i++) {
  if (i < 10) {
    continue;
  }
  if (i == 5) {
    break;
  }
}
for (;;) {
}
while(true) {
}

public class Test: MonoBehaviour {
  void Start() {
    // do~while
    int i = 0;
    do {
      i++;
    } while(i < 10);
    
    // foreach
    string text = "abcdef";
    foreach (char a in text) {
      print(a);
    }
  }
}
```

# 配列
```c#
public class Test: MonoBehaviour {
  void Start() {
    int[] arr = {1,2,3,4,5};// 追加不可
    print(arr[0]);
    print(arr.length);
    
    int[] arr = new int[2];
    arr[0] = 1;
    arr[1] = 2;

    int[] arr = new int[2]{1, 2}; // メモリー確保と同時に代入
    arr[0] = 1;
    arr[1] = 2;

    int[,] arr2 = {{1, 2}, {3, 4}}
    print(arr2[0, 1]);// arr2[0][1]ではない
    print(arr2[1, 1]);// arr2[1][1]ではない
  }
}
```

# コレクション
```c#
public class Test: MonoBehaviour {
  void Start() {
    int[] arr = new int[5]{1,2,3,4,5};
    
    // ArrayList
    ArrayList list = new ArrayList();// 何でも入る
    list.Add(1);
    list.Add(2);
    list.Add(3.3);
    list.Add("aaa");
    print(list.Count);// 4   
    
    list.Remove("aaa");// "aaa"を消す
    list.RemoveAt(0);// 1を消す
    list.RemoveRange(0, 2);// 0から2個を消す

    // 代入
    list[2] = 4;

    list.Insert(1, 1.5);// 1と2の間に入る

    list.Clear();// 初期化

    list.Contains("aaa");// true
    
    // List int限定、あとはArrayListと同じ使い方
    List<int> list = new List<int>();
    
    // Hashtable
    Hashtable hash = new Hashtable();
    hash.Add("a", 1);
    hash.Add("b", 2);
    hash.Add(2, 3);
    print(hash["a"]);
    print(hash[2]);
    
    // Dictionary
    Dictionary<string, int> dic = new Dictionary<string, int>();
    dic.Add("a", 1);
    
    // Queue FIFO(first in,first out)
    Queue<int> q = new Queue<int>();
    q.Enqueue(1);
    q.Enqueue(2);
    if (q.Count != 0) {
      print(q.Dequeue());// 1
    }
    if (q.Count != 0) {
      print(q.Dequeue());// 2
    }
    
    // Stack LIFO (last in first out)
    Stack<int> s = new Stack<int>();
    s.Push(1);
    s.Push(2);
    if (s.Count != 0) {
      print(s.Pop());// 2
    }
    if (s.Count != 0) {
      print(s.Pop());// 1
    }
  }
}

```
