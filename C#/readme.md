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

# 関数
void FloatToInt(float f, string d = "default") {
   print((int)f);
   print(d);
}

int FloatToInt(float f, string d = "default") {
   return (int)f;
}

# アクセサー
public class Test2 {
  private int a;
  public int b;
  
  public void A() {
  }
  private void B() {
  }
}

public class Test: MonoBehaviour {
  Test2 a;
  
  void A() {
    // Test2をnewしなくても使える
    a.a; // error
    a.b = 5;
    a.A();
    a.B(); // error
  }
}

# static
public class Test2 {
  private int a;
  public int b;
  public static int c; // 共有
}

public class Test: MonoBehaviour {
  Test2 a1;
  Test2 a2;
  Test2 a3;
  
  void A() {
    a1.b = 1;
    a2.b = 5;
    a3.b = 10;
  }
}

```
