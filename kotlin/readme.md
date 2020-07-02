# 特徴
- コードが簡潔
- 文末のセミコロン不要
- Android開発公式言語
- 変数はNullableとNotNullに分かれ、?をつけてNullableを宣言可能
- NullPointerException(NPE)から自由
- 関数型プログラミングとOOP両方可能

# 使用可能プラットフォーム
- Kotlin/JVM 
- Kotlin/JS 
- Kotlin/Native

# Kotlin/Nativeのターゲット
- iOS
- MacOS
- Android
- Windows
- Linux
- WebAssembly

# JDK
- Oracle JDK 一部ライセンス料必要
- OpenJDK Oracle JDKとほぼ同じ
- AzulのZulu(OpenJDKを配布するサードパーティー)

# main関数だけの実行
```kotlin
fun main() {
    println("hello")
}
```
Tools > Kotlin > REPLを選んでから実行するとうまくいく

# 一般的なメモリ領域(JVMはもっと細かい)
- Code 関数など
- Data 初期化されたデータ
- Heap(動的割り当て) クラスのインスタンス(Object)。不要になったらGC
- Stack(臨時割り当て) 

# 階層
Project > Module > Package > File   
Module指定しない場合はProjectと同名のModule   
Package指定しない場合はdefaultというパッケージ

# Package
指定しない場合はdefault   
package xxx.aaa.ccc   
import xxx.aaa.ccc.Class   
import xxx.aaa.ccc.Class as OtherClass

# Other
違うModuleにあるpackageはimportできないので、jarにする必要がある   
ktファイルにclassが一つしかない場合はktが省略される   

# 変数
```kotlin
val some: String = "abcde"
val num: Int = 20
val n: Float = 40.4
```

# val VS var
- val(value) 不変
- var(variable) 可変

# 型の推論
```kotlin
val username = "AAAAA" // String
val number = 10 // Int
val e01 = 123 // Int
val e2 = 123L // Long
val e3 = 0x0F // 16進数Int
val e4 = 0b00001111 // 2進数Int
val e01 = 3.14 // Double
val e02 = 3.14F // Float
val isOpen = true // Boolean
val ch = 'c' // Char
```

## プリミティブ型は使用できない

# 整数型
- 符号あり Long, Int, Short, Byte
- 符号なし ULong, UInt, UShort, UByte

# 符号なしデータ型
```kotlin
val uint: UInt = 123u
val ushort: UShort = 65535u
val ulong: ULong = 2323223uL
val ubyte: UByte = 255u
```

# 数字を読みやすく
```kotlin
val number = 1_000_000
val cardNumber = 1233_2222_3333_4444L
val hex = 0xAB_CD_EF_FF
val bytes = 0b1111_0000
```

# データ型の限界値
- Byte.MIN_VALUE ~ Byte.MAX_VALUE
- Short.MIN_VALUE ~ Short.MAX_VALUE
- Int.MIN_VALUE ~ Int.MAX_VALUE
- Long.MIN_VALUE ~ Long.MAX_VALUE
- Float.MIN_VALUE ~ Float.MAX_VALUE
- Double.MIN_VALUE ~ Double.MAX_VALUE

# println
```kotlin
println("some: $some, num: $num")
```

# Insert File
ALT + Insert

# Auto Import
ALT + Enter

# $で文字列出力
```kotlin
val a = 1
val s = "a is $a" // a is 1
val str = "a = ${a + 2}" // a = 3
```

# nullを許容する場合
```kotlin
val a: Int? = null
val b: String? = null
```

# Safe-Calling
```kotlin
val str = null
str?.length // nullでない場合のみlengthを実行
```

# non-null断定
```kotlin
val str = null
str!!.length // strがnullかどうかチェックさせない。NPEになるのでnon-null断定は使わないこと
```

# エルビス演算子
```kotlin
val str: String? = null
println("str : ${str?.length ?: -1}") // A ?: B Aがfalseのとき、Bが実行される
```

