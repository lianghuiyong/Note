
```xml
<android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/color_f4f4f4"
    android:fitsSystemWindows="true">

    <android.support.design.widget.AppBarLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:fitsSystemWindows="true"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="@android:color/white"
            android:orientation="vertical">


        </LinearLayout>

        <android.support.design.widget.CollapsingToolbarLayout
            android:layout_width="match_parent"
            android:layout_height="0dp" />

    </android.support.design.widget.AppBarLayout>


    <android.support.v4.widget.NestedScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@android:color/white"
        android:fillViewport="true"
        android:paddingLeft="@dimen/sx_dp10"
        android:paddingRight="@dimen/sx_dp10"
        android:paddingTop="@dimen/sx_dp10"
        android:scrollbars="none"
        app:layout_behavior="@string/appbar_scrolling_view_behavior">


    </android.support.v4.widget.NestedScrollView>

</android.support.design.widget.CoordinatorLayout>

```