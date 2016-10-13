---
layout: post
title: 高新技术
tags:
- java
categories: boatt
description: 高新技术.
---
## 高新技术
高新技术。

<!-- more -->
## 日志详情

> ## 反射
>
> - 1.Class   代表类的类，用来表示一个类
>
>   - 1.Class.forName();
>   - 2.对象名.getClass()
>   - 2.类名.class
>   - 基本数据类型，String，void，数组，引用类型都存在类类型Class
>   - 方法
>     - 1.newInstance(); 创建实例对象
>     - 2.getName();   获取类的名字，带包名的
>     - 3.getSimpleName(); 获取不带包名的类名
>     - 4.getMethod(方法名，方法参数的类类型);  获取指定公有的方法
>     - 5.getDeclaredMethod();   获取所有的指定的方法
>     - 6.getMethods();  获取所有公有地方法
>     - 7.getDelcaredMethods(); 获取类上面所有的方法
>     - 8.getFields();    获取所有公有的成员变量
>     - 9.getField("成员变量的名称");  通过成员变量的名字获取公有的成员变量
>     - 10.getDeclaredField("成员变量的名称");  通过成员变量的名字获取成员变量
>     - 11.getDeclaredFields();    获取所有的成员变量
>     - 12.getConstructor("","","");
>     - 13.getConstructors();
>     - 14.getDeclaredConstructor(parameterTypes);
>
>   JVM内存区域：
>   堆：
>
>   ```
>   1.存储的全部是对象，每个对象都包含一个与之对应的class的信息。(class的目的是得到操作指令)
>   2.jvm只有一个堆区(heap)被所有线程共享，堆中不存放基本类型和对象引用，只存放对象本身
>   ```
>
>   栈：
>
>   ```
>   1.每个线程包含一个栈区，栈中只保存基础数据类型的对象和自定义对象的引用(不是对象)，对象都存放在堆区中
>   2.每个栈中的数据(原始类型和对象引用)都是私有的，其他栈不能访问。
>   ```
>
>   方法区：
>
>   ```
>   1.又叫静态区，跟堆一样，被所有的线程共享。方法区包含所有的class和static变量。
>   2.方法区中包含的都是在整个程序中永远唯一的元素，如class，static变量。
>   ```
>
>   加载类
>
>   - 1.静态加载(通过new的方式获取对象，都属于静态加载)
>   - 2.动态加载
>
> - 2.Constructor  构造方法
>
>   - 1.getName(); 获取构造方法的名字
>   - 2.getParameterTypes(); 获取所有参数的类类型
>
> - 3.Method   成员方法
>
>   - 1.method.getReturnType(); 获取返回值的类类型
>   - 2.method.getName(); 获取方法的名字
>   - 3.method.getParameterTypes(); 获取所有参数的类类型
>   - 4.Field成员变量
>   - 1.getName(); 获取成员变量的名称
>   - 2.getType(); 返回成员变量的类类型
>
> - 调用反射获取的方法
>
>   ```
>      /**
>   ```
>
>   - 参数1：要执行那个对象的方法
>     - 参数2：参数
>        */
>
>
>   - method.invoke   通过反射调用类中的摸一个方法
>
> - 通过反射给成员变量赋值
>
>   - /**
>     - 参数1：给那个对象的成员变量赋值
>       - 参数2：给成员变量设置的值
>          */
>         field.set(number, "Test07...number...run");
>   - 如何给私有的成员变量赋值
>   - 1.获取成员变量的时候需要使用   getDelcaredField();
>   - 2.给成员变量设置权限
>     - field.setAccessible(true);
>   - 3.给成员变量赋值
>
> ## 注解
>
> - 分类
>   - 1.标示的注解 成员个数为0，用来标示的
>   - 2.单值注解   成员个数为1
>   - 3.完整注解   成员个数>1
> - 根据使用和用途
>   - 1.系统注解 
>     - 1.@Override  实现或者重写接口或父类中的方法
>     - 2.@Deprecated  用来标识过时地方法
>     - 3.@SuppressWarnings 用来警告用户
>   - 2.元注解
>     - 1.@Target  指定注解存放的位置
>       - 1.CONSTRUCTOR:用于描述构造器
>     - 2.FIELD:用于描述域
>     - 3.LOCAL_VARIABLE:用于描述局部变量  var a;
>       - 4.METHOD:用于描述方法
>     - 5.PACKAGE:用于描述包
>     - 6.PARAMETER:用于描述参数    //eat(@override int a)
>     - 7.TYPE:用于描述类、接口(包括注解类型) 或enum声明
>     - 2.@Retention  注解存在的位置
>       - 1.SOURCE:在源文件中有效（即源文件保留）
>     - 2.CLASS:在class文件中有效（即class保留）
>     - 3.RUNTIME:在运行时有效（即运行时保留）
>     - 3.Documented  生成文档之后注解的信息会显示在文档中
>     - 4.@Inherited 父类的类上的注解可以被子类继承，被标注的注解retention必须是runTime
> - 自定义注解
>   - 定义注解格式：
>     　　public @interface 注解名 {定义体}
>   - 注解参数的可支持数据类型：
>     　　　　1.所有基本数据类型（int,float,boolean,byte,double,char,long,short)
>     　　　　2.String类型
>     　　　　3.Class类型
>     　　　　4.enum类型
>     　　　　5.Annotation类型
>     　　　　6.以上所有类型的数组
> - 注解的处理器
>   - 方法1：<T extends Annotation> T getAnnotation(Class<T> annotationClass): 返回改程序元素上存在的、指定类型的注解，如果该类型注解不存在，则返回null。
>   - 方法2：Annotation[] getAnnotations():返回该程序元素上存在的所有注解。
>   - 方法3：boolean is AnnotationPresent(Class<?extends Annotation> annotationClass):判断该程序元素上是否包含指定类型的注解，存在则返回true，否则返回false.
>   - 方法4：Annotation[] getDeclaredAnnotations()：返回直接存在于此元素上的所有注释。与此接口中的其他方法不同，该方法将忽略继承的注释。（如果没有注释直接存在于此元素上，则返回长度为零的一个数组。）该方法的调用者可以随意修改返回的数组；这不会对其他调用者返回的数组产生任何影响。
>
> ## 动态代理
>
> ```
> 根据编译时期或者运行时期，分为动态代理和静态代理
> 静态代理就是编译时期就存在的代理类
> 动态代理是运行时存在的代理类，增强功能，过滤方法
> 动态代理的实现步骤：
> 1.定义接口
> 2.接口实现类
> 3.定义委托类和代理类的桥梁
> 4.生成代理类   Proxy.newProxyInstance(People.class.getClassLoader(), new Class[]{People.class}, studentHandler);
> 5.调用代理类中的方法
> 举例中
> 学生是委托类
> proxyInstance是代理类
> StudentHandler是链接委托类和代理类的桥梁
> retrofit是用动态代理，注解实现的，底层是okhttp。
> ```
>
> ## 线程池
>
> ```
> - 1.newCachedThreadPool 是一个可根据需要创建新线程的线程池
> - 2.newSingleThreadExecutor 创建是一个单线程池，线程池中只有一个线程
> - 3.newFixedThreadPool 创建固定大小的线程池
> - 4.newScheduledThreadPool 创建一个大小无限的线程池
> ```
>
> - 线程池实例化的参数
>
>   - new ThreadPoolExecutor(3,//核心线程数
>
>     ```
>     	5, //最大线程数
>     	5, //线程空闲时间存活时间
>     	TimeUnit.SECONDS, //存活时间的单位
>     	new LinkedBlockingQueue<Runnable>(),   //任务队列
>     	Executors.defaultThreadFactory());  //线程产生的工厂
>     ```
>
> - 线程池的工作原理
>
>   - 当任务来了之后，如果核心线程数没有满，那么就使用核心线程数，如果核心线程数满了，那么就将任务放入任务队列中，如果任务队列也满了，就开始使用最大线程数，如果最大线程数也使用满了，会抛出异常，拒绝任务。
>
> - 线程池在使用的时候最后搞成静态的。
>
> ## 依赖注入（注解+反射）
>
> ```
> dragger2，依赖注入的框架
> 用来解耦的。方便做单元测试
> ```