# Casting
```kotlin
val a: Int = 1
val b: Double = a.toDouble
// 前にtoをつける
```

# ==, ===
- == 値のみ比較
- === 値と参照アドレスを比較 
```kotlin
val a: Int = 128
val b: Int = 128
val c: Int? = 128

println(a == b) // true
println(a === b) // true

println(a == c) // true
println(a === c) // false
```

# Smart Casting(自動キャスト）
```kotlin
var num: Number = 12.2
num = 10
num = 10L
num = 10.0f
```

# is
```kotlin
val num = 123
if (num is Int) {
} else if (num !is Int) {
}
```

# Any
```kotlin
var a: Any = 1
a = 20L
println("a : $a type : ${a.javaClass}")
```

# ビット演算
```kotlin
3.shl(bits) // 3.shl bits でもいい
3.shr(bits)
3.ushr(bits)
3.and(bits)
3.or(bits)
3.xor(bits)
3.inv // すべて反転
```

# 関数
```kotlin
fun sum(a: Int, b: Int): Int {
    val sum = a + b
    return sum
}
```

# 簡素化
```kotlin
fun sum(a: Int, b: Int): Int = a + b
fun sum(a: Int, b: Int) = a + b // Intに推論できるので省略
```

# デフォルト引数
```kotlin
fun sum_fun(a: Int, b: String = "default") {
    println("a $a , b $b")
}
```

# 引数の名前で渡すとデフォルト引数が最後じゃなくてもいい
```kotlin
fun main() {
    namedFun(x = 200, z = 100)
    namedFun(z = 150)
}

fun namedFun(x: Int = 100, y: Int = 200, z: Int) {
    println(x + y + z)
}
```

# 可変引数
```kotlin
fun varFun(vararg counts: Int) {
    for (num in counts) {
        println("$num")
    }
}

fun main() {
    varFun(1,2,3)
    varFun(1,2)
}
```

## KotlinはOOP, FPいずれで書いてもいい

# Functional Programming（関数型プログラミング）の特徴
- コードが簡略、高い再利用性
- ラムダ式、高次関数で構成
- 純粋関数

# 純粋関数
- 副作用のない関数
- 同じ入力引数に対して常に同じ結果を出力
- 値が予測可能
```kotlin
fun sum(a: Int, b:Int): Int {
    return a + b
}
```

# 純粋関数でない例
```kotlin
fun test() {
    val test = Some.funtion() // 外部のSomeクラスを使用
}
```
```kotlin
const val global = 10

fun main() {
    val result = someFun(1, 2)
}

fun someFun(a: Int, b: Int): Int {
    return a + b + global // 入力と関係ない外部変数使用
}
```

# 純粋関数を使う理由
- いろんな関数を組み合わせても副作用がない
- 関数の値を追跡し、予測可能なのでテストやデバッグがしやすい

# ラムダ式（匿名関数）
```kotlin
{x, y -> x + y}
```

# First Class Citizen（一級オブジェクト）
- 関数の引数で使える
- 関数の返却値で使える
- 変数に代入できる
Kotlinの関数はFirst Class Citizen   

# 高次関数(high order function)
引数と返却値にラムダ式や関数を使う関数   
```kotlin
fun main() {
    println(highFun({x, y -> x + y}, 10,20))
}

fun highFun(sum: (Int, Int) -> Int, a: Int, b: Int): Int {
    return sum(a, b)
}
```

# ラムダ式の書き方いろいろ
```kotlin
val multi: (Int, Int) -> Int = {x: Int, y: Int -> x * y}

// 表現式が2行以上
val multi: (Int, Int) -> Int = {x: Int, y: Int -> 
    println(x * y)
    x * y // 最後が返却される
}

// 宣言データ型を省略
val multi = {x: Int, y: Int -> x * y}

// 引数のデータ型を省略
val multi: (Int, Int) -> Int = {x, y -> x * y}

// エラー。データ型が推論できない
val multi　= {x, y -> x * y}

// 返却値ない
val greet: () -> Unit = { println("hello") }

// 引数がひとつのみ
val square: (Int) -> (Int) = { x -> x * x }

// 宣言部の省略
val greet = { println("hello") }
val square = { x: Int -> x * x }
```

