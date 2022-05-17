# Lambda表达式
### Java8 新特性
Lambda、流、函数式编程  
这些新特性使得代码更简洁，易阅读，易维护

### Lambda表达式的基本结构
```
f->{}
```
![Lambda表达式的基本结构](/Pic/Lambda表达式.png "Lambda表达式")  

>Lambda表达式相当于一个匿名方法，但它将方法名和public void全部省略了  

当有多个参数变量或者没有参数变量时，要用()包裹起来，例如：
```
(student1,student2)->{}
()->{}
```
如果代码较为复杂，也可以为参数变量指定类型：
```
fruits.forEach((Fruit f) -> {
  System.out.println(f.getName());
});
```
### 使用Lambda表达式时可以引用局部变量
有两个规范  
1. 引用的局部变量不允许被修改
2. 参数不能与局部变量同名

### forEach()
forEach()表示循环遍历当前集合  

