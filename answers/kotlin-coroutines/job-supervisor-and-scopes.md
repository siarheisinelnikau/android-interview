# Compare `Job` and `SupervisorJob`, and `coroutineScope` and `supervisorScope`. How does a failing child affect siblings and the parent?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Senior · **Topic:** Kotlin Coroutines

## Answer

With an ordinary Job parent, a child's non-cancellation failure normally cancels the parent and its other children. SupervisorJob isolates failures of its direct children so one failed child need not cancel its siblings; cancellation of the supervisor's parent still propagates downward.

`coroutineScope` creates a lexical scope that waits for its children and fails the combined operation when a child fails. `supervisorScope` uses supervisory child-failure behavior and also waits for completion. It does not install automatic error recovery.

If the supervisorScope block itself throws, its children are cancelled. Likewise, allowing an async child's await failure to escape that block fails the scope. Handle acceptable child failures deliberately, and provide an appropriate reporting path for failed launch children rather than assuming supervision swallows their exceptions.

## References

- [kotlinx.coroutines: SupervisorJob](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-supervisor-job.html)
- [kotlinx.coroutines: supervisorScope](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/supervisor-scope.html)
