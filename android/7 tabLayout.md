修改tabLayout下划线距离
```
    public void setTabLine(TabLayout tab, int left, int right) {
        try {
            Class<?> tablayout = tab.getClass();
            Field tabStrip = tablayout.getDeclaredField("mTabStrip");
            tabStrip.setAccessible(true);
            LinearLayout ll_tab = (LinearLayout) tabStrip.get(tabLayout);
            for (int i = 0; i < ll_tab.getChildCount(); i++) {
                View child = ll_tab.getChildAt(i);
                child.setPadding(0, 0, 0, 0);
                LinearLayout.LayoutParams params = new LinearLayout.LayoutParams(0, LinearLayout.LayoutParams.MATCH_PARENT, 1);
                //修改两个tab的间距
                params.setMarginStart(ScreenUtils.dip2px(context, left));
                params.setMarginEnd(ScreenUtils.dip2px(context, right));
                child.setLayoutParams(params);
                child.invalidate();
            }
        } catch (NoSuchFieldException e) {
            e.printStackTrace();
        } catch (IllegalAccessException e) {
            e.printStackTrace();
        }
    }
```

不和viewpager绑定

```xml
android.support.design.widget.TabLayout
    android:id="@+id/tabLayout"
    android:layout_weight="1"
    android:layout_width="match_parent"
    android:layout_height="0dp"
    app:tabGravity="fill"
    app:tabIndicatorHeight="0dp"
    app:tabMode="fixed"
    app:tabSelectedTextColor="#FF4081"
    app:tabTextColor="#000">
```

```
    //设置自定义视图
    /*for (int i = 0; i < tabLayout.getTabCount(); i++) {
        TabLayout.Tab tab = tabLayout.getTabAt(i);
        tab.setCustomView(adapter.getTabView(i));
    }*/
    for (int i = 0; i < 3; i++) {
        TabLayout.Tab tab = tabLayout.newTab();
        tab.setCustomView(adapter.getTabView(i));
        tabLayout.addTab(tab);
    }
```