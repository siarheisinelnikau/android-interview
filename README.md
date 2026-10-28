## Questions for Interview
**Position - Android Developer (j - junior, m - middle, s - senior).**

Select questions based on the role and the project's stack. RxJava, Koin, and Kotlin Multiplatform sections are optional.

---

### OOP

- **j** What is OOP? (in English, since our native language is Russian)
- **j** Explain SOLID principles with examples.
- **m** Composition vs. inheritance - when would you choose each?
- **m** Class naming - when do names like "Helper" and "Manager" hide unclear responsibilities?
- **m** How does Garbage Collection work? Can unreachable objects with circular references be collected?

### Algorithms

- **j** What is Big O notation? Compare searching in a list and looking up a key in a hash map.
- **m** How would you remove duplicates from a large list while preserving order? Discuss time and memory complexity.
- **s** Worst-case vs. amortized complexity - how does this apply to a growing array or a hash table?

### Collections

- **j** Differences between `List`, `Set`, and `Map`.
- **m** Compare `ArrayList` and `LinkedList`. How do access patterns and memory overhead affect the choice?
- **m** How does `HashMap` work? What happens with collisions or mutable keys?
- **m** Compare `HashMap`, `LinkedHashMap`, and `TreeMap`. When does iteration order matter?
- **m** Eager collection operations vs. `Sequence` - when does lazy evaluation help, and when can it add overhead?

### Multithreading/Concurrency

- **m** Concurrency vs. parallelism. Why must UI work stay on the main thread?
- **m** What are race conditions and deadlocks? How would you reproduce and investigate them?
- **s** Explain the Java Memory Model and the happens-before relationship. What guarantees do locks and `volatile` provide?
- **m** Why does `volatile` not make `counter++` atomic? When would you use atomic classes and `compareAndSet`?
- **m** Compare `synchronized` and coroutine `Mutex`. What happens to the waiting thread or coroutine?
- **m** When would you use an `ExecutorService`? How do pool size and queue capacity affect resource usage?
- **s** Thread confinement, immutable data, locks, and concurrent collections - how would you choose a strategy for shared state?

### RxJava (Optional)

- **m** Differences between `Observable`, `Single`, `Maybe`, and `Completable`.
- **s** What is `Flowable`, and how does backpressure work?
- **m** Compare `map`, `flatMap`, `concatMap`, and `switchMap` using a search screen as an example.
- **m** Difference between `subscribeOn` and `observeOn`. How do you manage subscriptions across Android lifecycles?
- **s** How would you migrate an RxJava chain to Coroutines and Flow while preserving cancellation, error handling, and scheduling behavior?

### Database (DB)

- **j** SQL basics: `SELECT`, `WHERE`, `ORDER BY`, and `JOIN`.
- **m** Difference between `WHERE` and `HAVING`. How do `GROUP BY` and aggregate functions work?
- **m** How do indexes speed up reads? What are the costs for writes and storage?
- **m** Explain transactions, foreign keys, and conflict handling in SQLite.
- **s** How would you investigate a slow SQLite query? Discuss `EXPLAIN QUERY PLAN`, indexes, and pagination.

### Room and DataStore

- **j** What does Room provide over working directly with SQLite?
- **m** How do you model one-to-many and many-to-many relationships in Room? When is `@Transaction` needed?
- **m** Compare a DAO `suspend` function with a DAO returning `Flow`. What causes an observable query to run again?
- **m** Automatic vs. manual migrations. Why export schemas, and how do you test migration paths without losing user data?
- **m** When would you choose Preferences DataStore, typed DataStore, or Room? How would you migrate from `SharedPreferences`?
- **s** How would you combine Room, Paging 3, and `RemoteMediator` for a list backed by a local database and a remote API?

### Android Core

- **j** Core components: `Activity`, `Service`, `BroadcastReceiver`, and `ContentProvider`. What is the role of `Application`?
- **j** Explain the Activity lifecycle. How does it differ from the lifecycle of a Fragment's view?
- **m** Configuration change vs. process death - what happens to an Activity and its `ViewModel`?
- **m** Compare `ViewModel`, `SavedStateHandle`, saved instance state, and persistent storage. What belongs in each?
- **m** What are `Context` types? How can holding an Activity context cause a memory leak?
- **m** How do `Looper`, `Handler`, and the main message queue work?
- **m** Why use `repeatOnLifecycle` or `collectAsStateWithLifecycle` to collect flows from the UI?
- **j** Explicit vs. implicit intents. What is the Activity Result API used for?
- **m** Runtime permissions - how do you handle denial, one-time grants, and permission revocation?
- **m** Photo Picker vs. Storage Access Framework - when would you use each? How do scoped storage and URI permissions affect file sharing?
- **m** Difference between `minSdk`, `targetSdk`, and `compileSdk`. How do you prepare an app for a target SDK upgrade?
- **s** How do you distinguish Android behavior changes affecting all apps from changes gated by `targetSdk`? How would you test both?

