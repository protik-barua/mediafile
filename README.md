#design_layout
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:layout_gravity="center"
    android:weightSum="3"
    tools:context=".MainActivity">

   <ImageView
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:layout_weight="2"
       android:src="@drawable/bd">

   </ImageView>
    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:orientation="horizontal"
        android:layout_weight="1">

        <ImageButton
            android:id="@+id/playbtn_id"
            android:layout_width="198dp"
            android:layout_height="131dp"
            android:padding="2dp"
            android:layout_weight="1"
            android:layout_marginBottom="5dp"
            android:src="@drawable/play">

        </ImageButton>

        <ImageButton
            android:id="@+id/pausebtn_id"
            android:layout_margin="3dp"
            android:layout_width="219dp"
            android:layout_height="131dp"
            android:src="@drawable/pause">

        </ImageButton>
    </LinearLayout>


</LinearLayout>



#java_file
package com.example.mediaplayback;

import androidx.appcompat.app.AppCompatActivity;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.ImageButton;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {
    private ImageButton playbutton,pausebutton;
    private MediaPlayer mediaPlayer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        playbutton=(ImageButton) findViewById(R.id.playbtn_id);
        pausebutton=(ImageButton) findViewById(R.id.pausebtn_id);
        mediaPlayer=MediaPlayer.create(this,R.raw.abcd);
        playbutton.setOnClickListener(this);
        pausebutton.setOnClickListener(this);

    }

    @Override
    public void onClick(View view) {
        if (view.getId()==R.id.playbtn_id){
            if (mediaPlayer!=null){
                mediaPlayer.start();
                Toast.makeText(MainActivity.this,"played",Toast.LENGTH_SHORT).show();
            }


        }
        if (view.getId()==R.id.pausebtn_id){
            if (mediaPlayer!=null){
                mediaPlayer.pause();
                Toast.makeText(MainActivity.this,"played",Toast.LENGTH_SHORT).show();
            }

        }
    }
}
