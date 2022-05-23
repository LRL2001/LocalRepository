# Utils的一些常见常用
### ```Arrays.asList```语法
```
List<Fruit> fruits = Arrays.asList(
    new Fruit("香蕉"),
    new Fruit("苹果"),
    new Fruit("梨子"),
    new Fruit("西瓜"),
    new Fruit("荔枝")
);
```
等价于
```
List<Student> students = new ArrayList<Student>();
students.add(new Student(111, "bbbb", "london"));
students.add(new Student(131, "aaaa", "nyc"));
students.add(new Student(121, "cccc", "jaipur"));
```
### 类中重写```toString```方法
```
// 重写 toString 方法，用于后面的打印
    public String toString() {
        return this.rollNo + " " + this.name + " " + this.address + " " + this.age;
    }
```
这样可以直接使用```students.forEach(System.out::println);```来打印出你想要的值

### 随机数`Random()`
```
Random r=new Random();
r.nextInt(101);
```
>*以上代码表示0-100的随机整数*  
>*不带参数的nextInt()会生成所有有效的整数（包含正数，负数，0）*  
>*带参的nextInt(int x)则会生成一个范围在0~x（不包含X，包含0）的任意整数*
>*`int x=new Random.nextInt(100);`;则x为一个0~99的任意整数*