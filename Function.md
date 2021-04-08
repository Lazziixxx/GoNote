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

三：闭包
闭包 = 函数 + 引用环境

这里引用环境的概念就是 共享外部变量
三条原则：

1：产生多次闭包函数，每次都会生成一个外部变量的副本
比如:
func fa(x int) func(i int) int {
  return func(i int) int {
    x = x + i
    return x 
  }
}

f := fa(0)
fmt.Println(f(1)) // 1
g := fa(0)
fmt.Println(g(1)) // 1
f和g是两个x的副本


2：但是对于同一个闭包调用多次，是同一个副本
f := fa(0)
fmt.Println(f(1)) // 1
fmt.Println(f(1)) // 2

3:如果这里的x是个全局，那么无论是情况1还是2都是操作同一个副本

4：如果一个函数一次性返回多个闭包函数，这些闭包函数也共享同一个副本
func fa(a int) (func(int) int ,func(int) int）{...}
f,g := fa(1)  // f和g共享一个a的副本
