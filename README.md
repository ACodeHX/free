### 社交主页

  [GitHub](https://github.com/ACodeHX)
  
  [gitee](https://gitee.com/ACodeHX)

  
## free


mListView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
    @Override
    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
        String title = titles[position];
        String price = prices[position];
        int icon = icons[position];
        
        // 在这里显示价格和图片，可以使用Toast或者Dialog来显示
        
        // 例如使用Toast显示价格
        Toast.makeText(MainActivity.this, "价格：" + price, Toast.LENGTH_SHORT).show();
        
        // 如果您希望显示图片，可以创建一个Dialog，并在其中显示图片
        Dialog dialog = new Dialog(MainActivity.this);
        dialog.setContentView(R.layout.dialog_layout); // 创建一个自定义的Dialog布局，包含一个ImageView用于显示图片
        ImageView imageView = dialog.findViewById(R.id.dialog_image_view);
        imageView.setImageResource(icon);
        dialog.show();
    }
});
