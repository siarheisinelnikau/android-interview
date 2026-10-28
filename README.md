## Questions for Interview
**Position - Android Developer (j - junior, m - middle, s - senior).**

Select questions based on the role and the project's stack. RxJava, Koin, and Kotlin Multiplatform sections are optional.

Review dates for version-specific questions are recorded in their answers. Check the device OS, target SDK, library version, and API stability when discussing a feature.

Each question links to a self-contained answer in [answers/](answers/README.md), with examples and primary-source references.

All 270 answers were reviewed on **2026-10-29**. See [version notes](docs/version-notes.md) for the Kotlin, Android, AGP, and Compose baseline. Illustrated answers include local SVG diagrams that display directly on GitHub.

---

### OOP

- **j** [What is OOP? (in English, since our native language is Russian)](answers/oop/oop-principles.md)
- **j** [Explain SOLID principles with examples.](answers/oop/solid-principles.md)
- **m** [Composition vs. inheritance - when would you choose each?](answers/oop/composition-vs-inheritance.md)
- **m** [Class naming - when do names like "Helper" and "Manager" hide unclear responsibilities?](answers/oop/class-naming.md)
- **m** [How does Garbage Collection work? Can unreachable objects with circular references be collected?](answers/oop/garbage-collection.md)

### Algorithms

- **j** [What is Big O notation? Compare searching in a list and looking up a key in a hash map.](answers/algorithms/big-o-and-lookup.md)
- **m** [How would you remove duplicates from a large list while preserving order? Discuss time and memory complexity.](answers/algorithms/ordered-deduplication.md)
- **s** [Worst-case vs. amortized complexity - how does this apply to a growing array or a hash table?](answers/algorithms/amortized-complexity.md)

### Collections

- **j** [Differences between `List`, `Set`, and `Map`.](answers/collections/list-set-map.md)
- **m** [Compare `ArrayList` and `LinkedList`. How do access patterns and memory overhead affect the choice?](answers/collections/arraylist-vs-linkedlist.md)
- **m** [How does `HashMap` work? What happens with collisions or mutable keys?](answers/collections/hashmap-and-mutable-keys.md)
- **m** [Compare `HashMap`, `LinkedHashMap`, and `TreeMap`. When does iteration order matter?](answers/collections/map-ordering.md)
- **m** [Eager collection operations vs. `Sequence` - when does lazy evaluation help, and when can it add overhead?](answers/collections/sequences-vs-collections.md)

### Multithreading/Concurrency

- **m** [Concurrency vs. parallelism. Why must UI work stay on the main thread?](answers/multithreading-concurrency/concurrency-vs-parallelism.md)
- **m** [What are race conditions and deadlocks? How would you reproduce and investigate them?](answers/multithreading-concurrency/races-and-deadlocks.md)
- **s** [Explain the Java Memory Model and the happens-before relationship. What guarantees do locks and `volatile` provide?](answers/multithreading-concurrency/memory-model.md)
- **m** [Why does `volatile` not make `counter++` atomic? When would you use atomic classes and `compareAndSet`?](answers/multithreading-concurrency/volatile-and-atomics.md)
- **m** [Compare `synchronized` and coroutine `Mutex`. What happens to the waiting thread or coroutine?](answers/multithreading-concurrency/synchronized-vs-mutex.md)
- **m** [When would you use an `ExecutorService`? How do pool size and queue capacity affect resource usage?](answers/multithreading-concurrency/executor-sizing.md)
- **s** [Thread confinement, immutable data, locks, and concurrent collections - how would you choose a strategy for shared state?](answers/multithreading-concurrency/shared-state-strategies.md)

### RxJava (Optional)

- **m** [Differences between `Observable`, `Single`, `Maybe`, and `Completable`.](answers/rxjava-optional/reactive-types.md)
- **s** [What is `Flowable`, and how does backpressure work?](answers/rxjava-optional/flowable-backpressure.md)
- **m** [Compare `map`, `flatMap`, `concatMap`, and `switchMap` using a search screen as an example.](answers/rxjava-optional/mapping-operators.md)
- **m** [Difference between `subscribeOn` and `observeOn`. How do you manage subscriptions across Android lifecycles?](answers/rxjava-optional/rx-schedulers-and-disposal.md)
- **s** [How would you migrate an RxJava chain to Coroutines and Flow while preserving cancellation, error handling, and scheduling behavior?](answers/rxjava-optional/rx-to-flow-migration.md)

### Database (DB)

- **j** [SQL basics: `SELECT`, `WHERE`, `ORDER BY`, and `JOIN`.](answers/database-db/select-where-join.md)
- **m** [Difference between `WHERE` and `HAVING`. How do `GROUP BY` and aggregate functions work?](answers/database-db/group-by-and-having.md)
- **m** [How do indexes speed up reads? What are the costs for writes and storage?](answers/database-db/database-indexes.md)
- **m** [Explain transactions, foreign keys, and conflict handling in SQLite.](answers/database-db/transactions-and-conflicts.md)
- **s** [How would you investigate a slow SQLite query? Discuss `EXPLAIN QUERY PLAN`, indexes, and pagination.](answers/database-db/slow-query-investigation.md)

### Room and DataStore

- **j** [What does Room provide over working directly with SQLite?](answers/room-and-datastore/room-benefits.md)
- **m** [How do you model one-to-many and many-to-many relationships in Room? When is `@Transaction` needed?](answers/room-and-datastore/room-relationships.md)
- **m** [Compare a DAO `suspend` function with a DAO returning `Flow`. What causes an observable query to run again?](answers/room-and-datastore/room-suspend-and-flow.md)
- **m** [Automatic vs. manual migrations. Why export schemas, and how do you test migration paths without losing user data?](answers/room-and-datastore/room-migrations.md)
- **m** [When would you choose Preferences DataStore, typed DataStore, or Room? How would you migrate from `SharedPreferences`?](answers/room-and-datastore/datastore-vs-room.md)
- **s** [How would you combine Room, Paging 3, and `RemoteMediator` for a list backed by a local database and a remote API?](answers/room-and-datastore/room-paging-remote-mediator.md)

