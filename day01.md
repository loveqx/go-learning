#基础语法day01

## 一、变量定义

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

## 二、内建变量类型

### 1、布尔 字符串
bool，string

### 2、整形（有符号、u无符号）
(u)int,(u)int8,(u)int16,(u)int32,(u)int64,uintptr

### 3、字符
byte,rune(类似char，长度32位)

### 4、浮点数、复数
float32，float64，complex64,complex128

## 三、常量定义

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

### 变量定义要点
1、变量类型写在变量名之后
2、编译器可以推测变量类型
3、没有char，只有rune
4、原生支持复数类型



##  四、条件语句


### if
```
func bounded(v int) int{
   if v > 100 {
     return 100
   } else if v < 0 {
     return 0
   } else {
     return v
 
   }

}
```

```
if contents,err := ioutil.ReadFile(filename); err == nil {

   fmt.Println(string(contents))

} else {
    
    fmt.Println("cannot print file contents", err1)


}
```


### switch
```
func grade(score int) string{
    switch {

        case score < 60:
            return "F"
        case core < 80:
            return "C"
        case score < 90:
            return "B"
        default:
            return "A"

    }
}

```


## 五、循环for 
```
//正常循环
sum := 0
for i :=1;i<=100; i++{
    sum +=1
}

```


```
// 单条件循环

const filename = "abc.txt"
func printFile(filename string) {

    file, err := os.Open(filename)
    if err != nil{
        panic(err)
   }

    scanner := bufio.NewScanner(file)
    for scanner.Scan() {
      fmt.Println(scanner.Text())
    }

}
```

```
//死循环，无while

func forever(){

  for {
    fmt.Println("循环中....") 
 }
}
```



###  语句总结


#### 1、for if后面的条件没有括号
#### 2、if 条件里可以定义变量
#### 3、 没有while
#### 4、 swittch 不需要break，也可以直接switch多个条件


## 六、函数

### 普通函数
```
func eval(a,b int ,op string) (int ,error){

    switch op{

       case "+":
           return a + b,nil
       case "-":
           return a - b,nil
       case "*":
           return a * b,nil
       case "/":
           q,_ := div(a,b)
           return q,nil
       default:
           return 0,fmt.Errorf("unsupported operation: #{op}")

   }


}

func div(a, b int) (q, r int){

    return a / b, a % b
} 

```


### 函数为参数

```
func apply(op func(int ,int) int, a, b int) int{
       p := reflect.ValueOf(op).Pointer()
       opName := runtime.FuncForPC(p).Name()
       fmt.Printf("calling function %s with args" + "(%d, %d)\n",opName, a, b)
       return op(a, b)

}

// 调用
rt = apply(func(a , b int) int{
    retun int(math.Pow(float64(a), float64(b)))
    },3, 4)

}
```

### 可变参数的函数
```
func sum(numbers ...int) int{
    s := 0
    for i := range numbers {

      s += number[i]
    }
    return s

}

// 调用

fmt.Println(sum(1,2,3,4,5))
```

## 七、指针

Go语言使用值传递？引用传递？Go语言只有值传递一种。
// 指针初体验

```

func pointTest(){
    var a int = 2
    var pa *int = &a
    *pa = 40
    fmt.Println(a)    

}


// 2个数交换
func swap(a, b int) (int, int ){
	a, b = b, a
	return a,b

}
// 调用
a, b := 3,4
a, b = swap(a,b)

// 2个数交换
func swap1(a, b int) (int, int ){
	return b,a

}
// 调用
a, b := 3,4
a, b = swap(a,b)

// 2个数交换
func swap2(a, b *int){
	*b,*a = *a, *b
}
// 调用
a, b := 3,4
swap2(&a,&b)
fmt.Printf("swap2 after，a and b is %d,%d",a,b)

```


















































