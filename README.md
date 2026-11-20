# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to play and control the audio file”.
Developed by: Santhosh P
Registeration Number : 212224220088
*/
```

## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <TextView
        android:id="@+id/titleText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Audio Player"
        android:textSize="28sp"
        android:textStyle="bold"
        android:layout_marginBottom="40dp" />

    <Button
        android:id="@+id/startButton"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:text="START" />

    <Button
        android:id="@+id/pauseButton"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:text="PAUSE" />

    <Button
        android:id="@+id/stopButton"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:text="STOP" />

</LinearLayout>
```

### MainActivity.java
```
package com.example.audiofile;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.widget.Button;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    MediaPlayer mediaPlayer;

    Button startButton, pauseButton, stopButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

        startButton = findViewById(R.id.startButton);
        pauseButton = findViewById(R.id.pauseButton);
        stopButton = findViewById(R.id.stopButton);

        mediaPlayer = MediaPlayer.create(this, R.raw.song);

        startButton.setOnClickListener(v -> {

            if (!mediaPlayer.isPlaying()) {
                mediaPlayer.start();

                Toast.makeText(
                        MainActivity.this,
                        "Audio Started",
                        Toast.LENGTH_SHORT
                ).show();
            }
        });

        pauseButton.setOnClickListener(v -> {

            if (mediaPlayer.isPlaying()) {
                mediaPlayer.pause();

                Toast.makeText(
                        MainActivity.this,
                        "Audio Paused",
                        Toast.LENGTH_SHORT
                ).show();
            }
        });

        stopButton.setOnClickListener(v -> {

            if (mediaPlayer.isPlaying()) {
                mediaPlayer.stop();
            }

            mediaPlayer = MediaPlayer.create(
                    MainActivity.this,
                    R.raw.song
            );

            Toast.makeText(
                    MainActivity.this,
                    "Audio Stopped",
                    Toast.LENGTH_SHORT
            ).show();
        });
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();

        if (mediaPlayer != null) {
            mediaPlayer.release();
            mediaPlayer = null;
        }
    }
}
```

## AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Audiofile">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:windowSoftInputMode="adjustResize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## OUTPUT
<img width="1920" height="1080" alt="Screenshot (16)" src="https://github.com/user-attachments/assets/682b86c7-6de0-4257-9f1f-6e2c1f733aad" />

<img width="1920" height="1080" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/295fb1f0-aa53-45e8-a9a0-9c0c7b8430b7" />

<img width="1920" height="1080" alt="Screenshot (18)" src="https://github.com/user-attachments/assets/deec7003-87a9-4621-b2aa-de17d5c865ad" />




## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.