### Background Work

- **m** When would you choose a coroutine, WorkManager, a foreground service, or `AlarmManager`?
- **m** WorkManager constraints, unique work, retries, and backoff - how would you implement reliable synchronization?
- **m** Why is WorkManager unsuitable for exact-time alarms? What restrictions apply to exact alarms?
- **m** Foreground service types, permissions, and background start restrictions - what must you account for?
- **s** How do Doze, App Standby, job quotas, and process death affect background work? How would you make work safe to retry?

### Android UI (Views)

- **j** Explain `dp`, `sp`, and resource qualifiers. How do font scaling and localization affect layouts?
- **m** What are the measure, layout, and draw phases of a View? When would you use `requestLayout()` vs. `invalidate()`?
- **m** How do `RecyclerView`, `ListAdapter`, and `DiffUtil` work together? What causes incorrect item updates or scroll jank?
- **m** View Binding vs. Data Binding. How do you manage a Fragment's binding across its view lifecycle?
- **m** How would you migrate a View-based screen to Compose incrementally using `ComposeView` and `AndroidView`?
- **s** How would you investigate touch dispatch or nested scrolling problems in a custom View hierarchy?

### Jetpack Compose

- **j** What is a composable function? How does declarative UI differ from updating Views directly?
- **j** What is recomposition, and what can trigger it?
- **j** Compare `remember` and `rememberSaveable`. What happens after recreation or process death?
- **m** State hoisting and unidirectional data flow - where should screen state and reusable component state live?
- **m** Why can mutating a regular list inside `mutableStateOf` fail to update the UI? Compare immutable updates and snapshot state collections.
- **m** Why does modifier order matter? Compare padding before and after `clickable` or `background`.
- **m** Compare `LaunchedEffect`, `DisposableEffect`, and `rememberCoroutineScope`. How do effect keys control cancellation and restarts?
- **m** When would you use `rememberUpdatedState` to avoid a stale value in a long-running effect?
- **m** Compare `derivedStateOf` and `snapshotFlow`. What problem does each solve?
- **m** How do item keys and `contentType` affect state and reuse in `LazyColumn` or `LazyVerticalGrid`?
- **s** Explain stability, skipping, and strong skipping. Why is an unstable parameter not enough to conclude that a composable cannot be skipped?
- **s** Composition, layout, and drawing - how would you locate expensive work and defer state reads to the appropriate phase?
- **m** Edge-to-edge layouts and `WindowInsets` - how do you handle system bars, display cutouts, and the keyboard?
- **m** How would you adapt a screen to resizable windows, tablets, and foldables using window size classes and adaptive layouts?
- **m** How do semantics, touch targets, focus order, and content descriptions affect accessibility?

### Navigation

- **j** What is a back stack? How do Back and Up navigation differ?
- **m** How would you model type-safe destinations and pass identifiers instead of large objects between screens?
- **m** How do you scope a `ViewModel` to a destination or navigation graph and restore navigation state?
- **m** Deep links vs. verified App Links. How would you handle a link that requires authentication?
- **s** How does Navigation 3's app-owned back stack differ from the `NavController` approach? How would you support predictive back and multiple panes?

### Dagger and Hilt

- **j** What problem does Dependency Injection solve? Compare constructor injection with a Service Locator.
- **m** Compare constructor injection, `@Binds`, and `@Provides`. When do you need a qualifier?
- **m** What do Dagger components and subcomponents represent? How does Hilt organize them for Android?
- **m** Explain Hilt component lifetimes and scopes. How do `@Singleton`, `@ActivityRetainedScoped`, and `@ViewModelScoped` differ?
- **m** How do `@HiltViewModel`, `@AndroidEntryPoint`, and `@InstallIn` work together?
- **s** When do you need `@EntryPoint` or assisted injection? How would you avoid retaining a short-lived dependency in a longer-lived scope?

### Koin (Optional)

- **m** How do you define modules and choose between `single`, `factory`, and `scoped` definitions?
- **m** How do Koin scopes relate to Activity, Fragment, and `ViewModel` lifecycles?
- **s** Compare Koin and Dagger/Hilt in terms of dependency validation, startup cost, tooling, and maintenance for your project.
- **m** How would you verify module configuration and replace dependencies in tests?

### Patterns and Architecture

