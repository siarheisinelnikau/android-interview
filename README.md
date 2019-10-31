## Questions for interview.
## Position - Android Developer (j - junior, m - middle, s - senior).


### OOP
* j What is OOP? (in English, since our native language is Russian)
* j Explain SOLID
* m Class Naming (Why Helper and Manager isn't good names?)
* m How GC works (can it resolve circular dependencies?)

### Algorithms
* s What is the difference between o(n) and O(n)?

### Collections
* m List/Collection/Set, what are the differences
* m ArrayList/LinkedList
* m Map/Set/Tree, HashMap/HashSet, AbastractMap/TreeMap/LinkedHashMap

### Multithreading/Concurrency
* s Memory Model (happen-before) and memory consistency properties
* s wait/notify, why do we need it for "synchronized" block
* m Thread.sleep()/Thread.yield()/Thread.join()
* m ThreadLocal, "volatile" keyword
* m Executors/ExecutorServices - ThreadPoolExecutor/ScheduledThreadPoolExecutor, FutureTask/ForkJoinTask
* s ConcurrentLinkedQueue/ConcurrentLinkedDeqeue
* s LinkedBlockingQueue/ArrayBlockingQueue/SynchronousQueue/PriorityBlockingQueue/DelayQueue/TransferQueue(LinkedTransferQueue)
* s Semaphore/CountDownLatch/CyclicBarrier/Phaser/Exchanger
* s ConcurrentHashMap/ConcurrentSkipListMap/ConcurrentSkipListSet/CopyOnWriteArrayList/CopyOnWriteArraySet
* m Atomic/compareAndSet

### Rx2
* m Observable/Single/MayBe/Completable + XxxSource
* s Flowable and backpressure
* m Subjects/Processors - BehaviorSubject/PublishSubject
* m map/flatMap/concatMap, switchMap?
* m onErrorReturn
* m subscribeOn/observeOn
* s compose/lift, when to use?
* s Schedulers

### DB
* s SQL - select/where/join(left/right/inner/outer/cross)/group by
* s SQLite limitations
* m SQLite - data types
* m Cyrillic issues
* m SQL vs NOSQL

### Room
* m Benefit
* s How to declare many-to-many relation?

### Android Core
* m Main Thread, lifecycle
* m Looper/Handler/HandlerThread
* m AsyncTask/Loader
* j Application/Activity/ContentProvider(Resolver)/BroadcastReceiver/Service
* m App Bundle
* m ART vs Dalvik (Ahead of Time vs JIT)
* s AlarmManager, JobSchedulaer, WorkManager
* m Service limitations

### Android UI (AndroidX)
* s Method "measure" (RelativeLayout - double measuring issue)
* s Method "layout"
* s draw/onDraw
* m CoordinatorLayout, ConstraintLayout
* j Selectors
* j Density, mipmap vs drawable
* s Animation in Android, Animation/ViewPropertyAnimator/Animator/Transition, How to Animate Layout Changes

### Dagger2
* s Reason/Benefit
* s Inheritance vs Sub-component
* m Scope

### Patterns
* m Architecture patterns - MVP, MVC, MVVM, MVI
* s Clean Architecture, Dependency Rules, Communication Between ViewModel and Repository
* m Singleton/Multition - why is it so bad?
* m Facade, abstract factory, immutable, strategy, state, builder, composite
* s Adapter/bridge/Proxy, the difference

### Kotlin
* m Visibility Modifiers (difference in java for "internal")
* m Class "Any"
* m Data classes/copy()/componentXX(), destructive declaration
* s Inline classes and limitations; inline classes vs type aliases; inline methods, reified
* j Objects/Companion objects
* m Annotations (JvmField, JvmStatic, JvmOverloads, etc.)
* m hashcode/equals
* m ArrayList/MutableList/Array
* m Nested and inner classes, anonymous inner classes
* m Enum, sealed classes
* m Operator overloading
* s Generics - in/out and difference between super/extends in Java, Type projections, Declaration-site variance, Generic functions, Generic constraints, Type erasure
* j open class/final method/override
* j fun method(): Unit - what this code will do?
* m Secondary constructors
* j "when" keyword
* m Lambda/closure, lambda expressions and anonymous functions
* s DSL, @DslMarker
* m Delegates - by Lazy/NonNull/etc
* s ReadOnlyProperty, ReadWriteProperty, provideDelegate operator
* s KProperty<*>/KClass<*>/KCallable<out R>/KFunction<out R>
* s let/apply/also/run
* m foreach - "until", ".." ("rangeTo"), "downTo", "step", ClosedRange<T>
* m Extensions
* m Exceptions and difference between Java and Kotlin
* s Reflection
  
  ### Kotlin Coroutines
* TODO