# 参照による呼び出し
```kotlin
fun main() {
    val res = funcParam(1, 2, ::sum)
    
    hello(::text) // hello(text)ではエラー

    val likeLambda = ::sum
    println(likeLambda(3,3))
}

fun sum(a: Int, b: Int) = a + b

fun text(a: String, b: String) = "Hello, $a $b"

fun funcParam(a: Int, b: Int, c: (Int, Int) -> Int): Int {
    return c(a,b)
}

fun hello(body: (String, String) -> String): Unit {
    println(body("hello", "world"))
}
```

# 引数の数によるラムダ式の呼び出し方
```kotlin
fun main() {
    // 引数がない
    noParam({"hello"})
    noParam{"hello"}

    // ひとつ
    oneParam({a -> "hello $a"})
    oneParam{a -> "hello $a"}
    
    // two
    twoParam{a, b -> "hello $a $b"}
    
    // 引数を省略
    twoParam{_, b -> "hello $b"}
}

fun noParam(out: () -> String) = println(out())

fun oneParam(out: (String) -> String) {
    println(out("one param"))
}

fun twoParam(out: (String, String) -> String) {
    println(out("one", "two"))
}
```

# ラムダ式引数を最後に持ってくると外に出せる
```kotlin
fun main() {
    withArgs("a", "b", {a, b -> "$a $b"})
    withArgs("a", "b") {a, b -> "$a $b"}
    
    twoLambda({a, b -> "$a $b"}, {"aa"})
    twoLambda({a, b -> "$a $b"}) {"aa"}
}

fun withArgs(a: String, b: String, out: (String, String) -> String) {
    println(out(a, b))
}

fun twoLambda(first: (String, String) -> String, second: (String) -> String) {
    println(first("a", "b"))
    println(second("a"))
}
```

# ラムダ式の活用事例　１．ロック機構
```java
// JavaのLock, ReentrantLock
Lock lock = new ReentrantLock();
lock.lock();
try {
    // 保護すべきコード
} finally {
    lock.unlock();
}
```

```kotlin
var sharable = 1 // 保護すべきもの

fun <T> lock(relock: ReentrantLock, body: () -> T): T {
    relock.lock()
    try {
        return body()
    } finally {
        relock.unlock
    }
}

fun main() {
    val relock = ReentrantLock()
    
    lock(relock, {critical})
    lock(relock) {critical}
    lock(relock, ::critical)
}

fun critical() {
    shareable += 1
}
```

# ラムダ式の活用事例　２．ネットワークのコールバック関数
```kotlin
fun networkCall(onSuccess: (ResultType) -> Unit, onError: (Throwable) -> Unit) {
    try {
        onSuccess(result)
    } catch (e: Throwable) {
        onError(e)
    }
}

networkCall(result -> {

}, error -> {

});
```

# 匿名関数
```kotlin
fun (x: Int, y: Int): Int = x + y

val add: (Int, Int) -> Int = fun(x, y) = x + y
val result = add(1,2)

val add = fun(x: Int, y: Int) = x + y // anonymouse function
val add = {x: Int, y: Int -> x + y} // lambda

// 匿名関数はreturn, break, continueが使用可能
// ラムダ式は使えないので、ラベルと一緒に使わないといけない
```

# infix notation
```kotlin
// メンバーメソッド又は拡張メソッド
// 引数を一つ
// infixキーワードを使用
// . と()を省略できる

fun main() {
    // val multi = 3.multiply(10)
    val multi = 3 multiply 10
}

infix fun Int.multiply(x: Int): Int {
    return this * x;
}
```

# local function
```kotlin
// ローカル関数はローカル関数の中でしか使えない
fun a() {
    fun b() = c() // error c()を認識できない
    fun c() = println("c")
}
```

