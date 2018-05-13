 # Paging Library - Architecture Components

As you know some last year Architecture Components was released like a guideline to help to build better architecture for android applications 
so I decided start to play with Paging Library & RX the new feature supported on it, this sample was created to practice how *Paging Library* with *Rx* works.

## What Have I learned?

### Paging Library (:+1)
 
The Paging Library makes it easier for you to load data on demand within your app's RecyclerView.
  
### PagedList 
Collection that loads data in pages, asynchronously. A PagedList can be used to load data from sources you define, and present it easily in your UI with a RecyclerView.
    
### DataSource and DataSource.Factory  
DataSource is the base class for loading snapshots of data into a PagedList. A DataSource.Factory is used to create a DataSource.

### PageKeyedDataSource 

DataSource used to load embed next/previous keys.

### ItemKeyedDataSource

DataSource used to retrieve data from item N to fetch item N+1

### PositionalDataSource 
if you need to fetch pages of data from any location you choose.

### LivePagedListBuilder 
Class used to build a LiveData<PagedList> based on DataSource.Factory and a PagedList.Config.
  
### RxPagedListBuilder
Class used to build a Observable<PagedList> based on DataSource.Factory and a PagedList.Config.
  
### BoundaryCallback 
Helper callback to signals when a PagedList has reached the end of available data.
    
### PagedListAdapter
RecyclerView.Adapter that presents paged data from PagedLists in a RecyclerView. PagedListAdapter listens to PagedList loading callbacks as pages are loaded, and uses DiffUtil to compute fine grained updates as new PagedLists are received.


## What was wrong?
 
 * I get stranger behaviors with LinearLayoutManager & GridLayoutManager
 * onItemAtEndLoaded` is called when the ui is not visible so I'm not scrolling on the end the list.
 * Complicated to handle errors (it implies use LiveData observables in DataLayer to be used in other layers, I prefer keep working with RX and LiveData on UI layer.)
 * Limited API to work on Rx architectures.
 * I think there should be a reactive version of `PagedList.BoundaryCallback<Movie>() `
 * It's alpha so I won't use it in production in a near future
 * Could save a lot of time to handle the logic of retrieve items but the architecture will be forced to use all the elements of pager library like `PagedList` & `PagedListAdapter`
 
I like the library but there are stuffs to fix it before to start to use it production.

# Demo
![](./art/device-2018-05-12-205800.gif)


### Resources to start with Paging Library on Android

* [Paging library overview Android by Google][10]
* [Paging Library CodeLab][11]
* [PagingWithNetworkSample by Yigit Boyar][12]
* [Android Jetpack: manage infinite lists with RecyclerView and Paging (Google I/O '18)][13]
* [Android Jetpack: what's new in Architecture Components (Google I/O '18)][13]

 [9]: https://developer.android.com/topic/libraries/architecture/paging/
[10]: https://codelabs.developers.google.com/codelabs/android-paging/index.html?index=..%2F..%2Findex#0
[11]: https://github.com/googlesamples/android-architecture-components/tree/master/PagingWithNetworkSample
[12]: https://www.youtube.com/watch?v=BE5bsyGGLf4
[13]: https://www.youtube.com/watch?v=pErTyQpA390&t=862s
[14]: https://antonioleiva.com/kotlin-android-developers-book/



Do you want to contribute?
--------------------------

Feel free to report or add any useful feature, I will be glad to improve it with your help.

Developed By
------------

* Erik Jhordan Rey  - <erikjhordan.rey@gmail.com> or <erik.gonzalez@schibsted.com>

License
-------

    Copyright 2018 Erik Jhordan Rey

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
