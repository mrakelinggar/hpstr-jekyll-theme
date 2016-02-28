---
layout: post
title: Notifikasi Salah Input di Android
modified: 2016-02-18
tags: [Android, Java]

image:
  feature: write-a-book-DariuszSankowski.png
  credit: DariuszSankowski

---

Banyak aplikasi Android yang menggunakan View EditText untuk menerima input dari pengguna.

Entah itu untuk login, memasukkan kode verifikasi, atau mem-publish status di media sosial.

Pastinya cepat atau lambat user akan memasukkan input yang tidak benar atau kurang tepat pada aplikasi. Dan aplikasi tentunya harus memberikan suatu notifikasi kepada user apa yang salah.

Pada tutorial ini saya ingin berbagi bagaimana caranya kita bisa menampilkan notifikasi salah input sederhana pada Android menggunakan Android Studio.

<!--excerpt-->

Buat apliaksi baru di Android Studio menggunakan template **Empty Project**, terserah namanya apa, versi minimalnya berapa, dst. Untuk tutorial ini, nama aplikasi saya adalah **WrongInputEditText**, dan nama *package* saya adalah `com.training.wronginputedittext`

Pada `activity_main.xml`, masukkan kodingan ini.

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="com.training.wronginputedittext.MainActivity"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enter the username/password (admin/admin)"
        android:textSize="20sp"/>
    <EditText
        android:id="@+id/editUsername"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Username"
        android:layout_margin="10dp"
        android:textSize="20sp"/>
    <EditText
        android:id="@+id/editPass"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password"
        android:layout_margin="10dp"
        android:inputType="textPassword"
        android:textSize="20sp"/>
    <Button
        android:id="@+id/btnLogin"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Login"
        android:textColor="#fff"
        android:layout_marginLeft="10dp"
        android:layout_marginRight="10dp"
        android:layout_marginTop="20dp"
        android:background="@color/colorPrimaryDark"/>
</LinearLayout>

{% endhighlight %}

Kemudian di `MainActivity.java`, masukkan kodingan ini

{% highlight java %}

package com.training.wronginputedittext;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    Button loginBtn;
    EditText editUser;
    EditText editPass;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        loginBtn = (Button)findViewById(R.id.btnLogin);
        editUser = (EditText)findViewById(R.id.editUsername);
        editPass = (EditText)findViewById(R.id.editPass);

        loginBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if(!editUser.getText().toString().equals("admin")) {
                    editUser.setError("Username salah");
                } else {
                    editUser.setError(null);
                }
                if(!editPass.getText().toString().equals("admin")) {
                    editPass.setError("Password salah");
                } else {
                    editPass.setError(null);
                }
            }
        });
    }
}

{% endhighlight %}

Jalankan aplikasi, dan lihatlah hasilnya.

<figure class="third">
	<a href="/images/posts/2016-02-28-android-notifikasi-salah-input/android-salah-input-1.png"><img src="/images/posts/2016-02-28-android-notifikasi-salah-input/android-salah-input-1.png" alt=""/></a>
  <a href="/images/posts/2016-02-28-android-notifikasi-salah-input/android-salah-input-2.png"><img src="/images/posts/2016-02-28-android-notifikasi-salah-input/android-salah-input-2.png" alt=""/></a>
  <a href="/images/posts/2016-02-28-android-notifikasi-salah-input/android-salah-input-3.png"><img src="/images/posts/2016-02-28-android-notifikasi-salah-input/android-salah-input-3.png" alt=""/></a>
  <figcaption>Hasil Notifikasi Salah Input</figcaption>
</figure>

***

Sudah, itu saja, gampang banget kan ya? Ketika kita ingin menyampaikan pesan eror pada EditText kita cukup menggunakan perintah `setError()` dengan input parameter fungsi tersebut adalah pesan notifikasi error-nya.

Untuk menghilangkan pesan notifikasi error, kita cukup berikan `null` pada fungsi `setError`.

Gampang banget bukan?
