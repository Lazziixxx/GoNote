一：函数签名
（1）如何判断函数类型相同？
Q：相同的形参列表和返回值列表
func add(a,b int) int {return a+ b}
func sub(x,y int) (c int) {c = x - y ;return c} - 类型相同

可以用type op func(int, int) int 定义函数类型
因此函数名可以看作函数类型的常量，并且可以赋值给函数类型变量，通过变量调用改函数
类似：
存在func sum(int, int) int {...}
f := sum
val := f(1, 2

二：匿名函数
匿名函数区别与有名函数，可以看作函数字面量，可以赋值给函数变量，也可以当作实参作为返回值，或者直接被调用；
