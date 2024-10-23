## Questions for Interview
**Position - Android Developer (j - junior, m - middle, s - senior).**

---

### OOP

- **j** What is OOP? (in English, since our native language is Russian)
- **j** Explain SOLID principles.
- **m** Class Naming (Why are "Helper" and "Manager" not good names?)
- **m** How does the Garbage Collector work? Can it resolve circular dependencies?

### Algorithms

- **s** What is the difference between **o(n)** and **O(n)**?

### Collections

- **m** Differences between List, Collection, and Set.
- **m** Compare ArrayList and LinkedList.
- **m** Explain Map, Set, Tree, HashMap, HashSet, AbstractMap, TreeMap, and LinkedHashMap.

### Multithreading/Concurrency

- **s** Java Memory Model (happens-before relationship) and memory consistency properties.
- **s** Explain `wait`/`notify` methods. Why do we need them in a `synchronized` block?
- **m** Difference between `Thread.sleep()`, `Thread.yield()`, and `Thread.join()`.
- **m** Explain `ThreadLocal` and the `volatile` keyword.
- **m** Executors and ExecutorServices - `ThreadPoolExecutor`, `ScheduledThreadPoolExecutor`, `FutureTask`, `ForkJoinTask`.
- **s** Discuss `ConcurrentLinkedQueue` and `ConcurrentLinkedDeque`.
- **s** Explain various blocking queues: `LinkedBlockingQueue`, `ArrayBlockingQueue`, `SynchronousQueue`, `PriorityBlockingQueue`, `DelayQueue`, `TransferQueue` (`LinkedTransferQueue`).
- **s** Explain synchronization utilities: `Semaphore`, `CountDownLatch`, `CyclicBarrier`, `Phaser`, `Exchanger`.
- **s** Discuss concurrent collections: `ConcurrentHashMap`, `ConcurrentSkipListMap`, `ConcurrentSkipListSet`, `CopyOnWriteArrayList`, `CopyOnWriteArraySet`.
- **m** Explain Atomic classes and the `compareAndSet` method.

### RxJava

- **m** Differences between `Observable`, `Single`, `Maybe`, and `Completable`.
- **s** What is `Flowable` and how does backpressure work?
- **m** Explain Subjects like `BehaviorSubject` and `PublishSubject`.
- **m** Discuss operators: `map`, `flatMap`, `concatMap`, `switchMap`.
- **m** Error handling operators in RxJava.
- **m** Difference between `subscribeOn` and `observeOn`.
- **s** Explain Schedulers in RxJava.

### Database (DB)

- **s** SQL queries: `SELECT`, `WHERE`, `JOIN` (LEFT, RIGHT, INNER, OUTER, CROSS), `GROUP BY`.
- **s** Limitations of SQLite.
- **m** Data types in SQLite.
- **m** Handling Cyrillic characters in databases.
- **m** Differences between SQL and NoSQL databases.

### Room

- **m** Benefits of using Room.
- **s** How to declare a many-to-many relationship in Room.
- **m** Using Room with Coroutines and Flow.
- **m** Handling database migrations in Room.
- **m** Support for database transactions in Room.

### Android Core

- **m** Main Thread and Activity lifecycle.
- **m** `Looper`, `Handler`, and `HandlerThread`.
- **m** Introduction to WorkManager and its benefits over `AsyncTask` and Loaders.
- **s** Comparing `AlarmManager`, `JobScheduler`, and `WorkManager`.
- **j** Core components: `Application`, `Activity`, `ContentProvider` (Resolver), `BroadcastReceiver`, `Service`.
- **m** Understanding App Bundle.
- **m** Overview of Android Runtime (ART) and its features like AOT and JIT compilation.
- **m** Limitations of Services.
- **m** Differences between foreground, background, and bound services.
- **m** Importance of Lifecycle-aware components.
- **m** Principles of Modern Android Development (MAD).

### Android UI (AndroidX)

- **s** Method `measure` (e.g., double measuring issue in `RelativeLayout`).
- **s** Method `layout` in custom views.
- **s** `draw`/`onDraw` methods and custom drawing.
- **m** Understanding `CoordinatorLayout` and `ConstraintLayout`.
- **j** Use of Selectors in Android.
- **j** Understanding density, and the difference between `mipmap` and `drawable` folders.
- **s** Animations in Android: `Animation`, `ViewPropertyAnimator`, `Animator`, `Transition`, and animating layout changes.
- **m** Introduction to `MotionLayout` and its use cases.
- **m** Optimizing list performance with `RecyclerView`.
- **m** Basics of Jetpack Compose.
- **s** Jetpack Compose: State management, composable functions, and recomposition.
- **s** Comparing the traditional View system with Jetpack Compose.

### Dagger and Hilt

