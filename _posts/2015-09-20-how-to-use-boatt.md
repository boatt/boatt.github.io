---
layout: post
title: EventBus的使用和原理剖析
tags:
- boatt
- Jacman
categories: boatt
description: 在编程过程中，当我们想通知其他组件某些事情发生时，我们通常使用观察者模式，正式因为观察者模式非常常见，所以在jdk1.5中已经帮助我们实现了观察者模式，我们只需要简单的继承一些类就可以快速使用观察者模式，在Android中也有一个类似功能的开源库EventBus，可以很方便的帮助我们实现观察者模式，那么我们就开始学习如何使用EventBus.
---
> 在编程过程中，当我们想通知其他组件某些事情发生时，我们通常使用观察者模式，正式因为观察者模式非常常见，所以在jdk1.5中已经帮助我们实现了观察者模式，我们只需要简单的继承一些类就可以快速使用观察者模式，在Android中也有一个类似功能的开源库EventBus，可以很方便的帮助我们实现观察者模式，那么我们就开始学习如何使用EventBus.
>
>       在接下来的内容中，我首先会介绍如何使用EventBus,然后再简单的学习一下EventBus的底层实现原理，因为仅仅学习如何使用总是感觉内心不够踏实，万一哪天出了Bug也无从下手，了解了它的基本实现后，就会用得游刃有余。好了 废话不多说，下面开始学习吧
>
> 1、下载EventBus库：
>
> EvnetBus的下载地址：https://github.com/greenrobot/EventBus.git
>
> 2、将EventBus.jar放入自己工程的libs目录即可
>
> 3、定义一个事件，这个事件一旦被EventBus分发出去就是代表某一件事情发生了，这个事件就是某个观察者关心的事情(不需要继承任何类)
>
> 4、定义观察者，然后将该观察者注册到EventBus
>
> 5、由EventBus分发事件，告知观察者某一件事情发生了
>
> 6、使用完成后从EventBus中反注册观察者。
>
> 熟悉观察者模式的朋友肯定对于上面的流程非常熟悉，其实和观察模式基本是一样的。但是也是有区别的。在观察者模式中，所有的观察者都需要实现一个接口，这个接口有一个统一的方法如:
>
> public void onUpdate()；
>
> 然后当某一个事件发生时，某个对象会调用观察者的onUpdate方法通知观察者某件事情发生了，但是在EventBus中不需要这样，EventBus中是这样实现的：
>
> 在EventBus中的观察者通常有四种订阅函数（就是某件事情发生被调用的方法）
>
> 1、onEvent
>
> 2、onEventMainThread
>
> 3、onEventBackground
>
> 4、onEventAsync
>
> 这四种订阅函数都是使用onEvent开头的，它们的功能稍有不同,在介绍不同之前先介绍两个概念：
>
> 告知观察者事件发生时通过EventBus.post函数实现，这个过程叫做事件的发布，观察者被告知事件发生叫做事件的接收，是通过下面的订阅函数实现的。
>
> onEvent:如果使用onEvent作为订阅函数，那么该事件在哪个线程发布出来的，onEvent就会在这个线程中运行，也就是说发布事件和接收事件线程在同一个线程。使用这个方法时，在onEvent方法中不能执行耗时操作，如果执行耗时操作容易导致事件分发延迟。
>
> onEventMainThread:如果使用onEventMainThread作为订阅函数，那么不论事件是在哪个线程中发布出来的，onEventMainThread都会在UI线程中执行，接收事件就会在UI线程中运行，这个在Android中是非常有用的，因为在Android中只能在UI线程中跟新UI，所以在onEvnetMainThread方法中是不能执行耗时操作的。
>
> onEvnetBackground:如果使用onEventBackgrond作为订阅函数，那么如果事件是在UI线程中发布出来的，那么onEventBackground就会在子线程中运行，如果事件本来就是子线程中发布出来的，那么onEventBackground函数直接在该子线程中执行。
>
> onEventAsync：使用这个函数作为订阅函数，那么无论事件在哪个线程发布，都会创建新的子线程在执行onEventAsync.
>
> 下面就通过一个实例来看看这几个订阅函数的使用吧
>
> 1、定义事件：
>
> ```
> public class AsyncEvent
> {private static final String TAG = "AsyncEvent";
>   public String msg;
>   public AsyncEvent(String msg)
>   {
>     this.msg=msg;
>   }
> }
> ```
>
> 其他的事件我就不都贴出来了，我会提供代码的下载的。
>
> 2、创建观察者（也可以叫订阅者），并实现订阅方法
>
> ```
> public class MainActivity extends Activity
> {@Overrideprotected void onCreate(Bundle savedInstanceState)
>   {
>     super.onCreate(savedInstanceState);
>     setContentView(R.layout.activity_main);
>     //注册EventBus
>     EventBus.getDefault().register(this);
>   }
>
>   // click--------------------------------------start----------------------public void methodPost(View view)
>   {
>     Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>     EventBus.getDefault().post(new PostEvent("PostEvent"));
>   }
>   
>   public void methodMain(View view)
>   {
>     Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>     EventBus.getDefault().post(new MainEvent("MainEvent"));
>   }
>   
>   public void methodBack(View view)
>   {
>     Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>     EventBus.getDefault().post(new BackEvent("BackEvent"));
>   }
>   
>   public void methodAsync(View view)
>   {
>     Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>     EventBus.getDefault().post(new AsyncEvent("AsyncEvent"));
>   }
>   
>   public void methodSubPost(View view)
>   {
>     new Thread()
>     {
>       public void run() {
>         Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>         EventBus.getDefault().post(new PostEvent("PostEvent"));
>       };
>     }.start();
>    
>   }
>   
>   public void methodSubMain(View view)
>   {
>     new Thread()
>     {
>       public void run() {
>         Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>         EventBus.getDefault().post(new MainEvent("MainEvent"));
>       };
>     }.start();
>     
>   }
>   
>   public void methodSubBack(View view)
>   {
>     new Thread()
>     {
>       public void run() {
>         Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>         EventBus.getDefault().post(new BackEvent("BackEvent"));
>       };
>     }.start();
>    
>   }
>   
>   public void methodSubAsync(View view)
>   {
>     new Thread()
>     {
>       public void run() {
>         Log.d("yzy", "PostThread-->"+Thread.currentThread().getId());
>         EventBus.getDefault().post(new AsyncEvent("AsyncEvent"));
>       };
>     }.start();
>    
>   }
>   
>   
>   //click--------------------end------------------------------//Event-------------------------start-------------------------------/**
>    * 使用onEvent来接收事件，那么接收事件和分发事件在一个线程中执行
>    * @param event
>    */public void onEvent(PostEvent event)
>   {
>     Log.d("yzy", "OnEvent-->"+Thread.currentThread().getId());
>   }
>   
>   /**
>    * 使用onEventMainThread来接收事件，那么不论分发事件在哪个线程运行，接收事件永远在UI线程执行，
>    * 这对于android应用是非常有意义的
>    * @param event
>    */public void onEventMainThread(MainEvent event)
>   {
>     Log.d("yzy", "onEventMainThread-->"+Thread.currentThread().getId());
>   }
>   
>   /**
>    * 使用onEventBackgroundThread来接收事件，如果分发事件在子线程运行，那么接收事件直接在同样线程
>    * 运行，如果分发事件在UI线程，那么会启动一个子线程运行接收事件
>    * @param event
>    */public void onEventBackgroundThread(BackEvent event)
>   {
>     Log.d("yzy", "onEventBackgroundThread-->"+Thread.currentThread().getId());
>   }
>   /**
>    * 使用onEventAsync接收事件，无论分发事件在（UI或者子线程）哪个线程执行，接收都会在另外一个子线程执行
>    * @param event
>    */public void onEventAsync(AsyncEvent event)
>   {
>     Log.d("yzy", "onEventAsync-->"+Thread.currentThread().getId());
>   }
>   //Event------------------------------end-------------------------------------@Overrideprotected void onDestroy()
>   {
>     //取消注册EventBus
>     EventBus.getDefault().unregister(this);
>     super.onDestroy();
>   }
> }
> ```
>
> 说明:向EvnetBus中注册订阅者使用EventBus.register方法，取消订阅者使用EvnetBus.unregister方法，通知订阅者某件事情发生，调用EventBus.post方法，具体使用可以看上面的例子。在上面的例子中我创建了4中事件，并且分别中UI线程中post四个事件和在子线程中post四个事件，然后分别打印四种订阅函数所在线程的线程id.
>
> EventBus的使用都在这里了，实在是很简单，但是如果我们在此基础上理解EvnetBus的原理，那么我们就能非常轻松的使用EventBus了。
>
> 就从EvnetBus的入口开始看吧：EventBus.register
>
> ```
> public void register(Object subscriber) {
>         register(subscriber, DEFAULT_METHOD_NAME, false, 0);
>     }
> ```
>
> 其实调用的就是同名函数register，它的四个参数意义分别是：
>
> subscriber：就是要注册的一个订阅者，
>
> methodName:就是订阅者默认的订阅函数名，其实就是“onEvent”
>
> sticky:表示是否是粘性的，一般默认都是false，除非你调用registerSticky方法了
>
> priority：表示事件的优先级，默认就行，
>
> 接下来我们就看看这个函数具体干了什么
>
> ```
> private synchronized void register(Object subscriber, String methodName, boolean sticky, int priority) {
>         List<SubscriberMethod> subscriberMethods = subscriberMethodFinder.findSubscriberMethods(subscriber.getClass(),
>                 methodName);
>         for (SubscriberMethod subscriberMethod : subscriberMethods) {
>             subscribe(subscriber, subscriberMethod, sticky, priority);
>         }
>     }
> ```
>
> 通过一个findSubscriberMethods方法找到了一个订阅者中的所有订阅方法，返回一个 List<SubscriberMethod>，进入到findSubscriberMethods看看如何实现的
>
> ```
> List<SubscriberMethod> findSubscriberMethods(Class<?> subscriberClass, String eventMethodName) {
>     //通过订阅者类名+"."+"onEvent"创建一个key    String key = subscriberClass.getName() + '.' + eventMethodName;
>     List<SubscriberMethod> subscriberMethods;
>     synchronized (methodCache) {
>       //判断是否有缓存，有缓存直接返回缓存      subscriberMethods = methodCache.get(key);
>     }
>     //第一次进来subscriberMethods肯定是Null    if (subscriberMethods != null) {
>       return subscriberMethods;
>     }
>     subscriberMethods = new ArrayList<SubscriberMethod>();
>     Class<?> clazz = subscriberClass;
>     HashSet<String> eventTypesFound = new HashSet<String>();
>     StringBuilder methodKeyBuilder = new StringBuilder();
>     while (clazz != null) {
>       String name = clazz.getName();
>       //过滤掉系统类      if (name.startsWith("java.") || name.startsWith("javax.") || name.startsWith("android.")) {
>         // Skip system classes, this just degrades performance        break;
>       }
>
>       // Starting with EventBus 2.2 we enforced methods to be public (might change with annotations again)      //通过反射，获取到订阅者的所有方法      Method[] methods = clazz.getMethods();
>       for (Method method : methods) {
>         String methodName = method.getName();
>         //只找以onEvent开头的方法        if (methodName.startsWith(eventMethodName)) {
>           int modifiers = method.getModifiers();
>           //判断订阅者是否是public的,并且是否有修饰符，看来订阅者只能是public的，并且不能被final，static等修饰          if ((modifiers & Modifier.PUBLIC) != 0 && (modifiers & MODIFIERS_IGNORE) == 0) {
>             //获得订阅函数的参数            Class<?>[] parameterTypes = method.getParameterTypes();
>             //看了参数的个数只能是1个            if (parameterTypes.length == 1) {
>               //获取onEvent后面的部分              String modifierString = methodName.substring(eventMethodName.length());
>               ThreadMode threadMode;
>               if (modifierString.length() == 0) {
>                 //订阅函数为onEvnet                //记录线程模型为PostThread,意义就是发布事件和接收事件在同一个线程执行，详细可以参考我对于四个订阅函数不同点分析                threadMode = ThreadMode.PostThread;
>               } else if (modifierString.equals("MainThread")) {
>                 //对应onEventMainThread                threadMode = ThreadMode.MainThread;
>               } else if (modifierString.equals("BackgroundThread")) {
>                 //对应onEventBackgrondThread                threadMode = ThreadMode.BackgroundThread;
>               } else if (modifierString.equals("Async")) {
>                 //对应onEventAsync                threadMode = ThreadMode.Async;
>               } else {
>                 if (skipMethodVerificationForClasses.containsKey(clazz)) {
>                   continue;
>                 } else {
>                   throw new EventBusException("Illegal onEvent method, check for typos: " + method);
>                 }
>               }
>               //获取参数类型，其实就是接收事件的类型              Class<?> eventType = parameterTypes[0];
>               methodKeyBuilder.setLength(0);
>               methodKeyBuilder.append(methodName);
>               methodKeyBuilder.append('>').append(eventType.getName());
>               String methodKey = methodKeyBuilder.toString();
>               if (eventTypesFound.add(methodKey)) {
>                 // Only add if not already found in a sub class                //封装一个订阅方法对象，这个对象包含Method对象，threadMode对象，eventType对象                subscriberMethods.add(new SubscriberMethod(method, threadMode, eventType));
>               }
>             }
>           } else if (!skipMethodVerificationForClasses.containsKey(clazz)) {
>             Log.d(EventBus.TAG, "Skipping method (not public, static or abstract): " + clazz + "."                + methodName);
>           }
>         }
>       }
>       //看了还会遍历父类的订阅函数      clazz = clazz.getSuperclass();
>     }
>     //最后加入缓存，第二次使用直接从缓存拿    if (subscriberMethods.isEmpty()) {
>       throw new EventBusException("Subscriber " + subscriberClass + " has no public methods called "          + eventMethodName);
>     } else {
>       synchronized (methodCache) {
>         methodCache.put(key, subscriberMethods);
>       }
>       return subscriberMethods;
>     }
>   }
> ```
>
> 对于这个方法的讲解都在注释里面了，这里就不在重复叙述了，到了这里我们就找到了一个订阅者的所有的订阅方法
>
> 我们回到register方法：
>
> ```
> for (SubscriberMethod subscriberMethod : subscriberMethods) {
>             subscribe(subscriber, subscriberMethod, sticky, priority);
>         }
> ```
>
> 对每一个订阅方法，对其调用subscribe方法，进入该方法看看到底干了什么
>
> ```
> private void subscribe(Object subscriber, SubscriberMethod subscriberMethod, boolean sticky, int priority) {
>     subscribed = true;
>     //从订阅方法中拿到订阅事件的类型    Class<?> eventType = subscriberMethod.eventType;
>     //通过订阅事件类型，找到所有的订阅（Subscription）,订阅中包含了订阅者，订阅方法    CopyOnWriteArrayList<Subscription> subscriptions = subscriptionsByEventType.get(eventType);
>     //创建一个新的订阅    Subscription newSubscription = new Subscription(subscriber, subscriberMethod, priority);
>     //将新建的订阅加入到这个事件类型对应的所有订阅列表    if (subscriptions == null) {
>       //如果该事件目前没有订阅列表，那么创建并加入该订阅      subscriptions = new CopyOnWriteArrayList<Subscription>();
>       subscriptionsByEventType.put(eventType, subscriptions);
>     } else {
>       //如果有订阅列表，检查是否已经加入过      for (Subscription subscription : subscriptions) {
>         if (subscription.equals(newSubscription)) {
>           throw new EventBusException("Subscriber " + subscriber.getClass() + " already registered to event "              + eventType);
>         }
>       }
>     }
>
>     //根据优先级插入订阅    int size = subscriptions.size();
>     for (int i = 0; i <= size; i++) {
>       if (i == size || newSubscription.priority > subscriptions.get(i).priority) {
>         subscriptions.add(i, newSubscription);
>         break;
>       }
>     }
>     //将这个订阅事件加入到订阅者的订阅事件列表中    List<Class<?>> subscribedEvents = typesBySubscriber.get(subscriber);
>     if (subscribedEvents == null) {
>       subscribedEvents = new ArrayList<Class<?>>();
>       typesBySubscriber.put(subscriber, subscribedEvents);
>     }
>     subscribedEvents.add(eventType);
>     //这个是对粘性事件的，暂时不讨论    if (sticky) {
>       Object stickyEvent;
>       synchronized (stickyEvents) {
>         stickyEvent = stickyEvents.get(eventType);
>       }
>       if (stickyEvent != null) {
>         postToSubscription(newSubscription, stickyEvent, Looper.getMainLooper() == Looper.myLooper());
>       }
>     }
>   }
> ```
>
> 好了，到这里差不多register方法分析完了，大致流程就是这样的，我们总结一下：
>
> 1、找到被注册者中所有的订阅方法。
>
> 2、依次遍历订阅方法，找到EventBus中eventType对应的订阅列表，然后根据当前订阅者和订阅方法创建一个新的订阅加入到订阅列表
>
> 3、找到EvnetBus中subscriber订阅的事件列表，将eventType加入到这个事件列表。
>
> 所以对于任何一个订阅者，我们可以找到它的 订阅事件类型列表，通过这个订阅事件类型，可以找到在订阅者中的订阅函数。
>
> register分析完了就分析一下post吧，这个分析完了，EventBus的原理差不多也完了...
>
> ```
> public void post(Object event) {
>     //这个EventBus中只有一个，差不多是个单例吧，具体不用细究    PostingThreadState postingState = currentPostingThreadState.get();
>     List<Object> eventQueue = postingState.eventQueue;
>     //将事件放入队列    eventQueue.add(event);
>
>     if (postingState.isPosting) {
>       return;
>     } else {
>       postingState.isMainThread = Looper.getMainLooper() == Looper.myLooper();
>       postingState.isPosting = true;
>       if (postingState.canceled) {
>         throw new EventBusException("Internal error. Abort state was not reset");
>       }
>       try {
>         while (!eventQueue.isEmpty()) {
>           //分发事件          postSingleEvent(eventQueue.remove(0), postingState);
>         }
>       } finally {
>         postingState.isPosting = false;
>         postingState.isMainThread = false;
>       }
>     }
>   }
> ```
>
> post里面没有什么具体逻辑，它的功能主要是调用postSingleEvent完成的，进入到这个函数看看吧
>
> ```
> private void postSingleEvent(Object event, PostingThreadState postingState) throws Error {
>     Class<? extends Object> eventClass = event.getClass();
>     //找到eventClass对应的事件，包含父类对应的事件和接口对应的事件    List<Class<?>> eventTypes = findEventTypes(eventClass);
>     boolean subscriptionFound = false;
>     int countTypes = eventTypes.size();
>     for (int h = 0; h < countTypes; h++) {
>       Class<?> clazz = eventTypes.get(h);
>       CopyOnWriteArrayList<Subscription> subscriptions;
>       synchronized (this) {
>         //找到订阅事件对应的订阅，这个是通过register加入的（还记得吗....）        subscriptions = subscriptionsByEventType.get(clazz);
>       }
>       if (subscriptions != null && !subscriptions.isEmpty()) {
>         for (Subscription subscription : subscriptions) {
>           postingState.event = event;
>           postingState.subscription = subscription;
>           boolean aborted = false;
>           try {
>             //对每个订阅调用该方法            postToSubscription(subscription, event, postingState.isMainThread);
>             aborted = postingState.canceled;
>           } finally {
>             postingState.event = null;
>             postingState.subscription = null;
>             postingState.canceled = false;
>           }
>           if (aborted) {
>             break;
>           }
>         }
>         subscriptionFound = true;
>       }
>     }
>     //如果没有订阅发现，那么会Post一个NoSubscriberEvent事件    if (!subscriptionFound) {
>       Log.d(TAG, "No subscribers registered for event " + eventClass);
>       if (eventClass != NoSubscriberEvent.class && eventClass != SubscriberExceptionEvent.class) {
>         post(new NoSubscriberEvent(this, event));
>       }
>     }
>   }
> ```
>
> 这个方法有个核心方法 postToSubscription方法，进入看看吧
>
> ```
> private void postToSubscription(Subscription subscription, Object event, boolean isMainThread) {
>     //第一个参数就是传入的订阅，第二个参数就是对于的分发事件，第三个参数非常关键：是否在主线程switch (subscription.subscriberMethod.threadMode) {
>     //这个threadMode是怎么传入的，仔细想想？是不是根据onEvent,onEventMainThread,onEventBackground,onEventAsync决定的？case PostThread:
>       //直接在本线程中调用订阅函数
>             invokeSubscriber(subscription, event);
>             break;
>         case MainThread:
>             if (isMainThread) {
>         //如果直接在主线程，那么直接在本现场中调用订阅函数  invokeSubscriber(subscription, event);
>             } else {
>         //如果不在主线程，那么通过handler实现在主线程中执行，具体我就不跟踪了  mainThreadPoster.enqueue(subscription, event);
>             }
>             break;
>         case BackgroundThread:
>             if (isMainThread) {
>         //如果主线程，创建一个runnable丢入线程池中  backgroundPoster.enqueue(subscription, event);
>             } else {
>         //如果子线程，则直接调用  invokeSubscriber(subscription, event);
>             }
>             break;
>         case Async:
>       //不论什么线程，直接丢入线程池
>             asyncPoster.enqueue(subscription, event);
>             break;
>         default:
>             throw new IllegalStateException("Unknown thread mode: " + subscription.subscriberMethod.threadMode);
>         }
>     }
> ```
>
> 好了 ，对于EventBus的分析就到这里了，有哪里分析不对的，欢迎拍砖。。。