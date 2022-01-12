# لیستفیو و ناردنی داتا لە ئەندڕۆید ستۆدیۆ
دروستکردنی لیستفیو و ناردنی هەموو داتاکان بۆ یەک پەیج لە ئەندڕۆید ستۆدیۆ (جافا)

# سەرەتا با باسێکی پڕۆژەکە بکەین
سەرەتا 2 پەیجمان هەیە MainActivity لەگەڵ Page2 ، وە پەیجی سەرەکی ئێمە MainActivityیە و ئێمە لەو پەیجەlistviewێکمان داناوە وە ئەو listviewەش 4 بەشمان بۆی داناوە ، بەشەکان بریتین لە

<div align="right">

<ul>
  <li>ئەوە یەکەم</li>
    <ul>
       <li>ئەوە زانیاری یەکەم</li>
    </ul>
  
  <li>ئەوە دووەم</li>
    <ul>
       <li>ئەوە زانیاری دووەم</li>
    </ul>
  
  <li>ئەوە سێیەم</li>
    <ul>
       <li>ئەوە زانیاری سێیەم</li>
    </ul>
  
  <li>ئەوە چوارەم</li>
    <ul>
       <li>ئەوە زانیاری چوارەم</li>
    </ul>
</ul>
  

بەو جۆرە
<br>
<a href="https://imgbb.com/">
  <img src="https://i.ibb.co/x3JDYZC/yakam.png" alt="yakam" border="0">
</a>

تۆ ئەگەر بێت و کلیک لە هەر یەکێکیان بکەیت ئەوا زانیاری ئەو بەشەت لە پەیجی دووەم پێ نیشان دەدات
<br>
  
 <div style="display:flex;" align="right" dir="rtl">
   <a href="https://imgbb.com/"><img src="https://i.ibb.co/pP0X5VY/dwam.png" alt="dwam" border="0"></a>
   <a href="https://imgbb.com/"><img src="https://i.ibb.co/8zjyyJC/dwamm.png" alt="seyam" border="0"></a>
   </div
واتا ئەوە نیە بۆ هەر یەکێک لەو بەشەنا پەیجێکی ترمان دروست کردبێ ، هەمووی ئەچێتەوە ناو یەک پەیج کە کاتێ کلیکی لێ ئەکەیت
  
   <br>
   # چۆنیەتی دروستکردنی پڕۆژەکە
  سەرەتا لە بەشی xml لە MainActivity جۆرەکە بکە بە RelativeLayout و دواتر listviewێک دروست بکە بەم جۆرە
   <br>
    
 <div align="left" dir="ltr">
   ```
   <?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/listview"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" 
        />

</RelativeLayout>

   </div>
  <br>
   وە دواتر پەیجێکی نوێ دروست بکە بەو ڕێگەیە
  <br>
   کلیکی لای ڕاست لەسەر app بکە دواتر new دواتر Activity دواتر Empty Project و دواتر لە Activity Name و Layout Name ناوی پەیجەکەت بنووسە کە من دەنووسم Page2
   <br>
   دواتر لە بەشی کۆد نووسینی جافا بۆ MainActivity ئەمانە ئیمپۆرت بکە 
   <div align="left" dir="ltr">
package com.listview; <br>
import androidx.appcompat.app.AppCompatActivity; <br>
import android.content.Intent; <br>
import android.os.Bundle; <br>
import android.view.View; <br>
import android.widget.AdapterView; <br>
import android.widget.ArrayAdapter;  <br>
import android.widget.ListView;   <br>
import java.util.ArrayList;   <br>
import java.util.List;  
   </div>

   <br>
   وە ئەوانە دابنێ
 <div align="left" dir="ltr">
  

        // سەرەتا ناساندنی لیستفیوەکەی دروستمان کرد
        ListView listView = findViewById(R.id.listview);

        // دانانی ئایتمەکان بۆ لیستفیوەکە
        List<String> list = new ArrayList<>();
        list.add("ئەوە یەکەم");
        list.add("ئەوە دووەم");
        list.add("ئەوە سێیەم");
        list.add("ئەوە چوارەم");

        // ئەرەی ئەداپتەرێک دادەنێین بۆ ناساندنی لیست ئایتمەکان
        ArrayAdapter arrayAdapter = new ArrayAdapter(
                getApplicationContext(),
                android.R.layout.simple_list_item_1,
                list
        );

        // ئێستا ئەداپتەرەکەی ناساندمان دەیکەینە ناو لیستفیو
        listView.setAdapter(arrayAdapter);

        // وە بە ئۆن کلیک ئەوە کاتەک کلیک لە ئایتمەکان دەکەین ڕوداوەک ڕووبدە دایدەنێین
        listView.setOnItemClickListener(new AdapterView.OnItemClickListener(){
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                 // بە ئیف پۆزەشنەکە دیاری دەکەین گەر ئایتمی یەکەم کلیکی لەسەر کرا چ ڕوودەدا
                if (position == 0){
                     // ئەوەیان بۆ ئەوەیە پەیجەکە دیاری بکەیت
                    Intent i = new Intent(MainActivity.this, Page2.class);
                     // ئەوە بۆ ناردنی داتاکەیە
                    i.putExtra("babat","ئەوە زانیاری یەکەم");
                     // ئەوەش بۆ ڕۆشتن بۆ ئەو پەیجەیە کە دیاریمان کردووە
                    startActivity(i);

                } else if(position == 1){
                    Intent i = new Intent(MainActivity.this, Page2.class);
                    i.putExtra("babat","ئەوە زانیاری دووەم");
                    startActivity(i);

                } else if(position == 2){
                    Intent i = new Intent(MainActivity.this, Page2.class);
                    i.putExtra("babat","ئەوە زانیاری سێیەم");
                    startActivity(i);
                } else{
                    Intent i = new Intent(MainActivity.this, Page2.class);
                    i.putExtra("babat","ئەوە زانیاری چوارەم");
                    startActivity(i);
                }
            }
        });
  </div>
<div align="right" dir="rtl">
ئێستا لە xmlی پەیجی دووەم تێکست فیوەک دابنێ یان بنووسە
<div align="left" dir="ltr">
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".Page2">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="بابەتەکان"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</div>
وە لە بەشی کۆدی جافا لە پەیجی دووەم ئەمە ئیمپۆرت بکە
   <div align="left" dir="ltr">
     package com.listview; <br>
import androidx.appcompat.app.AppCompatActivity; <br>
import android.os.Bundle; <br>
import android.widget.TextView;  
   </div>
   وە بنووسە
    <div align="left" dir="ltr">
  
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.page2);

        
        // بۆ ناساندنی تێکست فیووەکە
        TextView textView = findViewById(R.id.textView);

        // بۆ وەرگرتنەوەی داتاکان
        Bundle extras = getIntent().getExtras();
        if (extras != null) {
            textView.setText(extras.getString("babat"));
        }

    }
      
   </div>
   
   بە هیوای سەرکەوتن
   <br>
   <a href="https://www.mediafire.com/file/pfurbxulwur9meg/listview.rar/file">سۆرس کۆدی پڕۆژەکە</a>
   <br>
   برای بچووکتان - دانا شێرزاد
</div>
   
   
