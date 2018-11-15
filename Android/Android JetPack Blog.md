## [Android JetPack](https://developer.android.com/jetpack/)

Jetpack is a collection of Android software components to make it easier for you to develop great Android apps. It was announced at Google I/O 2018. Jetpack builds on the foundations laid out by **Support Library** and **Architecture Component**.

## [AndroidX](https://developer.android.com/jetpack/androidx/)

AndroidX is Jetpack's evolution of the original Android Support Library. It is the open-source project that the Android team uses to develop, test, package, version and release libraries within Jetpack.

According to [Android Support Library Page](https://developer.android.com/topic/libraries/support-library/) -

> Note: With the release of Android 9.0 (API level 28) there is a new version of the support library called AndroidX which is part of Jetpack. The AndroidX library contains the existing support library and also includes the latest Jetpack components.

> You can continue to use the support library. Historical artifacts (those versioned 27 and earlier, and packaged as `android.support.*`) will remain available on Google Maven. However, all new library development will occur in the AndroidX library.

> We recommend using the AndroidX libraries in all new projects. You should also consider migrating existing projects to AndroidX as well.

Like the Support Library, AndroidX ships separately from the Android OS and provides backwards-compatibility across Android releases. AndroidX fully replaces the Support Library by providing feature parity and new libraries. In addition AndroidX includes the following features:

- All packages in AndroidX live in a consistent namespace starting with the string androidx. The Support Library packages have been mapped into corresponding androidx.* packages. For a full mapping of all the old classes and build artifacts to the new ones, see the Package Refactoring page.

- Unlike the Support Library, AndroidX packages are separately maintained and updated. The androidx packages use strict Semantic Versioning starting with version 1.0.0. You can update AndroidX libraries in your project independently.

- All new Support Library development will occur in the AndroidX library. This includes maintenance of the original Support Library artifacts and introduction of new Jetpack components.

So its time to use AndroidX or get stuck with 28.0.0 Support Library.

## [Android Architecture Component](https://developer.android.com/jetpack/arch/)

A collection of libraries that help you design robust, testable, and maintainable apps. Start with classes for managing your UI component lifecycle and handling data persistence.

Architecture Component 1.0 was announced back in Nov 2017 ([Developers Blog](https://android-developers.googleblog.com/2017/11/announcing-architecture-components-10.html)). Then after announcing JetPack at Google I/O 2018, Architecture Component is now considered as a sub component of JetPack.

- [Data Binding](https://developer.android.com/topic/libraries/data-binding/) - Declaratively bind observable data to UI elements.
- [Lifecycles](https://developer.android.com/topic/libraries/architecture/lifecycle) - Create a UI that automatically responds to lifecycle events.
- [LiveData](https://developer.android.com/topic/libraries/architecture/livedata) - Build data objects that notify views when the underlying database changes.
- [Navigation](https://developer.android.com/topic/libraries/architecture/navigation.html) - Handle everything needed for in-app navigation.
- [Paging](https://developer.android.com/topic/libraries/architecture/paging/) - Load data gradually and gracefully within your app’s UI.
- [Room](https://developer.android.com/topic/libraries/architecture/room) - Access your app's SQLite database with in-app objects and compile-time checks.
- [ViewModel](https://developer.android.com/topic/libraries/architecture/viewmodel) - Store UI-related data that isn't destroyed on app rotations.Easily schedule asynchronous tasks for optimal execution.
- [WorkManager](https://developer.android.com/topic/libraries/architecture/workmanager) - Manage your Android background jobs.

You can find sample projects on [googlesamples/android-architecture-components](https://github.com/googlesamples/android-architecture-components) GitHub repo