- **s** Reason/Benefit of using Dependency Injection.
- **s** Inheritance vs. Sub-component in Dagger.
- **m** Scope in Dagger.
- **m** Benefits of Hilt over Dagger 2.
- **m** Setting up Hilt in an Android project.
- **s** Hilt components and scopes.
- **s** Role of `@EntryPoint` and `@InstallIn` annotations.

### Patterns

- **m** Architecture patterns: MVP, MVC, MVVM, MVI.
- **s** Clean Architecture, Dependency Rules, Communication between ViewModel and Repository.
- **m** Singleton/Multiton - why is it considered bad?
- **m** Patterns: Facade, Abstract Factory, Immutable, Strategy, State, Builder, Composite.
- **s** Adapter/Bridge/Proxy patterns, and their differences.
- **m** Unidirectional Data Flow (UDF) in Android.
- **m** Dependency Injection patterns.
- **s** Observer pattern and its implementation in Android.

### Kotlin

- **m** Visibility Modifiers (difference in Java for `internal`).
- **m** Class `Any`.
- **m** Data classes, `copy()`, `componentN()` functions, and destructuring declarations.
- **s** Inline classes (value classes) and limitations; inline classes vs. type aliases; inline methods, reified types.
- **j** Objects and Companion objects.
- **m** Annotations (`@JvmField`, `@JvmStatic`, `@JvmOverloads`, etc.).
- **m** Implementing `hashCode()` and `equals()` methods.
- **m** Differences between `ArrayList`, `MutableList`, and `Array`.
- **m** Nested and inner classes, anonymous inner classes.
- **m** Enum classes and sealed classes.
- **m** Operator overloading.
- **s** Generics - `in`/`out` variance, difference between `super`/`extends` in Java, Type projections, Declaration-site variance, Generic functions, Generic constraints, Type erasure.
- **j** `open` class, `final` method, `override`.
- **j** What does `fun method(): Unit` do?
- **m** Secondary constructors.
- **j** The `when` keyword.
- **m** Lambda expressions and anonymous functions.
- **s** DSLs and the `@DslMarker` annotation.
- **m** Delegates - `by lazy`, `Delegates.notNull()`, etc.
- **s** `ReadOnlyProperty`, `ReadWriteProperty`, `provideDelegate` operator.
- **s** Reflection classes: `KProperty<*>`, `KClass<*>`, `KCallable<out R>`, `KFunction<out R>`.
- **s** Scope functions: `let`, `apply`, `also`, `run`.
- **m** Loop constructs: `forEach`, `until`, `..` (`rangeTo`), `downTo`, `step`, `ClosedRange<T>`.
- **m** Extension functions and properties.
- **m** Exceptions and differences between Java and Kotlin.
- **s** Reflection in Kotlin.
- **m** Coroutines Flow vs. RxJava: Differences and similarities.
- **m** Type aliases and their uses.
- **m** Sealed interfaces (introduced in Kotlin 1.5).
- **s** Context receivers (if applicable).
- **m** The `@OptIn` annotation and handling experimental features.

### Kotlin Coroutines

- **j** What are coroutines?
- **m** What is a suspending function?
- **m** What is `GlobalScope` and why is it discouraged?
- **m** Difference between `CoroutineScope` and `ViewModelScope`.
- **m** Dispatchers (`Main`, `IO`, `Default`).
- **m** Will the UI be blocked after starting a coroutine from the UI thread and suspending it?
- **s** How does uncaught exception propagation differ between `launch` and `async`?
- **m** How to handle exceptions in coroutines.
- **s** What is the `NonCancellable` context?
- **m** Difference between `withTimeout` and `withTimeoutOrNull`.
- **m** What are coroutine channels?
- **m** Difference between buffered and unbuffered channels.
- **m** Understanding structured concurrency and its benefits.
- **m** How coroutine cancellation works and how to handle it.
- **s** The use of `SupervisorJob` and its use cases.
- **s** Exception handling with `CoroutineExceptionHandler`.

### Kotlin Flow

- **m** What is Kotlin Flow?
- **s** Flow cancellation basics.
- **m** Flow builders.
- **m** Operators - Intermediate, Size-limiting, Terminal.
- **m** `flowOn` and how it changes the context.
- **m** Buffering in flows and when to use it.
- **m** Conflation and how it works.
- **m** Use of `collectLatest` and its benefits.
- **m** Flattening flows: `flatMapConcat`, `flatMapMerge`, `flatMapLatest`, etc.
- **m** Exception handling in flows, including transparent `catch`.
- **m** Understanding `SharedFlow` and `StateFlow`, their differences, and use cases.
- **m** Difference between hot and cold flows.
- **m** Combining flows using operators like `combine` and `zip`.
- **s** How backpressure is handled in Flows compared to RxJava.
