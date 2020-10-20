## 变量定义

### 1、使用var关键字
```
var a,b,c bool
var s1,s2 string = "hello","world"
```
可以放在函数内，或直接放在包内，看上去像全局变量，其实不是

### 2、使用var()集中定义变量

### 3、让编译器自动决定类型
```
var  a,b,i,s1,s2 = true,false,3,"hello","world"
```
### 4、使用 := 定义变量
```
a,b,i,s1,s2 := true,false,3,"hello","world"
```
注意：只能在函数内使用

## 内建变量类型

### 1、布尔 字符串
bool，string

### 2、整形（有符号、u无符号）
(u)int,(u)int8,(u)int16,(u)int32,(u)int64,uintptr

### 3、字符
byte,rune(类似char，长度32位)

### 4、浮点数、复数
float32，float64，complex64,complex128

## 常量定义

const finename = "abc.txt"
常量可以定义在函数内，也可以定义在包内
使用 const()集中定义常量
const 数值可以作为各种类型使用
const a,b = 3,4
var c int = int(math.Sqrt(a*a+b*b))

### 枚举类型
```
func enums(){
   const (

       cpp = 0
       java = 1
       python = 2
       golang = 3
)
   fmt.Println(cpp,java,python,golang)
}
```

等价于
```
func enums(){
   const (

       cpp = iota
       java 
       python
       golang
)
   fmt.Println(cpp,java,python,golang)
}
```

```
const (

    b = 1 << (10 * iota)
    kb
    mb
    gb
    tb
    pb

)

```