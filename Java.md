### 							<font face="楷体">**Java必备知识点总结**</font>

#### 1、list，set，map等集合操作

##### <font face="楷体">1.1  **什么是集合**</font>

&emsp;<font face="楷体">存储对象的容器，面向对象语言对事物的体现都是以对象的形式，所以为了方便对多个对象的操作，存储对象，集合是存储对象最常用的一种方式。集合的出现就是为了持有对象。集合中可以存储任意类型的对象, 而且长度可变。在程序中有可能无法预先知道需要多少个对象, 那么用数组来装对象的话, 长度不好定义, 而集合解决了这样的问题。</font>

##### <font face="楷体">1.2  **集合的分类**</font>

<font face="楷体"> ---|Collection: 单列集合</font>

​			<font face="楷体">---|List: 有存储顺序, 可重复</font>

​				<font face="楷体">---|ArrayList:数组实现, 查找快, 增删慢</font>

​					     <font face="楷体">由于是数组实现, 在增和删的时候会牵扯到数组增容, 以及拷贝元素. 所以慢。数组是可以直接按索引查找, 所以查找时较快</font>

​				<font face="楷体">---|LinkedList:链表实现, 增删快, 查找慢</font>

​					    <font face="楷体">  由于链表实现, 增加时只要让前一个元素记住自己就可以, 删除时让前一个元素记住后一个元素, 后一个元素记住前一个元素. 这样的增删效率较高但查询时需要一个一个的遍历, 所以效率较低</font>

​	     		<font face="楷体">---|Vector:和ArrayList原理相同, 但线程安全, 效率略低和ArrayList实现方式相同, 但考虑了线程安全问题, 所以效率略低</font>

​			<font face="楷体">---|Set: 无存储顺序, 不可重复</font>

​				<font face="楷体">---|HashSet</font>

​				<font face="楷体">---|TreeSet</font>

​				<font face="楷体">---|LinkedHashSet</font>

<font face="楷体">---| Map: 键值对</font>

​		<font face="楷体">---|HashMap</font>

​		<font face="楷体">---|TreeMap</font>

​		<font face="楷体">---|HashTable</font>

​		<font face="楷体">---|LinkedHashMap</font>

<table width=100%>
    <tr>
    	<th align="center"><font face="楷体">Collection</font></th>
        <th align="right">&emsp;&emsp;&emsp;<font face="楷体">使用集合对象的选择</font></th>
    </tr>
    <tr>
    	<td><font face="楷体">List</font></td>
        <td><font face="楷体">如果我们需要保留存储顺序, 并且保留重复元素, 使用List.如果查询较多, 那么使用ArrayList如果存取较多, 那么使用LinkedList如果需要线程安全, 那么使用Vector</font></td>
    </tr>
    <tr>
    	<td><font face="楷体">List</font></td>
        <td><font face="楷体">如果我们需要保留存储顺序, 并且保留重复元素, 使用List.如果查询较多, 那么使用ArrayList如果存取较多, 那么使用LinkedList如果需要线程安全, 那么使用Vector</font></td>
    </tr>
</table>

##### <font face="楷体">1.3 **集合类Collection**</font>

<font face="楷体">java.util.Collection</font>

​		<font face="楷体">---| Collection 描述所有接口的共性</font>

​			<font face="楷体">----| List 接口可以有重复元素的集合</font>

​			<font face="楷体">----| Set  接口不可以有重复元素的集合</font>

##### <font face="楷体">1.4 **集合类Collection接口的共性方法**</font>

<font face="楷体">增加：</font>

​		<font face="楷体">1：add()	将指定对象存储到容器中add 方法的参数类型是Object 便于接收任意对象</font>

​        <font face="楷体">2：addAll() 将指定集合中的元素添加到调用该方法和集合中</font>

<font face="楷体">删除：</font>

​		<font face="楷体">3：remove() 将指定的对象从集合中删除</font>

​		<font face="楷体">4：removeAll() 将指定集合中的元素删除</font>

<font face="楷体">修改：</font>

​		<font face="楷体">5：clear() 清空集合中的所有元素</font>

<font face="楷体">判断：</font>

​		<font face="楷体">6：isEmpty() 判断集合是否为空</font>

​		<font face="楷体">7：contains() 判断集合何中是否包含指定对象</font>

​		<font face="楷体">8：containsAll() 判断集合中是否包含指定集合</font>

​            <font face="楷体">使用equals()判断两个对象是否相等</font>  

<font face="楷体">获取: </font> 

​        <font face="楷体">9：int size()    返回集合容器的大小</font>

<font face="楷体">转成数组：</font>

​       <font face="楷体">10： toArray()   集合转换数组</font>

#### <font face="楷体">ArrayList:实现原理：</font>

<font face="楷体">    数组实现, 查找快, 增删慢</font>

<font face="楷体">    数组为什么是查询快?因为数组的内存空间地址是连续的.ArrayList底层维护了一个Object[] 用于存储对象，默认数组的长度是10。可以通过 new ArrayList(20)显式的指定用于存储对象的数组的长度。当默认的或者指定的容量不够存储对象的时候，容量自动增长为原来的容量的1.5倍。由于ArrayList是数组实现, 在增和删的时候会牵扯到数组增容, 以及拷贝元素. 所以慢。数组是可以直接按索引查找, 所以查找时较快可以考虑,假设向数组的0角标未知添加元素,那么原来的角标位置的元素需要整体往后移,并且数组可能还要增容,一旦增容,就需要要将老数组的内容拷贝到新数组中.所以数组的增删的效率是很低的.</font>

####    <font face="楷体">LinkList:实现原理：</font>

​       <font face="楷体"> LinkedList:链表实现, 增删快, 查找慢</font>

