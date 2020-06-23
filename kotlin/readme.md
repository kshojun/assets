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