- **m** Compare MVP, MVVM, and MVI. How would you choose an approach for a screen?
- **m** Explain Unidirectional Data Flow (UDF). How do UI state and user actions move through the app?
- **m** What responsibilities belong to a `ViewModel`, repository, and data source? When does a use case add value?
- **s** Clean Architecture and the dependency rule - where would you draw module boundaries, and what complexity would you avoid in a small app?
- **m** How would you represent loading, content, empty, and error states without allowing invalid combinations?
- **s** How would you handle navigation and snackbar actions across lifecycle changes? Discuss state, delivery guarantees, and the risks of one-off event streams.
- **m** Give practical uses of Strategy, Factory, Adapter, and Decorator. What tradeoffs come with global singletons?
- **s** How would you design an offline-first feature with a single source of truth, optimistic updates, and conflict resolution?

### Kotlin

- **j** `val` vs. `var`. Why does `val` not guarantee that an object is immutable?
- **j** Nullable types, safe calls, Elvis operator, and `!!` - how do you work safely with missing values?
- **m** What are platform types in Java interop? When is a smart cast unavailable?
- **j** Compare `==` and `===`. How are `equals()` and `hashCode()` related?
- **m** What do data classes generate? Why is `copy()` a shallow copy, and which properties participate in equality?
- **j** Objects, companion objects, and top-level declarations - when would you use each?
- **m** Compare enums, sealed classes, and sealed interfaces. How does an exhaustive `when` help model state?
- **m** Visibility modifiers - what does `internal` mean, and how does it differ from Java package visibility?
- **m** Read-only vs. mutable collections. Why is `List<T>` not a guarantee of immutability?
- **m** Extension functions and properties - how are they resolved, and can they override members?
- **m** Compare `let`, `run`, `with`, `apply`, and `also`. What are the risks of nesting scope functions?
- **m** Compare `lateinit` and delegated properties such as `by lazy`. What thread-safety options does `lazy` provide?
- **m** Higher-order functions, lambdas, and function types with receivers - how do they support a DSL?
- **s** Explain `inline`, `noinline`, `crossinline`, and reified type parameters. What limitations remain because of type erasure?
- **s** Generics - declaration-site variance (`in`/`out`), type projections, and star projections. How do they relate to Java wildcards?
- **m** Value classes vs. data classes and type aliases. When can a value class be boxed?
- **m** Compare `Unit`, `Nothing`, and nullable return types. When is each useful?
- **m** Exceptions and `Result` - how would you model expected failures without accidentally swallowing coroutine cancellation?
- **s** What do context parameters solve compared with extension receivers and explicit parameters? How do they differ from the older context receivers feature?
- **m** What does `@OptIn` mean? How would you evaluate the stability and compatibility of a Kotlin API before adopting it?

### Kotlin Coroutines

- **j** What are coroutines, and how do they differ from threads?
- **j** What does `suspend` mean? Does a suspending function automatically run on a background thread?
- **m** Structured concurrency - how do a `CoroutineScope`, its `Job`, and child coroutines relate?
- **m** Compare `viewModelScope`, `lifecycleScope`, and an application-owned scope. Why is `GlobalScope` usually discouraged?
- **m** Compare `launch`, `async`, and `withContext`. When is concurrency actually introduced?
- **m** Dispatchers (`Main`, `Main.immediate`, `IO`, `Default`) - how would you make a blocking operation safe to call from the main thread?
- **m** How does cooperative cancellation work? What do `isActive`, `ensureActive`, and `yield` do in CPU-intensive code?
- **s** Compare `Job` and `SupervisorJob`, and `coroutineScope` and `supervisorScope`. How does a failing child affect siblings and the parent?
- **s** How does exception propagation differ between `launch` and `async`? When can `CoroutineExceptionHandler` handle an exception?
- **m** Why should `CancellationException` usually be rethrown? How can `runCatching` or a broad `catch` break cancellation?
- **m** Compare `withTimeout` and `withTimeoutOrNull`. How would you release resources on cancellation?
- **s** When is `NonCancellable` appropriate for cleanup, and what are the risks of using it for regular work?
- **m** Channels vs. shared flows - how do buffering, suspension, and multiple consumers affect delivery?

### Kotlin Flow

