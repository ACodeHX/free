### 社交主页

  [GitHub](https://github.com/ACodeHX)
  
  [gitee](https://gitee.com/ACodeHX)

  
## free


package com.example.text;

import android.app.Activity;
import android.app.Dialog;
import android.os.Bundle;
import android.view.View;
import android.view.ViewGroup;
import android.widget.AdapterView;
import android.widget.BaseAdapter;
import android.widget.ImageView;
import android.widget.ListView;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends Activity {
    private ListView mListView;
    private String[] titles = {"桌子", "苹果", "蛋糕", "线衣", "猕猴桃", "围巾"};
    private String[] prices = {"1800元", "10元/kg", "300元", "350元", "10/kg", "280元"};
    private int[] icons = {R.drawable.table, R.drawable.apple, R.drawable.cake, R.drawable.wireclothes, R.drawable.kiwifruit, R.drawable.scarf};

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        mListView = findViewById(R.id.list_view);
        MyBaseAdapter mAdapter = new MyBaseAdapter();
        mListView.setAdapter(mAdapter);
        
        mListView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                String title = titles[position];
                String price = prices[position];
                int icon = icons[position];
                
                // 显示价格
                Toast.makeText(MainActivity.this, "价格：" + price, Toast.LENGTH_SHORT).show();
                
                // 显示图片
                showImageDialog(icon);
            }
        });
    }

    private void showImageDialog(int icon) {
        Dialog dialog = new Dialog(MainActivity.this);
        dialog.setContentView(R.layout.dialog_layout); // 创建一个自定义的Dialog布局，包含一个ImageView用于显示图片
        ImageView imageView = dialog.findViewById(R.id.dialog_image_view);
        imageView.setImageResource(icon);
        dialog.show();
    }

    class MyBaseAdapter extends BaseAdapter {
        @Override
        public int getCount() {
            return titles.length;
        }

        @Override
        public Object getItem(int position) {
            return titles[position];
        }

        @Override
        public long getItemId(int position) {
            return position;
        }

        @Override
        public View getView(int position, View convertView, ViewGroup parent) {
            View view = View.inflate(MainActivity.this, R.layout.list_item, null);
            TextView title = view.findViewById(R.id.title);
            TextView price = view.findViewById(R.id.price);
            ImageView iv = view.findViewById(R.id.iv);
            title.setText(titles[position]);
            price.setText(prices[position]);
            iv.setImageResource(icons[position]);
            return view;
        }
    }
}
