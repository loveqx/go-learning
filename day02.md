# 结构体
go语言仅仅支持封装，不支持继承(super)和多态(override)
继承和多态在go语言中用接口来做

```
package main

import "fmt"

type treeNode struct{
	value int
	left,right *treeNode
}

// 自定义工厂函数,结构体没有构造函数 ,返回局部变量的地址！
func createTreeNode(value int) *treeNode{
	return &treeNode{value: value}

}
//结构体的方法，print函数的接受者为node，node可以直接获取他的属性，系统会自动从引用转到地址获取属性
//通过root.print()调用
//go里面的参数都是传值
//显示定义和命名方法的接受者
func (node treeNode) print(){
	fmt.Println(node.value)
}
//他和print方法功能一样，只是调用的时候不同，print2(*pRoot)
func print2(node treeNode){
	fmt.Println(node.value)
}
//node是个接收者，注意：*treeNode进行传值，直接使用treeNode的话是传引用,只有指针才能改变内容
//只有指针才能改变结构内容，不加指针只是修改引用，内容无法修改
func (node *treeNode) setValue(value int){
	node.value  = value
}

func (node *treeNode) traverse(){
	if node == nil{
		return
	}
	node.left.traverse()
	node.print()
	node.right.traverse()
}
/* 总结
1、要改变内容，必须使用指针接受者
2、结构过大也考虑使用指针接受者 
3、一致性：如有指针接受者，最好都是指针接受者
4、值接受者是go语言特有


*/
func main() {
	var root treeNode
	root = treeNode{value:3}
	root.left = &treeNode{}
	root.right = &treeNode{5,nil,nil}
	root.right.left = new(treeNode)
	root.left.right = createTreeNode(22)

	root.right.left.setValue(4)
	root.right.left.print()

	pRoot := &root
	pRoot.setValue(200)
	print2(*pRoot)
	pRoot.setValue(100)
	pRoot.print()
	pRoot.traverse()


}
```
