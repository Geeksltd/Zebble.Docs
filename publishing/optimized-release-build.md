
### OPTIMIZED RELEASE BUILD

#### Android

The following configuration can usually give you the best performance for a release build of your app to submit to the Google Play store:

- Linker: Use All Assemblies
- Enable AOT. Ahead of Time Compilation builds everything upfront, to avoid JIT when first running your app.
- Generate one APK per ABI
- Use LLVM Optimizing Compiler