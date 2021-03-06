---&emsp;  
title: this与super&emsp;  
date: ‎2021-0‎2‎-01&emsp;  
description: Java的this与super&emsp;  
---&emsp;  
&emsp;  
## this&emsp;  
&emsp;  
**1.可以使用在实例方法中，代表当前对象。**&emsp;  
&emsp;  
没有static修饰时，变量叫做**实例变量**，方法叫做**实例方法**。实例变量和实例方法的调用都需要使用一个引用，格式为  **引用.变量名(或 .方法名)**。引用就是代表一个对象的变量，储存着对象所在的地址，**this就是一个引用**。但在一个类中使用这个类的实例变量或实例方法时，不可能知道对象的名称，所以要用this来代替对象的名称，**this储存有当前对象的地址**。所以，在一个类中使用这个类的实例变量或实例方法时，要用 **this.变量名(或 .方法名)**。&emsp;  
&emsp;  
this不能用在静态方法中，因为静态方法的使用不需要对象，静态方法中也不能用实例变量与方法。&emsp;  
&emsp;  
**2.可以利用this在一个构造器中调用另一个构造器。**&emsp;  
&emsp;  
例：&emsp;  
&emsp;  
```java
public class Answer {
    private int num;

    public Answer(int num){
        this.num = num;
    }
    
    public Answer(){
        this(42);    //可用于初始化对象，复用代码
    }
}
```
&emsp;  
## super&emsp;  
&emsp;  
前三点与this相似&emsp;  
&emsp;  
1. super：super能出现在实例方法和构造方法中。&emsp;  
&emsp;  
2. super的语法是：super. 、super()&emsp;  
&emsp;  
3. super不能使用在静态方法中。&emsp;  
&emsp;  
4. super()只能出现在构造方法第一行，&emsp;  
&emsp;  
   通过当前的构造方法去**调用父类中的构造方法**，是为了代码复用。&emsp;  
&emsp;  
   可以借助super (参数) 来访问**父类的私有属性**，从而达到初始化&emsp;  
&emsp;  
   **在构造器中，super (参数) 若没有出现，则会在构造器的第一行有一个super()，用于完成父类数据初始化 。所以，若父类中没有手动添加的无参数构造器，但是有其他有参构造器，就会编译错误。**&emsp;  
&emsp;  
5. super.大部分情况下是可以省略的。&emsp;  
&emsp;  
   父中有一个属性或方法，子中又有一个相同名字的属性或方法，如果想在子中访问父类的特征，super.不能省略。java中允许在子类中出现和父类一样的同名变量/同名属性。若在父类中一个变量不是private，则子类就会继承这个变量，但当此时子类中有一个同名变量时子类中的这个变量就会替代父类中的变量。若子类和父类中的方法相同，就是方法重写。以上两种情况中，若在子类中想访问父类的同名变量或方法就需要super。&emsp;  
&emsp;  
   &emsp;  
&emsp;  
this相当与一个引用，储存当前对象的地址&emsp;  
&emsp;  
super不是一个引用，super也不指向任何对象。super只是代表当前对象内部的那一块父类型的特征。&emsp;  