- **j** What is a cold Flow? What happens when it is collected twice?
- **m** Compare `flow`, `channelFlow`, and `callbackFlow`. Why is `awaitClose` important when adapting callbacks?
- **m** Intermediate vs. terminal operators. When does a Flow start doing work?
- **m** How does `flowOn` affect upstream execution? Why is emitting from another context inside `flow` problematic?
- **m** Compare `buffer`, `conflate`, and `collectLatest`. Which values or work can be skipped or cancelled?
- **m** Compare `flatMapConcat`, `flatMapMerge`, and `flatMapLatest`.
- **m** How would you implement search with `debounce`, `distinctUntilChanged`, and `flatMapLatest`?
- **m** Compare `combine` and `zip`. How do they behave when sources emit at different rates?
- **m** How do `catch`, `retry`, and `onCompletion` interact with upstream errors, downstream errors, and cancellation?
- **m** Compare `StateFlow` and `SharedFlow`: current value, replay, equality-based conflation, and slow collectors.
- **m** What do `stateIn`, `shareIn`, and `SharingStarted.WhileSubscribed` do? Who owns the upstream coroutine?
- **s** Why can a `SharedFlow` event be missed while the UI is stopped? What delivery guarantees would you design for a critical action?

### Networking

- **j** HTTP methods, status codes, and headers - what should the client do differently for transport errors and unsuccessful HTTP responses?
- **m** How do Retrofit suspend APIs, OkHttp, and serialization work together? How do cancellation and timeouts propagate?
- **m** Application vs. network interceptors in OkHttp. Where would you add headers, logging, or caching behavior?
- **s** How would you refresh an expired token when several requests fail at once, without refresh loops or duplicate refresh requests?
- **m** Retries, exponential backoff, and idempotency - when can retrying a request create duplicate data?
- **m** HTTP caching vs. a local database cache. How do you handle stale data, pagination, and offline errors?

### Testing

- **j** Unit tests vs. instrumented tests. What belongs in each for an Android app?
- **m** Fakes, mocks, and stubs - how would you choose dependencies for a `ViewModel` or repository test?
- **m** How do `runTest`, test dispatchers, and a shared `TestCoroutineScheduler` make coroutine tests deterministic?
- **m** How would you test Flow emissions, `StateFlow` conflation, cancellation, and a `stateIn` flow using `WhileSubscribed`?
- **m** How would you test Compose UI using semantics, user actions, and assertions? When do merged and unmerged semantics trees matter?
- **m** How would you test a screen's restoration after recreation and after process death? What does `ActivityScenario.recreate()` actually cover?
- **m** How would you use a controlled HTTP server to test timeouts, error responses, and token refresh?
- **s** How would you investigate flaky asynchronous UI tests and choose a useful balance of unit, integration, and end-to-end coverage?

### Performance and Debugging

- **m** What causes an ANR? How would you use traces, StrictMode, and production reports to find the cause?
- **m** How would you investigate a memory leak, excessive allocations, or an out-of-memory crash using a heap dump?
- **m** How do ART, JIT, AOT, and Baseline Profiles relate to startup and runtime performance?
- **s** How would you measure cold startup and scrolling performance with Macrobenchmark and Perfetto? Why use a release-like build?
- **s** How would you diagnose Compose jank using tracing, Layout Inspector, and compiler reports before changing stability annotations?
- **s** How would you verify that an optimization improves user-visible performance across device classes and does not regress battery usage?

### Build and Delivery

- **j** APK vs. Android App Bundle. What does app signing protect?
- **m** Build types, product flavors, and source sets - how would you configure separate app variants?
- **m** Gradle Kotlin DSL, version catalogs, and convention plugins - what problem does each solve?
- **m** Compare KSP and kapt. How would you check processor compatibility when upgrading Kotlin and the Android Gradle Plugin?
- **m** What do R8 shrinking, optimization, and obfuscation do? How do keep rules and mapping files help diagnose release-only failures?
- **s** How would you improve build speed using measurements, module boundaries, incremental processing, and Gradle caches?
- **s** How would you check 16 KB page-size compatibility when an app or a third-party SDK includes native libraries?

### Security and Privacy

- **m** Why can secrets embedded in an APK be extracted? What belongs on a backend instead of in the app?
- **m** How would you protect stored authentication tokens? What does Android Keystore provide, and how do backups and logs affect data exposure?
- **m** Exported components, mutable `PendingIntent`s, and untrusted deep-link input - what risks do they introduce?
- **m** How would you use Credential Manager for passwords, passkeys, and federated sign-in? Where should authentication be verified?
- **s** How would you audit third-party SDK permissions, data collection, and local network access when preparing a platform upgrade?

### Kotlin Multiplatform (Optional)

- **m** What can be shared with Kotlin Multiplatform? How does sharing business logic differ from sharing UI with Compose Multiplatform?
- **m** Explain common and platform source sets. When would you use `expect`/`actual` declarations vs. interfaces with injected implementations?
- **s** How would you evaluate library support, platform interop, testing, and build complexity before moving an Android feature into shared code?
