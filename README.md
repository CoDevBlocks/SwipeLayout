If you like what I do and want to support me, you can

<a href="https://www.buymeacoffee.com/cosminradu" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

# SwipeLayout

![Maven metadata URL](https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Frepo1.maven.org%2Fmaven2%2Fcom%2Fcodevblocks%2Fandroid%2Fswipelayout%2Fmaven-metadata.xml)
![Java](https://img.shields.io/badge/language-java-10748d.svg)
![Android](https://img.shields.io/badge/platform-android-green.svg)

An extended ConstraintLayout allowing for a child view (see [`swipeView`](https://github.com/CoDevBlocks/SwipeLayout#swipeView)) to be swiped aside (see [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe)) to reveal other child views below it. Swipe limits can be defined using the `swipe_constraint[Side]_to[Side]Of` and `swipe_constraint[Side]_maxLayoutOffset` XML attributes. `swipe_constraint[Side]_maxLayoutOffset` attributes have precedence over `swipe_constraint[Side]_to[Side]Of`. All views referenced by these attributes need to be direct children. You can subscribe to be notified of swipe updates by providing an `OnSwipeListener`.

![SwipeLayout Sample 1](/media/swipelayout_01.gif)

## Sample in-app usage

![Screen Recording](/media/swipelayout_screenrec.gif)

## Installation

Simply add the dependency to your module `build.gradle` file

```groovy
dependencies {
    // ...
    implementation 'com.codevblocks.android:swipelayout:<version>'
    // ...
}
```
Current version available on [Maven](https://search.maven.org/artifact/com.codevblocks.android/swipelayout)

![Maven metadata URL](https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Frepo1.maven.org%2Fmaven2%2Fcom%2Fcodevblocks%2Fandroid%2Fswipelayout%2Fmaven-metadata.xml)

## Usage

Include the `com.codevblocks.android.swipelayout.SwipeLayout` view in your XML layout file. Here is a complete XML example:

```xml
<com.codevblocks.android.swipelayout.SwipeLayout
    android:id="@+id/layout_swipe"
    android:layout_width="match_parent"
    android:layout_height="100dp"

    app:swipe="start|end"

    app:swipeView="@id/view_swipe"
    app:swipeSnapRatio="0.5"
    app:swipeMinFlingDistance="10dp"
    app:swipeMinFlingVelocity="55"
    app:swipeAnimationDuration="200"

    app:swipe_constraintStart_toEndOf="@id/guideline_start"
    app:swipe_constraintEnd_maxLayoutOffset="100dp"

    android:background="#FFD166" >

    <androidx.constraintlayout.widget.Guideline
        android:id="@+id/guideline_start"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        app:layout_constraintGuide_begin="100dp"/>

    <View
        android:id="@+id/view_start"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        android:layout_margin="25dp"
        android:background="#EF476F" />

    <View
        android:id="@+id/view_end"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        android:layout_marginEnd="25dp"
        android:background="#EF476F" />

    <View
        android:id="@+id/view_swipe"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#118AB2" />

</com.codevblocks.android.swipelayout.SwipeLayout>
```

## XML Attributes

#### `swipe`
The sides the `swipeView` can be swiped from.
```
app:swipe="start|end|top|bottom"
```
#### `swipeView`
The child view that can be swiped aside.
```
app:swipeView="@id/view_swipe"
```
#### `swipeSnapRatio`
The ratio in between the swipe view's normal position and maximum swiped position which determines where the view should snap upon a finished drag gesture.
```
app:swipeSnapRatio="0.5"
```
#### `swipeMinFlingDistance`
Distance in pixels a touch can wander before it is assumed the user is swiping. When ommited, the default sistem view configuration value is used (recommended).
```
app:swipeMinFlingDistance="10dp"
```
#### `swipeMinFlingVelocity`
Minimum velocity to initiate a swipe fling, as measured in pixels per second. When ommited, the default sistem view configuration value is used (recommended).
```
app:swipeMinFlingVelocity="55"
```
#### `swipeAnimationDuration`
The duration (in milliseconds) for the open/close swipe animation.
```
app:swipeAnimationDuration="200"
```
#### `swipe_constraintStart_toStartOf`
When defined, in conjunction with a `start` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'start' side to not overshoot the 'start' side of the referenced child view.
```
app:swipe_constraintStart_toStartOf="@id/guideline"
```
#### `swipe_constraintStart_toEndOf`
When defined, in conjunction with a `start` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'start' side to not overshoot the 'end' side of the referenced child view.
```
app:swipe_constraintStart_toEndOf="@id/guideline"
```
#### `swipe_constraintEnd_toStartOf`
When defined, in conjunction with an `end` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'end' side to not overshoot the 'start' side of the referenced child view.
```
app:swipe_constraintEnd_toStartOf="@id/guideline"
```
#### `swipe_constraintEnd_toEndOf`
When defined, in conjunction with an `end` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'end' side to not overshoot the 'end' side of the referenced child view.
```
app:swipe_constraintEnd_toEndOf="@id/guideline"
```
#### `swipe_constraintTop_toTopOf`
When defined, in conjunction with a `top` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'top' side to not overshoot the 'top' side of the referenced child view.
```
app:swipe_constraintTop_toTopOf="@id/guideline"
```
#### `swipe_constraintTop_toBottomOf`
When defined, in conjunction with a `top` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'top' side to not overshoot the 'bottom' side of the referenced child view.
```
app:swipe_constraintTop_toBottomOf="@id/guideline"
```
#### `swipe_constraintBottom_toTopOf`
When defined, in conjunction with a `bottom` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'bottom' side to not overshoot the 'top' side of the referenced child view.
```
app:swipe_constraintBottom_toTopOf="@id/guideline"
```
#### `swipe_constraintBottom_toBottomOf`
When defined, in conjunction with a `bottom` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'bottom' side to not overshoot the 'bottom' side of the referenced child view.
```
app:swipe_constraintBottom_toBottomOf="@id/guideline"
```
#### `swipe_constraintStart_maxLayoutOffset`
When defined, in conjunction with a `start` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'start' side to not overshoot the given dimension.
```
app:swipe_constraintStart_maxLayoutOffset="50dp"
```
#### `swipe_constraintEnd_maxLayoutOffset`
When defined, in conjunction with an `end` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'end' side to not overshoot the given dimension.
```
app:swipe_constraintEnd_maxLayoutOffset="50dp"
```
#### `swipe_constraintTop_maxLayoutOffset`
When defined, in conjunction with a `top` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'top' side to not overshoot the given dimension.
```
app:swipe_constraintTop_maxLayoutOffset="50dp"
```
#### `swipe_constraintBottom_maxLayoutOffset`
When defined, in conjunction with a `bottom` [`swipe`](https://github.com/CoDevBlocks/SwipeLayout#swipe), constraints the swipe view 'bottom' side to not overshoot the given dimension.
```
app:swipe_constraintBottom_maxLayoutOffset="50dp"
```