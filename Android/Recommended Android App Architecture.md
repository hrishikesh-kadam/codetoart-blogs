## Recommended Android App Architecture

This blog is based on [Guide to app architecture](https://developer.android.com/jetpack/docs/guide), which doesn't advocate to use any particular architecture but mostly focuses on how to structure an app using [Architecture Components](https://developer.android.com/jetpack/#architecture-components).

![1](https://codetoart.com/wp-content/uploads/2018/12/recommended-app-architecture.png)


## Isn't this MVVM?

Architecture Components have been developed in such a way that when we integrate it in our project, they eventually end up organizing our project in MVVM like  architecture. Most important components to look out are -

- [`ViewModel`](https://developer.android.com/topic/libraries/architecture/viewmodel)
- [`LiveData`](https://developer.android.com/topic/libraries/architecture/livedata)
- [`Data Binding`](https://developer.android.com/topic/libraries/data-binding/)

If we use `ViewModel` and Data Binding, then we can call our architecture as MVVM and if we use `ViewModel` and `LiveData`, then it is just MVVM without Data Binding.

Data Binding library was announced back in Google I/O 2015. Using it or not can be developer's choice to bind `ViewModel` with the View.


## Get Started

We have developed the [UpcomingMovies-Android](https://github.com/codetoart/UpcomingMovies-Android/tree/recommended-app-architecture) project, which demonstrates the use of `ViewModel` and `LiveData` and many other Android Jetpack components in Kotlin language. We referred following projects from [github.com/googlesamples](github.com/googlesamples) -

- https://github.com/googlesamples/android-architecture-components
- https://github.com/googlesamples/android-architecture


## How is `ViewModel` different than Presenter?

Many developers do not preserve Presenter on configuration changes like screen rotation. So long running network calls had to be called again, which shouldn't be the case. Android does not have anything to preserve Presenter out of the box. So they made `ViewModel` as a component. This `ViewModel` component not necessarily means ViewModel of the MVVM but can be very closely related with.

`ViewModel` attaches to the lifecycle of your `Activity`/`Fragment`. This means it is not destroyed on `Activity`'s/`Fragment`'s `onDestroy()` method but gets cleared only when `Activity`/`Fragment` is finishing. So you can say `ViewModel` as a Presenter with lifecycle aware feature.

In MVP, it gets difficult to access application context. Here in ViewModel library, `AndroidViewModel` is a class which extends from `ViewModel` and is nothing but `Application` aware `ViewModel`.


## What is `LiveData`?

`LiveData` is a lifecycle aware observable pattern, which emits value only when `Activity`/`Fragment` is in `STARTED` or `RESUMED` state. Have a look at `LiveDataUnitTest.kt`. `LiveData` does also have `observeForever()` method, which is not lifecycle aware and is always in an active state.

We can add multiple `Observer` to `LiveData` and whenever a value in it changes, all the added `Observer` will get notified. `LiveData` are generally stored in `ViewModel` so that we can expose data to `Activity`/`Fragment` through `ViewModel` and add necessary `Observer`.


## Expose data through Repository

Data can be fetched from a remote data source or can be stored locally for caching. A Repository isn't an architecture component but just the way of organizing data communication, same as the way in MVP. A Repository might have only remote data source or only local data source or combination of both. This would vary depending upon the use case. Organizing data communication through Repository makes it extendable and easy to test.


## Local Data Source using [`Room`](https://developer.android.com/topic/libraries/architecture/room)

`Room` is a persistence library which provides an abstraction layer over SQLite to allow for more robust database access while harnessing the full power of SQLite. We can communicate to local db by DAOs made using `Room`. DAO makes it easy for developers to write a SQLite query in a functional way. Room also has in memory db approach which saves the db until an `Activity`/`Fragment` is not finished. See `UpcomingMovieDaoTest.kt` in the attached project.


## Other Architecture Components to look at

We have also used the [`Paging`](https://developer.android.com/topic/libraries/architecture/paging/) library which makes it easy to load data from a source which supports pagination. It has three abstract classes `PageKeyedDataSource`, `ItemKeyedDataSource` and `PositionalDataSource`, which we can extend and use it according to our need. See `UpcomingMoviesDataSource.kt` which extends from `PageKeyedDataSource` to fetch remote data depending on the page key and if network call fails then it checks for the cached copy in local db using `Room`.


## Conclusion

We have made our first attempt towards MVVM, let's see how well it is adopted by developers.

We are proud to always keep hands on latest native tools, and that requires a team of passionate professionals. We’d be glad to help you with full-cycle app development using latest native tools with our team of professionals. Feel free to [contact us](https://codetoart.com/contact-us/) with any ideas you have. We’ll help you translate them into reality.
