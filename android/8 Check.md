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

3、

```
public class liveSponsorGuestsAdapter extends BaseQuickAdapter<ActivitySponsorBean.GuestsBean, BaseViewHolder> {

    private int selectPosition = -1;

    public liveSponsorGuestsAdapter() {
        super(R.layout.item_live_sponsor_guest_choose);
    }

    @Override
    protected void convert(final BaseViewHolder baseViewHolder, ActivitySponsorBean.GuestsBean item) {

        CheckBox checkBox = baseViewHolder.getView(R.id.checkbox);
        TextView name = baseViewHolder.getView(R.id.sponsor_name);
        name.setText(item.getMemberName());


        baseViewHolder.getView(R.id.root_layout).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (selectPosition >= 0) {
                    notifyItemChanged(selectPosition);
                    notifyItemChanged(baseViewHolder.getLayoutPosition());
                }
                selectPosition = baseViewHolder.getLayoutPosition();
            }
        });

        if (selectPosition == baseViewHolder.getLayoutPosition()) {
            checkBox.setChecked(true);
            name.setTextColor(ContextCompat.getColor(mContext, R.color.main_color));
        } else {
            checkBox.setChecked(false);
            name.setTextColor(ContextCompat.getColor(mContext, R.color.color_666666));
        }
    }
}
```