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