
### PERFORMANCE OPTIMIZATION

There are a number of techniques for increasing the performance, and perceived performance, of applications built with the Xamarin platform and Zebble.

Avoid Remote calls before the page is shown
Your app's pages should load very quickly. If they have contents that come from a Web Service (or Web API) call then lazy load such content. Before your page is shown, it should not make any Web Service calls in general.

 

Other tips:

- [Use the Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#profiler)
- [Unsubscribe from Events](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#events)
- [Use the SGen Garbage Collector](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#sgen)
- [Reduce the Size of the Application](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#linker)
- [Optimize Image Resources](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#optimizeimages)
- [Reduce the Application Activation Period](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#activationperiod)
- [Reduce Web Service Communication](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/memory_perf_best_practices/#webservicecommunication)

#### Ensure HardwareAccelerated is on (Android)

Set android:hardwareAccelerated="true" in AndroidManifest.xml file.