​         <font face="楷体">由于LinkedList:在内存中的地址不连续,需要让上一个元素记住下一个元素.所以每个元素中保存的有下一个元素的位置.虽然也有角标,但是查找的时候,需要从头往下找,显然是没有数组查找快的.但是,链表在插入新元素的时候,只需要让前一个元素记住新元素,让新元素记住下一个元素就可以了.所以插入很快.由于链表实现, 增加时只要让前一个元素记住自己就可以, 删除时让前一个元素记住后一个元素, 后一个元素记住前一个元素. 这样的增删效率较高。但查询时需要一个一个的遍历, 所以效率较低。</font>

#### 2、多线程/线程池，锁，信号量

##### 2.1、线程概述

<font face="楷体">进程：正在运行的程序，负责了这个程序的内存空间分配，代表了内存中的执行区域。</font>

<font face="楷体">线程：就是在一个进程中负责一个执行路径。</font>

<font face="楷体">多线程：就是在一个进程中多个执行路径同时执行。</font>

<font face="楷体">**多线程的好处：**</font>

1. <font face="楷体">解决了一个进程里面可以同时运行多个任务（执行路径）。</font>
2. <font face="楷体">提供资源的利用率，而不是提供效率。</font>

<font face="楷体">**多线程的弊端：**</font>

1. <font face="楷体">降低了一个进程里面的线程的执行频率。</font>
2. <font face="楷体">对线程进行管理要求额外的 CPU开销。线程的使用会给系统带来上下文切换的额外负担。</font>
3. <font face="楷体">公有变量的同时读或写。当多个线程需要对公有变量进行写操作时,后一个线程往往会修改掉前一个线程存放的数据，发生线程安全问题。</font>
4. <font face="楷体">线程的死锁。即较长时间的等待或资源竞争以及死锁等多线程症状。</font>

##### 2.2创建线程的方式

1. <font face="楷体">继承Thread类</font>

```java
class Demo extends Thread{
    public void run(){
        print();
    }
    public Demo(String name){
        super(name);
    }
    public void print(){
        for(int i=0;i<10;i++){
            try{
                this.sleep(10);
            }catch(InterrupteException e){
                e.printStackTrace();
            }
            System.out.println(this.getName()+i);
        }
    }
        public static void main(String[] args){
            Demo demo1=new Demo("张三");
            Demo demo2=new Demo("李四");
            demo1.start();
            demo2.start();
    }
}
```

2. <font face="楷体">实现Runnable接口</font>
   	1. <font face="楷体">定义了实现Runnable接口</font>
    	2. <font face="楷体">重写Runnable接口中的run方法，就是将线程运行的代码放入在run方法中</font>
    	3. <font face="楷体">通过Thread类建立线程对象</font>
    	4. <font face="楷体">将Runnable接口的子类对象作为实际参数，传递给Thread类构造方法</font>
    	5. <font face="楷体">调用Thread类的start方法开启线程，并调用Runable接口子类run方法</font>

```java
public class Demo1 {
	public static void main(String[] args) {
		MyRun my = new MyRun();
		Thread t1 = new Thread(my);
		t1.start();
		for (int i = 0; i < 200; i++) {
			System.out.println("main:" + i);
		}
	}
}
class MyRun implements Runnable {
	public void run() {
		for (int i = 0; i < 200; i++) {
			System.err.println("MyRun:" + i);
		}
	}
}
```

##### 2.3锁对象

<font face="楷体">什么是所对象？</font>

&emsp;<font face="楷体">每个java对象都有一个锁对象.而且只有一把钥匙.</font>

<font face="楷体">如何创建锁对象：</font>

&emsp;<font face="楷体">可以使用this关键字作为锁对象，也可以使用所在类的字节码文件对应的Class对象作为锁对象。如：类名.class,对象.getClass</font>

<font face="楷体">Java中的每个对象都有一个内置锁，只有当对象具有同步方法代码时，内置锁才会起作用，当进入一个同步的非静态方法时，就会自动获得与类的当前实例（this）相关的锁，该类的代码就是正在执行的代码。获得一个对象的锁也成为获取锁、锁定对象也可以称之为监视器来指我们正在获取的锁对象。</font>

<font face="楷体">因为一个对象只有一个锁，所有如果一个线程获得了这个锁，其他线程就不能获得了，直到这个线程释放（或者返回）锁。也就是说在锁释放之前，任何其他线程都不能进入同步代码（不可以进入该对象的任何同步方法）。释放锁指的是持有该锁的线程退出同步方法，此时，其他线程可以进入该对象上的同步方法。</font>

1. <font face="楷体">只能同步方法（代码块），不能同步变量或者类</font>
2. <font face="楷体">每个对象只有一个锁</font>
3. <font face="楷体">不必同步类中的所有方法，类可以同时具有同步方法和非同步方法</font>
4. <font face="楷体">如果两个线程要执行一个类中的一个同步方法，并且他们使用的是了类的同一个实例（对象）来调用方法，那么一次只有一个线程能够执行该方法，另一个线程需要等待，直到第一个线程完成方法调用，总结就是：一个线程获得了对象的锁，其他线程不可以进入该对象的同步方法。</font>
5. <font face="楷体">如果类同时具有同步方法和非同步方法，那么多个线程仍然可以访问该类的非同步方法。同步会影响性能（甚至死锁），优先考虑同步代码块。</font>
6. <font face="楷体">如果线程进入sleep（） 睡眠状态，该线程会继续持有锁，不会释放。</font>

##### 2.4正则表达式

<font face="楷体">正则表达式：其实一种规则，有自己特殊的应用,其作用就是针对于字符串进行操作。</font>

<font face="楷体">正则：就是用于操作字符串的规则,其中这些规则使用了一些字符表示。</font>

<font face="楷体"></font>