# 变量定义

## 1、使用var关键字
var a,b,c bool
var s1,s2 string = "hello","world"
可以放在函数内，或直接放在包内，看上去像全局变量，其实不是
使用var()集中定义变量

## 2、让编译器自动决定类型
var  a,b,i,s1,s2 = true,false,3,"hello","world"

## 3、使用 := 定义变量
a,b,i,s1,s2 := true,false,3,"hello","world"
注意：只能在函数内使用



