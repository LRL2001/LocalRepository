# Stream API(流)

### Java8新特性：流。  
流```(Stream)```的主要作用是对集合```(Collection)```中的数据进行各种操作，增强了集合对象的功能。  
### 流的设计思想
![](/Pic/流的设计思想.png)
使用普通Java代码，重点是使用对象完成各种各样的逻辑，加上语法代码比较多，就会导致整个代码比较繁复。  
使用了```Stream API```，系统会自动完成很多操作，加上利用```Lambda```表达式大幅简化了语法，开发者的注意力重点就可以转变为捋清数据计算的步骤，不用太关心变量类型，变量赋值，对象转换等，编程的重点更加清晰。

### 创建流有三种方式
#### 直接创建
```
import java.util.stream.Stream;

Stream<String> stream = Stream.of("苹果","西瓜","哈密瓜","菠萝");
```
#### 由数组转化
```
import java.util.stream.Stream;

String[] fruitArray = new String[] {"苹果","西瓜","哈密瓜","菠萝"}
Stream<String> stream = Stream.of(fruitArray);
```
#### 由集合转化
```
import java.util.stream.Stream;

List<String>fruits=Arrays.asList(
    new Fruit("苹果"),
    new Fruit("西瓜"),
    new Fruit("哈密瓜"),
    new Fruit("菠萝")
);
Stream<String>stream=fruits.stream();
```
### 迭代流
```
stream.forEach(System.out::println);
```
##### 聚合操作
1. 过滤 ```filter()```
2. 映射 ```map()```
3. 排序 ```sorted()```
4. 摘取 ```limit()```  

例如：
```
 pupils.stream()
        .filter(pupil->pupil.getAverageScore()>=80&&pupil.getViolationCount()<1)
        .map(pupil -> {
            if(pupil.getAverageScore()>85){
                 pupil.setMessage(pupil.getName()+"同学您的成绩优秀，恭喜入围");
            }
            else{
                pupil.setMessage(pupil.getName()+"同学您的成绩优良，恭喜入围");
            }
            return pupil;
        })
        .sorted((pupil1,pupil2)->{
            return pupil2.getAverageScore()-pupil1.getAverageScore();
        })
        .limit(3)
        .forEach(pupil -> {
            System.out.println(pupil.getMessage());
        });

```
### 1. 过滤（filter()方法）
对流中的数据对象进行过滤
```
List<Pupil> pupils = new ArrayList<>();
// 这里假设小学生数据对象已经存入了

pupils.stream()
    .filter(pupil -> pupil.getAverageScore() >= 80)
    .forEach(pupil -> {System.out.println(pupil.getName());});
```
> *过滤其实是条件选择，是if条件语句，所以->后面的可以用()括起来*
### 2. 映射（map()方法）
```
numbers.stream()
    .map(num -> {
        return num * num;
    })
    .forEach(System.out::println);
```
>*return返回的对象会代替流中的参数对象*
### 3. 排序（sorted()方法）
```
students.stream()
    // 实现升序排序
    .sorted((student1, student2) -> {
        return student1.getRollNo() - student2.getRollNo();
    })
    .forEach(System.out::println);
```
>*student1指代后一个元素，student2指代前一个元素*  
>*返回非正数表明两个相比较的元素需要交换位置，返回正则不需要*
>*因此升序1-2*
### 4. 摘取（limit()方法）
```
numbers.stream()
    .sorted((n1, n2) -> n2 - n1)
    .limit(3)
    .forEach(System.out::println);
```
>*```limit```的作用是返回流开头的前n个元素*

### 流合并（```reduce()方法```）
```
Student result = students.stream()
    .reduce(new Student("", 0),
        (a, b) -> {
            a.setMidtermScore(a.getMidtermScore() + b.getMidtermScore());
            return a;
        }
    );

System.out.println(result.getName() + " - " + result.getMidtermScore());
```
>- 第一个参数，是作为缓存角色的对象  
>- 第二个参数，是lambda表达式，完成计算。
>- 因此，当有第一个参数时  
>   - a变量就不再指代流中的第一个参数了，专门指代缓存角色的对象，即reduce方法的第一个参数对象（例子中也就是```Student("",0)```）  
>   - b变量依次指代流中的每个元素，包括第一个元素

### 流合并（```collect()方法```）
```
import java.util.stream.Collectors;

List<String> numResult = numbers.stream()
    .sorted((n1, n2) -> n2 - n1)
    .limit(3)
    .map(a -> "" + a)
    .collect(Collectors.toList());

String string = String.join("-", numResult);
System.out.println("字符串是: " + string);
```
>本例中`collect()`方法就是将流中收集的元素存放到`numResult`这个`String`类型的`List`集合中去，而`collect()`方法的参数`Collectors.toList()`就是将`stream`类型转化成`List`类型  

>为了能够把最终结果转化为字符串打印输出调用了`map()`方法把流中原来的整数映射成字符串`(""+a)`

### 并行流（`parallelStream()`）
改变串行计算模式，改为并行计算模式
其余和串行一样
>**注意：当流中每个数据元素之间有逻辑依赖关系时不能使用并行计算，会出bug**