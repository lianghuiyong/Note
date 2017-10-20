```xml
    <android.support.v4.widget.SwipeRefreshLayout
        android:id="@+id/refresh_layout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginBottom="@dimen/sx_dp45"
        android:background="@color/color_eeeeee"
        app:layout_behavior="@string/appbar_scrolling_view_behavior">

        <android.support.v7.widget.RecyclerView
            android:id="@+id/recyclerView"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layoutManager="LinearLayoutManager"/>
    </android.support.v4.widget.SwipeRefreshLayout>
```

```java
    myGuestAdapter = new CollegeInvoiceAdapter(recyclerView);
    recyclerView.setAdapter(myGuestAdapter);
    refreshLayout.setColorSchemeColors(Color.RED, Color.BLUE, Color.GREEN, Color.YELLOW);
    refreshLayout.setOnRefreshListener(this);
    myGuestAdapter.setOnLoadMoreListener(this, recyclerView);
```