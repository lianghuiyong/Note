1、CheckButton改变选中栏的值
```
 CompoundButtonCompat.setButtonTintList(
            (RadioButton) findViewById(R.id.colorBlue),
            getResources().getColorStateList(R.color.blue));
```

2、AppCompatCheckBox禁止点击事件
```xml
    android:clickable="false"
    android:focusable="false"
    android:focusableInTouchMode="false"
```