### Android Core

- **j** [Core components: `Activity`, `Service`, `BroadcastReceiver`, and `ContentProvider`. What is the role of `Application`?](answers/android-core/application-components.md)
- **j** [Explain the Activity lifecycle. How does it differ from the lifecycle of a Fragment's view?](answers/android-core/activity-and-fragment-lifecycles.md)
- **m** [Configuration change vs. process death - what happens to an Activity and its `ViewModel`?](answers/android-core/configuration-change-vs-process-death.md)
- **m** [Compare `ViewModel`, `SavedStateHandle`, saved instance state, and persistent storage. What belongs in each?](answers/android-core/state-storage-choices.md)
- **m** [What are `Context` types? How can holding an Activity context cause a memory leak?](answers/android-core/context-lifetimes.md)
- **m** [How do `Looper`, `Handler`, and the main message queue work?](answers/android-core/looper-handler-message-queue.md)
- **m** [Why use `repeatOnLifecycle` or `collectAsStateWithLifecycle` to collect flows from the UI?](answers/android-core/lifecycle-aware-flow-collection.md)
- **j** [Explicit vs. implicit intents. What is the Activity Result API used for?](answers/android-core/intents-and-activity-results.md)
- **m** [Runtime permissions - how do you handle denial, one-time grants, and permission revocation?](answers/android-core/runtime-permission-flow.md)
- **m** [Photo Picker vs. Storage Access Framework - when would you use each? How do scoped storage and URI permissions affect file sharing?](answers/android-core/file-selection-and-uri-permissions.md)
- **m** [Difference between `minSdk`, `targetSdk`, and `compileSdk`. How do you prepare an app for a target SDK upgrade?](answers/android-core/sdk-versions-and-upgrades.md)
- **s** [How do you distinguish Android behavior changes affecting all apps from changes gated by `targetSdk`? How would you test both?](answers/android-core/os-changes-vs-target-changes.md)
- **j** [Does a `Service` run on a separate thread or in a separate process by default? How would you move blocking work off its main thread?](answers/android-core/service-threading.md)
- **m** [How do a Fragment's lifecycle and its view lifecycle affect observers, coroutines, and references to Views?](answers/android-core/fragment-view-ownership.md)
- **m** [Tasks, launch modes, and intent flags - how would you prevent duplicate screens when opening a notification or deep link?](answers/android-core/tasks-launch-modes-and-deep-links.md)
- **m** [What does Binder do? Compare `Parcelable` and `Serializable`, and explain how oversized transactions can fail.](answers/android-core/binder-and-transaction-size.md)
- **m** [How do notification channels and `PendingIntent`s work? How would you open the correct screen with a valid back stack?](answers/android-core/notifications-and-pending-intents.md)
- **s** [Force-stop vs. removing an app from Recents vs. system-initiated process death - how do they affect state and scheduled work?](answers/android-core/force-stop-recents-process-death.md)

### Android Versions

#### [Android 13 (API 33)](https://developer.android.com/about/versions/13/behavior-changes-13)

- **m** [How does the `POST_NOTIFICATIONS` permission affect ordinary notifications and foreground service notifications? Can a foreground service start if the permission is denied?](answers/android-versions/android-13-notification-permission.md)
- **m** [How do granular media permissions replace `READ_EXTERNAL_STORAGE` for apps targeting API 33? When can the Photo Picker avoid requesting broad media access?](answers/android-versions/android-13-media-permissions.md)

#### [Android 14 (API 34)](https://developer.android.com/about/versions/14/behavior-changes-14)

- **m** [What foreground service types and type-specific permissions must an app declare when targeting API 34? How do while-in-use permissions affect background starts?](answers/android-versions/android-14-foreground-service-types.md)
- **m** [How would you handle selected-photos access and changes to the user's selected media when targeting API 34?](answers/android-versions/android-14-selected-photos.md)
- **m** [When must a context-registered receiver specify `RECEIVER_EXPORTED` or `RECEIVER_NOT_EXPORTED`? What is the exception for system broadcasts?](answers/android-versions/android-14-receiver-export-flags.md)

#### [Android 15 (API 35)](https://developer.android.com/about/versions/15/behavior-changes-15)

- **m** [What changes for non-floating windows when an app targets API 35 on Android 15? How would you find inset and edge-to-edge regressions?](answers/android-versions/android-15-edge-to-edge.md)
- **s** [How do time limits for `dataSync` and `mediaProcessing` foreground services work for apps targeting API 35? How should a service handle `onTimeout()`?](answers/android-versions/android-15-service-timeouts.md)
- **m** [What restrictions apply to starting foreground services from `BOOT_COMPLETED` when targeting API 35? How would you redesign affected work?](answers/android-versions/android-15-boot-completed-services.md)

#### [Android 16 (API 36)](https://developer.android.com/about/versions/16/behavior-changes-16)

- **m** [What happens to the edge-to-edge opt-out when an app targets API 36 and runs on Android 16? How does running that app on Android 15 differ?](answers/android-versions/android-16-edge-to-edge-opt-out.md)
- **m** [How does targeting API 36 on Android 16 affect legacy `onBackPressed()` and `KEYCODE_BACK` handling? Which supported APIs would you use instead?](answers/android-versions/android-16-predictive-back.md)
- **m** [How do orientation, resizability, and aspect-ratio restrictions change on large screens when targeting API 36? What should you test in a portrait-only app?](answers/android-versions/android-16-large-screen-layouts.md)
- **s** [How do Android 16's job quota changes affect WorkManager even without a target SDK upgrade? How would you diagnose stopped work?](answers/android-versions/android-16-job-quotas.md)

#### [Android 17 (API 37)](https://developer.android.com/about/versions/17/behavior-changes-17)

- **m** [When targeting API 37, why can local network access require more than the `INTERNET` permission? When can a system device picker replace broad network access?](answers/android-versions/android-17-local-network-permission.md)
- **m** [What happens to the large-screen orientation and resizability opt-out when targeting API 37? How would you verify adaptive behavior?](answers/android-versions/android-17-large-screen-opt-out.md)
- **s** [How does the lock-free `MessageQueue` implementation for apps targeting API 37 affect code or SDKs that inspect private queue internals?](answers/android-versions/android-17-lock-free-message-queue.md)
- **s** [How would you investigate Android 17's app memory limits using `ApplicationExitInfo` and heap dumps? Do these limits depend on `targetSdk`?](answers/android-versions/android-17-app-memory-limits.md)
- **m** [What changes for certificate transparency when targeting API 37? How would you investigate a TLS failure without bypassing certificate checks?](answers/android-versions/android-17-certificate-transparency.md)

### Background Work

- **m** [When would you choose a coroutine, WorkManager, a foreground service, or `AlarmManager`?](answers/background-work/choosing-background-api.md)
- **m** [WorkManager constraints, unique work, retries, and backoff - how would you implement reliable synchronization?](answers/background-work/reliable-workmanager-sync.md)
- **m** [Why is WorkManager unsuitable for exact-time alarms? What restrictions apply to exact alarms?](answers/background-work/exact-alarms-vs-workmanager.md)
- **m** [Foreground service types, permissions, and background start restrictions - what must you account for?](answers/background-work/foreground-service-rules.md)
- **s** [How do Doze, App Standby, job quotas, and process death affect background work? How would you make work safe to retry?](answers/background-work/doze-quotas-and-retries.md)

### Android UI (Views)

- **j** [Explain `dp`, `sp`, and resource qualifiers. How do font scaling and localization affect layouts?](answers/android-ui-views/density-fonts-and-resources.md)
- **m** [What are the measure, layout, and draw phases of a View? When would you use `requestLayout()` vs. `invalidate()`?](answers/android-ui-views/view-layout-and-drawing.md)
- **m** [How do `RecyclerView`, `ListAdapter`, and `DiffUtil` work together? What causes incorrect item updates or scroll jank?](answers/android-ui-views/recyclerview-diffing.md)
- **m** [View Binding vs. Data Binding. How do you manage a Fragment's binding across its view lifecycle?](answers/android-ui-views/view-binding-vs-data-binding.md)
- **m** [How would you migrate a View-based screen to Compose incrementally using `ComposeView` and `AndroidView`?](answers/android-ui-views/incremental-compose-migration.md)
- **s** [How would you investigate touch dispatch or nested scrolling problems in a custom View hierarchy?](answers/android-ui-views/touch-and-nested-scrolling.md)

### Jetpack Compose

- **j** [What is a composable function? How does declarative UI differ from updating Views directly?](answers/jetpack-compose/composable-functions.md)
- **j** [Compare `Row`, `Column`, and `Box`. How do alignment, arrangement, and `weight` affect a layout?](answers/jetpack-compose/row-column-box.md)
- **j** [What is recomposition, and what can trigger it?](answers/jetpack-compose/recomposition-triggers.md)
- **j** [Compare `remember` and `rememberSaveable`. What happens after recreation or process death?](answers/jetpack-compose/remember-vs-remembersaveable.md)
- **m** [How do call-site identity and `key` affect remembered state when composables are reordered or conditionally included?](answers/jetpack-compose/composition-identity-and-keys.md)
- **m** [When do you need a custom `Saver`? Why should saved state contain small restoration inputs instead of an entire screen's data?](answers/jetpack-compose/custom-saver.md)
- **m** [State hoisting and unidirectional data flow - where should screen state and reusable component state live?](answers/jetpack-compose/state-hoisting-and-udf.md)
- **m** [Compare `compositionLocalOf` and `staticCompositionLocalOf`. When are explicit parameters preferable to a `CompositionLocal`?](answers/jetpack-compose/composition-local.md)
- **m** [Why can mutating a regular list inside `mutableStateOf` fail to update the UI? Compare immutable updates and snapshot state collections.](answers/jetpack-compose/observable-collection-updates.md)
- **s** [What do snapshot mutation policies control? How do structural equality, referential equality, and `neverEqualPolicy` affect invalidation?](answers/jetpack-compose/snapshot-mutation-policies.md)
- **m** [Why does modifier order matter? Compare padding before and after `clickable` or `background`.](answers/jetpack-compose/modifier-order.md)
- **m** [Compare `LaunchedEffect`, `DisposableEffect`, and `rememberCoroutineScope`. How do effect keys control cancellation and restarts?](answers/jetpack-compose/effect-ownership-and-keys.md)
- **m** [What does `produceState` provide? How would you adapt an external data source and clean it up when the producer leaves composition?](answers/jetpack-compose/produce-state.md)
- **m** [When would you use `rememberUpdatedState` to avoid a stale value in a long-running effect?](answers/jetpack-compose/remember-updated-state.md)
- **m** [Compare `derivedStateOf` and `snapshotFlow`. What problem does each solve?](answers/jetpack-compose/derived-state-vs-snapshot-flow.md)
- **m** [How do item keys and `contentType` affect state and reuse in `LazyColumn` or `LazyVerticalGrid`?](answers/jetpack-compose/lazy-list-keys-and-content-types.md)
- **m** [What contracts do `@Stable` and `@Immutable` declare? Why can incorrect annotations lead to stale UI?](answers/jetpack-compose/stable-immutable-contracts.md)
- **s** [Explain stability, skipping, and strong skipping. Why is an unstable parameter not enough to conclude that a composable cannot be skipped?](answers/jetpack-compose/strong-skipping.md)
- **s** [Composition, layout, and drawing - how would you locate expensive work and defer state reads to the appropriate phase?](answers/jetpack-compose/compose-phases-and-deferred-reads.md)
- **s** [How do constraints flow through a custom `Layout`? Why is measuring a child repeatedly in one layout pass unsupported, and when are intrinsic measurements useful?](answers/jetpack-compose/custom-layout-constraints.md)
- **m** [Why can nesting a `LazyColumn` inside another vertically scrolling container fail with unbounded constraints? How would you structure the content?](answers/jetpack-compose/nested-scrolling-constraints.md)
- **m** [Compare state-based text fields using `TextFieldState` with the `value`/`onValueChange` approach. How do `InputTransformation` and `OutputTransformation` differ?](answers/jetpack-compose/state-based-text-fields.md)
- **m** [Compare `animate*AsState`, `Animatable`, and `updateTransition`. How would you coordinate animations and handle interrupted gestures?](answers/jetpack-compose/animation-api-choice.md)
- **m** [Edge-to-edge layouts and `WindowInsets` - how do you handle system bars, display cutouts, and the keyboard?](answers/jetpack-compose/compose-window-insets.md)
- **m** [How would you adapt a screen to resizable windows, tablets, and foldables using window size classes and adaptive layouts?](answers/jetpack-compose/adaptive-compose-layouts.md)
- **m** [How do semantics, touch targets, focus order, and content descriptions affect accessibility?](answers/jetpack-compose/compose-accessibility.md)
- **m** [How would you use previews and preview parameters to check dark mode, large fonts, locales, and different screen sizes? What still needs a device test?](answers/jetpack-compose/compose-previews.md)

### Jetpack Compose Versions

Use the [Compose Runtime release notes](https://developer.android.com/jetpack/androidx/releases/compose-runtime) to check the version and stability of each API.

- **m** [How does the Compose BOM align Runtime, UI, and Material 3 artifacts with different version numbers? Why is the compiler plugin configured separately?](answers/jetpack-compose-versions/compose-bom-and-compiler.md)
- **m** [Runtime 1.9 - what do `@RememberInComposition` and `@FrequentlyChangingValue` help lint detect? Why move stability annotations into `runtime-annotation`?](answers/jetpack-compose-versions/runtime-19-lint-annotations.md)
- **m** [Runtime 1.10 - compare `retain`, `remember`, `rememberSaveable`, and `ViewModel`. Which lifetimes and restoration guarantees differ?](answers/jetpack-compose-versions/runtime-110-retain-lifetimes.md)
- **s** [Runtime 1.10 - why can retaining an Activity, View, or a key referencing them leak resources? What does `@DoNotRetain` communicate?](answers/jetpack-compose-versions/runtime-110-retention-leaks.md)
- **s** [Runtime 1.11 - what does the experimental `SlotTable` rewrite aim to improve? How would you benchmark an opt-in runtime change?](answers/jetpack-compose-versions/runtime-111-slot-table.md)
- **s** [Runtime 1.11 - what does experimental `SnapshotFlowManager` change when observing many `snapshotFlow` instances?](answers/jetpack-compose-versions/runtime-111-snapshot-flow-manager.md)
- **m** [Runtime 1.12 - when would keyed `SideEffect` replace a `LaunchedEffect` that performs no suspending work?](answers/jetpack-compose-versions/runtime-112-keyed-side-effect.md)
- **s** [How would you assess a move from Runtime 1.12 to a 1.13 beta? Does a stable library release guarantee every API is stable?](answers/jetpack-compose-versions/runtime-beta-upgrade-assessment.md)

### Navigation

- **j** [What is a back stack? How do Back and Up navigation differ?](answers/navigation/back-stack-back-and-up.md)
- **m** [How would you model type-safe destinations and pass identifiers instead of large objects between screens?](answers/navigation/type-safe-destinations.md)
- **m** [How do you scope a `ViewModel` to a destination or navigation graph and restore navigation state?](answers/navigation/navigation-viewmodel-scope.md)
- **m** [Deep links vs. verified App Links. How would you handle a link that requires authentication?](answers/navigation/deep-links-and-authentication.md)
- **s** [How does Navigation 3's app-owned back stack differ from the `NavController` approach? How would you support predictive back and multiple panes?](answers/navigation/navigation-3-vs-navcontroller.md)

### Dagger and Hilt

- **j** [What problem does Dependency Injection solve? Compare constructor injection with a Service Locator.](answers/dagger-and-hilt/dependency-injection-vs-service-locator.md)
- **m** [Compare constructor injection, `@Binds`, and `@Provides`. When do you need a qualifier?](answers/dagger-and-hilt/inject-binds-provides-qualifiers.md)
- **m** [What do Dagger components and subcomponents represent? How does Hilt organize them for Android?](answers/dagger-and-hilt/components-and-subcomponents.md)
- **m** [Explain Hilt component lifetimes and scopes. How do `@Singleton`, `@ActivityRetainedScoped`, and `@ViewModelScoped` differ?](answers/dagger-and-hilt/hilt-scopes-and-lifetimes.md)
- **m** [How do `@HiltViewModel`, `@AndroidEntryPoint`, and `@InstallIn` work together?](answers/dagger-and-hilt/hilt-android-annotations.md)
- **s** [When do you need `@EntryPoint` or assisted injection? How would you avoid retaining a short-lived dependency in a longer-lived scope?](answers/dagger-and-hilt/entry-points-and-assisted-injection.md)

### Koin (Optional)

- **m** [How do you define modules and choose between `single`, `factory`, and `scoped` definitions?](answers/koin-optional/koin-definition-lifetimes.md)
- **m** [How do Koin scopes relate to Activity, Fragment, and `ViewModel` lifecycles?](answers/koin-optional/koin-android-scopes.md)
- **s** [Compare Koin and Dagger/Hilt in terms of dependency validation, startup cost, tooling, and maintenance for your project.](answers/koin-optional/koin-vs-hilt.md)
- **m** [How would you verify module configuration and replace dependencies in tests?](answers/koin-optional/koin-configuration-tests.md)

### Patterns and Architecture

- **m** [Compare MVP, MVVM, and MVI. How would you choose an approach for a screen?](answers/patterns-and-architecture/mvp-mvvm-mvi.md)
- **m** [Explain Unidirectional Data Flow (UDF). How do UI state and user actions move through the app?](answers/patterns-and-architecture/unidirectional-data-flow.md)
- **m** [What responsibilities belong to a `ViewModel`, repository, and data source? When does a use case add value?](answers/patterns-and-architecture/viewmodel-repository-usecase.md)
- **s** [Clean Architecture and the dependency rule - where would you draw module boundaries, and what complexity would you avoid in a small app?](answers/patterns-and-architecture/clean-architecture-boundaries.md)
- **m** [How would you represent loading, content, empty, and error states without allowing invalid combinations?](answers/patterns-and-architecture/modeling-ui-state.md)
- **s** [How would you handle navigation and snackbar actions across lifecycle changes? Discuss state, delivery guarantees, and the risks of one-off event streams.](answers/patterns-and-architecture/ui-actions-and-delivery-guarantees.md)
- **m** [Give practical uses of Strategy, Factory, Adapter, and Decorator. What tradeoffs come with global singletons?](answers/patterns-and-architecture/practical-design-patterns.md)
- **s** [How would you design an offline-first feature with a single source of truth, optimistic updates, and conflict resolution?](answers/patterns-and-architecture/offline-first-feature-design.md)

### Kotlin

- **j** [`val` vs. `var`. Why does `val` not guarantee that an object is immutable?](answers/kotlin/val-var-and-mutability.md)
- **j** [Compare final, open, and abstract classes, and interfaces. Which declarations can be overridden by default?](answers/kotlin/final-open-abstract.md)
- **j** [Default and named arguments, `vararg`, and the spread operator - how do they affect a function's call sites?](answers/kotlin/function-arguments.md)
- **j** [Nullable types, safe calls, Elvis operator, and `!!` - how do you work safely with missing values?](answers/kotlin/null-safety.md)
- **m** [What are platform types in Java interop? When is a smart cast unavailable?](answers/kotlin/platform-types-and-smart-casts.md)
- **j** [Compare `==` and `===`. How are `equals()` and `hashCode()` related?](answers/kotlin/equality-and-hash-code.md)
- **m** [What do data classes generate? Why is `copy()` a shallow copy, and which properties participate in equality?](answers/kotlin/data-class-generated-members.md)
- **j** [Objects, companion objects, and top-level declarations - when would you use each?](answers/kotlin/objects-companions-top-level.md)
- **m** [Nested vs. inner classes - which holds an outer instance, and how can that cause an Android memory leak?](answers/kotlin/nested-vs-inner-classes.md)
- **m** [Compare enums, sealed classes, and sealed interfaces. How does an exhaustive `when` help model state?](answers/kotlin/enum-sealed-state.md)
- **m** [Visibility modifiers - what does `internal` mean, and how does it differ from Java package visibility?](answers/kotlin/visibility-and-internal.md)
- **m** [Read-only vs. mutable collections. Why is `List<T>` not a guarantee of immutability?](answers/kotlin/read-only-vs-immutable-collections.md)
- **m** [Compare `IntArray` and `Array<Int>`. Where does boxing occur, and why can it matter in a hot path?](answers/kotlin/primitive-arrays-and-boxing.md)
- **m** [How do `@JvmStatic`, `@JvmField`, and `@JvmOverloads` affect Java callers? When do annotation use-site targets such as `@field:` and `@get:` matter?](answers/kotlin/jvm-interop-annotations.md)
- **m** [Extension functions and properties - how are they resolved, and can they override members?](answers/kotlin/extension-resolution.md)
- **m** [Compare `let`, `run`, `with`, `apply`, and `also`. What are the risks of nesting scope functions?](answers/kotlin/scope-functions.md)
- **m** [Compare `lateinit` and delegated properties such as `by lazy`. What thread-safety options does `lazy` provide?](answers/kotlin/lateinit-and-lazy.md)
- **m** [Higher-order functions, lambdas, and function types with receivers - how do they support a DSL?](answers/kotlin/higher-order-functions-and-dsls.md)
- **m** [A function type vs. a `fun interface` - how do SAM conversion, identity, and Java interoperability affect the choice?](answers/kotlin/function-types-vs-fun-interfaces.md)
- **s** [Explain `inline`, `noinline`, `crossinline`, and reified type parameters. What limitations remain because of type erasure?](answers/kotlin/inline-and-reified.md)
- **s** [Why can a public inline function not freely access private implementation details? How does `@PublishedApi` affect compatibility?](answers/kotlin/published-api-and-inline-compatibility.md)
- **s** [Generics - declaration-site variance (`in`/`out`), type projections, and star projections. How do they relate to Java wildcards?](answers/kotlin/generics-and-variance.md)
- **m** [Value classes vs. data classes and type aliases. When can a value class be boxed?](answers/kotlin/value-data-and-alias-types.md)
- **m** [Compare `Unit`, `Nothing`, and nullable return types. When is each useful?](answers/kotlin/unit-nothing-nullable.md)
- **m** [How does `use` manage a closeable resource when a block returns early or throws? Why can a lazily consumed `Sequence` escape the resource's lifetime?](answers/kotlin/use-and-lazy-resource-lifetimes.md)
- **m** [Exceptions and `Result` - how would you model expected failures without accidentally swallowing coroutine cancellation?](answers/kotlin/exceptions-result-and-cancellation.md)
- **s** [What do context parameters solve compared with extension receivers and explicit parameters? How do they differ from the older context receivers feature?](answers/kotlin/context-parameters.md)
- **m** [What does `@OptIn` mean? How would you evaluate the stability and compatibility of a Kotlin API before adopting it?](answers/kotlin/opt-in-and-api-stability.md)

### Kotlin Versions

#### [Kotlin 2.0](https://kotlinlang.org/docs/whatsnew20.html)

- **m** [What changed with the stable K2 compiler? How would you investigate source compatibility or smart-cast changes during migration?](answers/kotlin-versions/kotlin-20-k2-migration.md)
- **m** [Why does the Compose compiler Gradle plugin follow the Kotlin version? What changes when migrating from the old compiler extension setup?](answers/kotlin-versions/kotlin-20-compose-compiler-plugin.md)

#### [Kotlin 2.1-2.2](https://kotlinlang.org/docs/whatsnew22.html)

- **m** [How do guard conditions in `when` simplify branching? What changed between their preview in 2.1 and stabilization in 2.2?](answers/kotlin-versions/kotlin-22-when-guards.md)
- **m** [When can non-local `break` and `continue` be used inside inline lambdas? How do they differ from returning from a lambda?](answers/kotlin-versions/kotlin-22-non-local-loop-control.md)
- **m** [What does multi-dollar string interpolation solve when embedding JSON, templates, or source code containing `$` characters?](answers/kotlin-versions/kotlin-22-multi-dollar-interpolation.md)

#### [Kotlin 2.3](https://kotlinlang.org/docs/whatsnew23.html)

- **m** [When are nested type aliases useful? Do they introduce a new type or capture an outer class's type parameters?](answers/kotlin-versions/kotlin-23-nested-type-aliases.md)
- **s** [What bugs can the experimental unused return value checker detect? How would you introduce it without hiding meaningful warnings?](answers/kotlin-versions/kotlin-23-unused-result-checker.md)

#### [Kotlin 2.4](https://kotlinlang.org/docs/whatsnew24.html)

- **s** [Which context-parameter capabilities became stable in 2.4? Why do explicit context arguments still need experimental opt-in?](answers/kotlin-versions/kotlin-24-context-parameter-stability.md)
- **m** [How do stable explicit backing fields let you expose `StateFlow` while keeping a `MutableStateFlow` field, without a second backing property?](answers/kotlin-versions/kotlin-24-explicit-backing-fields.md)
- **m** [How do the stabilized annotation defaulting rules and `@all` meta-target affect constructor properties used by Android or validation frameworks?](answers/kotlin-versions/kotlin-24-annotation-targets.md)
- **m** [Experimental collection literals - how does the expected type affect `[]`, and when is a custom `operator fun of` needed?](answers/kotlin-versions/kotlin-24-collection-literals.md)
- **m** [When would you choose the stable common `kotlin.uuid.Uuid` API over `java.util.UUID`? What would you check when migrating serialized identifiers?](answers/kotlin-versions/kotlin-24-common-uuid.md)

### Kotlin Coroutines

- **j** [What are coroutines, and how do they differ from threads?](answers/kotlin-coroutines/coroutines-vs-threads.md)
- **j** [What does `suspend` mean? Does a suspending function automatically run on a background thread?](answers/kotlin-coroutines/suspend-is-not-background.md)
- **m** [Structured concurrency - how do a `CoroutineScope`, its `Job`, and child coroutines relate?](answers/kotlin-coroutines/structured-concurrency-job-tree.md)
- **m** [Compare `viewModelScope`, `lifecycleScope`, and an application-owned scope. Why is `GlobalScope` usually discouraged?](answers/kotlin-coroutines/android-coroutine-scopes.md)
- **m** [Compare `launch`, `async`, and `withContext`. When is concurrency actually introduced?](answers/kotlin-coroutines/launch-async-withcontext.md)
- **m** [Dispatchers (`Main`, `Main.immediate`, `IO`, `Default`) - how would you make a blocking operation safe to call from the main thread?](answers/kotlin-coroutines/dispatcher-choice.md)
- **m** [How does cooperative cancellation work? What do `isActive`, `ensureActive`, and `yield` do in CPU-intensive code?](answers/kotlin-coroutines/cooperative-cancellation.md)
- **s** [Compare `Job` and `SupervisorJob`, and `coroutineScope` and `supervisorScope`. How does a failing child affect siblings and the parent?](answers/kotlin-coroutines/job-supervisor-and-scopes.md)
- **s** [How does exception propagation differ between `launch` and `async`? When can `CoroutineExceptionHandler` handle an exception?](answers/kotlin-coroutines/exception-propagation.md)
- **m** [Why should `CancellationException` usually be rethrown? How can `runCatching` or a broad `catch` break cancellation?](answers/kotlin-coroutines/rethrow-cancellation.md)
- **m** [Compare `withTimeout` and `withTimeoutOrNull`. How would you release resources on cancellation?](answers/kotlin-coroutines/timeouts-and-resource-cleanup.md)
- **s** [When is `NonCancellable` appropriate for cleanup, and what are the risks of using it for regular work?](answers/kotlin-coroutines/noncancellable-cleanup.md)
- **m** [Channels vs. shared flows - how do buffering, suspension, and multiple consumers affect delivery?](answers/kotlin-coroutines/channels-vs-broadcast-flows.md)

### Kotlin Flow

- **j** [What is a cold Flow? What happens when it is collected twice?](answers/kotlin-flow/cold-flow-and-recollection.md)
- **m** [Compare `flow`, `channelFlow`, and `callbackFlow`. Why is `awaitClose` important when adapting callbacks?](answers/kotlin-flow/flow-builders-and-callbacks.md)
- **m** [Intermediate vs. terminal operators. When does a Flow start doing work?](answers/kotlin-flow/flow-operator-execution.md)
- **m** [How does `flowOn` affect upstream execution? Why is emitting from another context inside `flow` problematic?](answers/kotlin-flow/flow-on-and-context-preservation.md)
- **m** [Compare `buffer`, `conflate`, and `collectLatest`. Which values or work can be skipped or cancelled?](answers/kotlin-flow/buffer-conflate-collectlatest.md)
- **m** [Compare `flatMapConcat`, `flatMapMerge`, and `flatMapLatest`.](answers/kotlin-flow/flattening-flows.md)
- **m** [How would you implement search with `debounce`, `distinctUntilChanged`, and `flatMapLatest`?](answers/kotlin-flow/debounced-search.md)
- **m** [Compare `combine` and `zip`. How do they behave when sources emit at different rates?](answers/kotlin-flow/combine-vs-zip.md)
- **m** [How do `catch`, `retry`, and `onCompletion` interact with upstream errors, downstream errors, and cancellation?](answers/kotlin-flow/flow-error-boundaries.md)
- **m** [Compare `StateFlow` and `SharedFlow`: current value, replay, equality-based conflation, and slow collectors.](answers/kotlin-flow/stateflow-vs-sharedflow.md)
- **m** [What do `stateIn`, `shareIn`, and `SharingStarted.WhileSubscribed` do? Who owns the upstream coroutine?](answers/kotlin-flow/statein-sharein-and-ownership.md)
- **s** [Why can a `SharedFlow` event be missed while the UI is stopped? What delivery guarantees would you design for a critical action?](answers/kotlin-flow/critical-action-delivery.md)

### Networking

- **j** [HTTP methods, status codes, and headers - what should the client do differently for transport errors and unsuccessful HTTP responses?](answers/networking/http-errors-and-semantics.md)
- **m** [How do Retrofit suspend APIs, OkHttp, and serialization work together? How do cancellation and timeouts propagate?](answers/networking/retrofit-okhttp-serialization.md)
- **m** [Application vs. network interceptors in OkHttp. Where would you add headers, logging, or caching behavior?](answers/networking/application-network-interceptors.md)
- **s** [How would you refresh an expired token when several requests fail at once, without refresh loops or duplicate refresh requests?](answers/networking/single-flight-token-refresh.md)
- **m** [Retries, exponential backoff, and idempotency - when can retrying a request create duplicate data?](answers/networking/retries-backoff-idempotency.md)
- **m** [HTTP caching vs. a local database cache. How do you handle stale data, pagination, and offline errors?](answers/networking/http-cache-vs-database-cache.md)

### Testing

- **j** [Unit tests vs. instrumented tests. What belongs in each for an Android app?](answers/testing/unit-vs-instrumented-tests.md)
- **m** [Fakes, mocks, and stubs - how would you choose dependencies for a `ViewModel` or repository test?](answers/testing/fakes-mocks-stubs.md)
- **m** [How do `runTest`, test dispatchers, and a shared `TestCoroutineScheduler` make coroutine tests deterministic?](answers/testing/deterministic-coroutine-tests.md)
- **m** [How would you test Flow emissions, `StateFlow` conflation, cancellation, and a `stateIn` flow using `WhileSubscribed`?](answers/testing/testing-flow-and-stateflow.md)
- **m** [How would you test Compose UI using semantics, user actions, and assertions? When do merged and unmerged semantics trees matter?](answers/testing/compose-ui-tests-and-semantics.md)
- **m** [How would you test a screen's restoration after recreation and after process death? What does `ActivityScenario.recreate()` actually cover?](answers/testing/recreation-vs-process-restoration-tests.md)
- **m** [How would you use a controlled HTTP server to test timeouts, error responses, and token refresh?](answers/testing/controlled-http-integration-tests.md)
- **s** [How would you investigate flaky asynchronous UI tests and choose a useful balance of unit, integration, and end-to-end coverage?](answers/testing/flaky-tests-and-coverage-balance.md)

### Performance and Debugging

- **m** [What causes an ANR? How would you use traces, StrictMode, and production reports to find the cause?](answers/performance-and-debugging/anr-investigation.md)
- **m** [How would you investigate a memory leak, excessive allocations, or an out-of-memory crash using a heap dump?](answers/performance-and-debugging/heap-dumps-and-memory-pressure.md)
- **m** [How do ART, JIT, AOT, and Baseline Profiles relate to startup and runtime performance?](answers/performance-and-debugging/art-jit-aot-profiles.md)
- **s** [How would you measure cold startup and scrolling performance with Macrobenchmark and Perfetto? Why use a release-like build?](answers/performance-and-debugging/macrobenchmark-and-perfetto.md)
- **s** [How would you diagnose Compose jank using tracing, Layout Inspector, and compiler reports before changing stability annotations?](answers/performance-and-debugging/diagnosing-compose-jank.md)
- **s** [How would you verify that an optimization improves user-visible performance across device classes and does not regress battery usage?](answers/performance-and-debugging/validating-performance-improvements.md)

### Build and Delivery

- **j** [APK vs. Android App Bundle. What does app signing protect?](answers/build-and-delivery/apk-app-bundle-signing.md)
- **m** [Build types, product flavors, and source sets - how would you configure separate app variants?](answers/build-and-delivery/build-types-flavors-source-sets.md)
- **m** [Gradle Kotlin DSL, version catalogs, and convention plugins - what problem does each solve?](answers/build-and-delivery/gradle-dsl-catalogs-conventions.md)
- **m** [Compare KSP and kapt. How would you check processor compatibility when upgrading Kotlin and the Android Gradle Plugin?](answers/build-and-delivery/ksp-kapt-and-upgrades.md)
- **m** [What do R8 shrinking, optimization, and obfuscation do? How do keep rules and mapping files help diagnose release-only failures?](answers/build-and-delivery/r8-and-release-only-failures.md)
- **s** [How would you improve build speed using measurements, module boundaries, incremental processing, and Gradle caches?](answers/build-and-delivery/build-speed-investigation.md)
- **s** [How would you check 16 KB page-size compatibility when an app or a third-party SDK includes native libraries?](answers/build-and-delivery/native-16kb-page-sizes.md)

### Gradle and Gradle DSL

#### Build lifecycle and scripts

- **j** [What does the Gradle Wrapper pin? How would you upgrade and verify the build distribution?](answers/gradle-and-gradle-dsl/gradle-wrapper.md)
- **j** [Explain Gradle initialization, configuration, and execution. Why can configuration-time work slow down an unrelated task?](answers/gradle-and-gradle-dsl/build-lifecycle.md)
- **j** [What belongs in `settings.gradle.kts` versus `build.gradle.kts`? How do `pluginManagement` and `dependencyResolutionManagement` differ?](answers/gradle-and-gradle-dsl/settings-and-build-scripts.md)
- **j** [Groovy DSL vs. Kotlin DSL - what changes, and is the build script Kotlin version the same as the app Kotlin version?](answers/gradle-and-gradle-dsl/groovy-vs-kotlin-dsl.md)
- **m** [How do `plugins`, `apply false`, and Kotlin DSL type-safe accessors interact? Why can an `android` block be unavailable?](answers/gradle-and-gradle-dsl/plugins-and-type-safe-accessors.md)

#### Tasks and lazy configuration

- **m** [What is the difference between configuring a task and adding a `doLast` or `@TaskAction`? When does each piece of code run?](answers/gradle-and-gradle-dsl/task-configuration-vs-actions.md)
- **m** [Compare `tasks.register`, `tasks.named`, and `configureEach` with eager task creation. What accidentally realizes tasks?](answers/gradle-and-gradle-dsl/lazy-task-registration.md)
- **m** [Explain `Provider`, `Property`, `map`, `flatMap`, `convention`, and `set`. How can an early `get()` call break lazy wiring?](answers/gradle-and-gradle-dsl/providers-and-properties.md)
- **m** [How do producer/consumer providers, `dependsOn`, `mustRunAfter`, and `finalizedBy` differ?](answers/gradle-and-gradle-dsl/task-dependencies-and-ordering.md)
- **s** [How would you implement a deterministic custom task with declared inputs and outputs? When is `@CacheableTask` appropriate?](answers/gradle-and-gradle-dsl/custom-task-inputs-outputs.md)

#### Caching and build logic

- **m** [Distinguish `UP-TO-DATE` checks, the build cache, the configuration cache, and incremental task execution.](answers/gradle-and-gradle-dsl/gradle-cache-layers.md)
- **s** [What makes a task incompatible with the configuration cache? How should it obtain files, environment values, and Gradle services?](answers/gradle-and-gradle-dsl/configuration-cache-compatible-tasks.md)
- **m** [When would you use `buildSrc` or an included `build-logic` build for convention plugins? Why avoid broad cross-project configuration?](answers/gradle-and-gradle-dsl/buildsrc-vs-included-build-logic.md)
- **s** [How would you test a convention plugin or custom task with Gradle TestKit, including configuration-cache and build-cache behavior?](answers/gradle-and-gradle-dsl/testing-gradle-plugins.md)

#### Dependencies and resolution

- **m** [Compare `api`, `implementation`, `compileOnly`, and `runtimeOnly`. How does dependency exposure affect consumers and recompilation?](answers/gradle-and-gradle-dsl/dependency-exposure-configurations.md)
- **s** [What are declarable, resolvable, and consumable configurations? How does variant-aware resolution choose an Android library variant?](answers/gradle-and-gradle-dsl/configuration-roles-and-variants.md)
- **m** [How would you diagnose an unexpected transitive dependency version? When are constraints or exclusions safer than forcing a version?](answers/gradle-and-gradle-dsl/dependency-conflict-investigation.md)
- **m** [Why does a version catalog not enforce the resolved version? Compare a BOM, `platform`, `enforcedPlatform`, and dependency constraints.](answers/gradle-and-gradle-dsl/catalogs-platforms-and-constraints.md)
- **m** [How do repository order, centralized repositories, and content filters affect dependency resolution and provenance?](answers/gradle-and-gradle-dsl/repository-policy-and-content-filters.md)
- **s** [Dependency locking vs. dependency verification - what does each protect, and what else is needed for reproducible builds?](answers/gradle-and-gradle-dsl/dependency-locking-and-verification.md)

#### Android toolchains and AGP

- **m** [Distinguish the JDK running Gradle, Java toolchains, `sourceCompatibility`, `targetCompatibility`, and Kotlin `jvmTarget`. Which determines Android API availability?](answers/gradle-and-gradle-dsl/jdk-toolchain-and-bytecode-targets.md)
- **m** [Language desugaring vs. core library desugaring - what problems do they solve, and why does a newer JVM target not make every Java API available?](answers/gradle-and-gradle-dsl/language-vs-library-desugaring.md)
- **m** [AGP 9.0 - what changes with built-in Kotlin? How should `kapt`, compiler options, and KMP modules be migrated?](answers/gradle-and-gradle-dsl/agp-9-built-in-kotlin.md)
- **s** [How do `finalizeDsl`, `beforeVariants`, `onVariants`, and artifact APIs replace `afterEvaluate` or hard-coded task names? What changes with AGP 9.0 public DSL types?](answers/gradle-and-gradle-dsl/agp-variant-and-artifact-apis.md)

### Production Engineering

- **m** [What should an Android CI pipeline validate before producing a release? How would you separate fast feedback from device and release checks?](answers/production-engineering/android-ci-pipeline.md)
- **s** [How would you define staged-rollout health checks and recover from a bad release? What does halting a rollout actually undo?](answers/production-engineering/staged-rollout-and-recovery.md)
- **s** [How would you correlate crashes, ANRs, performance regressions, and failed user journeys with a release without logging sensitive data?](answers/production-engineering/release-observability.md)
- **m** [How would you design feature flags and remote configuration with safe defaults, offline behavior, and a useful kill switch?](answers/production-engineering/feature-flags-and-remote-config.md)
- **s** [How do you evolve a backend API while old app versions remain installed? Which seemingly additive changes can break a mobile client?](answers/production-engineering/mobile-api-backward-compatibility.md)
- **m** [How would you introduce lint or custom static-analysis rules without allowing an existing baseline to hide new violations?](answers/production-engineering/static-analysis-and-baselines.md)

### Security and Privacy

- **m** [Why can secrets embedded in an APK be extracted? What belongs on a backend instead of in the app?](answers/security-and-privacy/embedded-secrets.md)
- **m** [How would you protect stored authentication tokens? What does Android Keystore provide, and how do backups and logs affect data exposure?](answers/security-and-privacy/token-storage-and-keystore.md)
- **m** [Exported components, mutable `PendingIntent`s, and untrusted deep-link input - what risks do they introduce?](answers/security-and-privacy/component-and-intent-security.md)
- **m** [How would you use Credential Manager for passwords, passkeys, and federated sign-in? Where should authentication be verified?](answers/security-and-privacy/credential-manager-and-server-validation.md)
- **s** [How would you audit third-party SDK permissions, data collection, and local network access when preparing a platform upgrade?](answers/security-and-privacy/third-party-sdk-audit.md)

### Kotlin Multiplatform (Optional)

- **m** [What can be shared with Kotlin Multiplatform? How does sharing business logic differ from sharing UI with Compose Multiplatform?](answers/kotlin-multiplatform-optional/kmp-logic-vs-shared-ui.md)
- **m** [Explain common and platform source sets. When would you use `expect`/`actual` declarations vs. interfaces with injected implementations?](answers/kotlin-multiplatform-optional/source-sets-and-platform-apis.md)
- **s** [How would you evaluate library support, platform interop, testing, and build complexity before moving an Android feature into shared code?](answers/kotlin-multiplatform-optional/evaluating-kmp-adoption.md)
