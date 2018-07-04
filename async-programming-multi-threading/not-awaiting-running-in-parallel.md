
### NOT AWAITING (RUNNING IN PARALLEL)

Sometimes you may need to invoke an async (task-returning) method, but you don't want to "await" it.  Instead, you want it to just run in parallel.

If you invoke an async method without awaiting it, in general, Visual Studio will show you a warning. The reason for that is because in case of an exception in that method, it gets lost and silenced, which can lead to unexpected and hard to find problems.

#### Zebble's solution

There is an extension method named RunInParallel() which can be called on any **Task**.

It will then watch for exceptions in the method and then:

- Log the exception in the output window
- If in Dev mode, then it will throw the exception also on the UI thread, so Visual Studio debugger can break and allow you to investigate