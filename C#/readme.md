# データ型
```c#
// sbyte -128 ~ +127 1byte
// byte 0 ~ 255 1byte

// short 約-30000 ~ 約+30000 2byte  ushort  0 ~ 約+60000
// int 約-20億 ~ 約+20億 4byte  uint  0 ~ 約+40億
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

# メソッド
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

# Class
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
    
    // List データ型を限定、他はArrayListと同じ使い方
    List<int> list = new List<int>();
    
    // Hashtable（何でもあり）
    Hashtable hash = new Hashtable();
    hash.Add("a", 1);
    hash.Add("b", 2);
    hash.Add(2, 3);
    print(hash["a"]);
    print(hash[2]);
    
    // Dictionary(データ型限定)
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

# 名前空間(クラス名被り防止)
```c#
using Shojun.Twitter;// using Shojun;でもいい

namespace Shojun {
  public class Twitter {
    private int like;
    
    public void Like(int v) {
      like = v;
    }
    
    public int IsLike() {
      return like != 0;
    }
  }
}

public class Test: MonoBehaviour {
  void Start() {
    Twitter tw = new Twitter();
    tw.Like(1);
    print(tw.IsLike());
  }
}
```

```c#
// 同じクラス名を同時に使いたい場合は名前空間も明示
using Shojun.Twitter;
using Another;

namespace Shojun {
  namespace Another {
    public class Twitter {
    }
  }
  public class Twitter {
  }
}

public class Test: MonoBehaviour {
  void Start() {
    Shojun.Twitter tw = new Shojun.Twitter();
    Shojun.Another.Twitter tw2 = new Shojun.Another.Twitter();    
  }
}
```

# Constructor
```c#
public class Test: MonoBehaviour {
  public int a;
  public int b;
  
  public Test(int _a, int _b) {
    a = _a;
    b = _b;
  }
  
  void Start() {
    Test t = new Test(1, 2);
  }
}
```

# Enum
```c#
public enum Item {
  Weapon,
  Shield,
  Portion,
}

public class Test: MonoBehaviour {
  Item item;
  void Start() {    
    item = Item.Weapon;
    print(item);
  }
}
```

# Delegate（メソッドをまとめて呼び出す）
```c#
// Delegate使う前
public class Test: MonoBehaviour {
  public power;
  public defence;
  
  public void SetPower(int v) {
    power += v;
    print("power -> " + power);
  }

  public void SetDefence(int v) {
    defence += v;
    print("defence -> " + defence);
  }
  
  void Start() {
    // メソッドを個別で呼び出すと、メソッドが増えたとき、呼び出し忘れが起きやすい
    SetPower();
    SetDefence();
  }
}

// Delegate使う（他クラスからも使う場合はEventを利用）
public class Test: MonoBehaviour {
  public power;
  public defence;
  
  public delegate void Chain(int v);
  Chain chain;
  
  public void SetPower(int v) {
    power += v;
    print("power -> " + power);
  }

  public void SetDefence(int v) {
    defence += v;
    print("defence -> " + defence);
  }
  
  void Start() {
    chain += SetPower;
    chain += SetDefence;
    // 削除する場合 chain -= SetPower;
    if (chain != null) {
      chain(5);
    }
  }
}
```

# 継承
```c#
// メソッドをabstractにする場合はabstract
abstract public class Human : MonoBehaviour {
  protected string name;
  protected int age;
  
  // virtual：子クラスでOverrideできる
  protected virtual void Info() {
    print("I am a human");
  }
  
  // 子クラスに実装を強制する
  abstract protected void Name();
}

public class Student : Human {
  string schoolName;
  
  void Start() {
    schoolName = "school";
    name = "abc";
    age = 10;
    
    Info();
  }
  
  protected override void Info() {
    base.Info();
    print("I am a student");
  }
  
  protected override void Name() {
    print(name);
  }
}
```

# メンバー変数をカプセル化
```c#
// メンバー変数の数 x 2個ずつメソッドを増やさないといけない
public class Salary : MonoBehaviour {
  private int salary;
  private void SetSalary(int value) {
    salary = value;
  }
  
  public int GetSalary() {
    return salary;
  }
}
```

# プロパティを使う
```c#
public class Salary : MonoBehaviour {
  private int salary;
  public int SalaryP {
    get { return salary; }
    // 必ずvalueにしないといけない
    // このset自体を書かなくてもいい
    private set { salary = value; }
  }
  // 自動プロパティ
  public int Bonus { get; set; }
  
  void Start() {
    SalaryP = 10;
    print(SalaryP);
    Bonus = 2;
    print(Bonus);
  }
}
```

# Indexer(配列のように扱える)
```c#
public class Record {
  public int[] r = new int[5];
  public int this[int index] {
    get { if (index >= r.Length) {
      Debug.Log("Out of index");// printはMonoBehaviourにあるのでDebugを使う
      return 0;
    } else {
      return r[index];
    }
    set { if (index >= r.Length) Debug.Log("Out of index"); else r[index] = value; }
  }
}

public class Test : MonoBehaviour {
  Record record = new Record();
  
  void Start() {
    record.r[0] = 3;
    // Indexerで簡潔に書ける
    record[0] = 3;        
  }
}
```

# Interface(多重継承できるようにする)
```c#
abstract public class A : MonoBehaviour {
  abstract public void Abc();
}

interface ITest {
  // メンバー変数は定義できない
  void Bbc();
}

// インターフェース同士では継承できる
interface ITest2 : ITest {
}

public class Test : A, ITest {
  public override void Abc() {
    print("abc");
  }
  
  // override不要
  public void Bbc() {
    print("bbc");
  }
}
```

