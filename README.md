# TabFragmentDemo
fragment simple framework

//MainActivity

public class MainActivity extends FragmentActivity {

    public static final String key = "contentkey";
    LinearLayout linearLayout;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        linearLayout = (LinearLayout)findViewById(R.id.menu_layout);
        //根据父布局给子布局设置点击事件
        int count = linearLayout.getChildCount();



        for (int i = 0;i<count;i++) {
            linearLayout.getChildAt(i).setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    Bundle bundle = new Bundle();
                    FragmentTransaction ft = getSupportFragmentManager().beginTransaction();
                    ContentFragment contentFragment = new ContentFragment();
                    switch(v.getId()) {
                        case R.id.cd1:
                            bundle.putString(key,"菜单1");
                            break;
                        case R.id.cd2:
                            bundle.putString(key,"菜单2");
                            break;
                        case R.id.cd3:
                            bundle.putString(key,"菜单3");
                            break;
                        case R.id.cd4:
                            bundle.putString(key,"菜单4");
                            break;

                    }
                    contentFragment.setArguments(bundle);
                    ft.replace(R.id.content,contentFragment).commit();
                }
            });
        }
    }
}
