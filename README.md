# Text Into Speech App Source Code In-Android-Studio

# Presenting brand new Article:
 In this article you will learn how to create Text Into Speech App in Android Studio. Just follow the steps in the Article.
More article about Android Application Development will uploaded so get in touch with the channel. So you are no more far. You can be 
developer. 

## Step 1: Creating a new project

- Open a new project.
- We will be working on Empty Views Activity with language as Java. Leave all other options unchanged.
- You can change the name of the project at your convenience.
- There will be two default files named activity_main.xml and MainActivity.java.

  ## Step 2: Open res -> layout ->activity_main.xml (or) main.xml and add following code:

In this step we open an XML file and add the code :-
```xml
  <?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:id="@+id/main"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    android:orientation="vertical"  
    android:padding="10dp"  
    android:background="#00796B"  
    tools:context=".MainActivity">  
  
    <EditText        android:id="@+id/edText"  
        android:layout_width="match_parent"  
        android:layout_height="250dp"  
        android:hint="Enter Your Text"  
        android:textColor="@color/white"  
        android:textSize="25sp"  
        android:padding="10dp"  
        android:textAlignment="center" />  
  
    <Button        android:id="@+id/btn"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:text="Speech"  
        android:textSize="25sp"  
        android:padding="10dp"/>  
</LinearLayout>
```
## Step 3: Open Java -> package – > MainActivity.Java and add following code:

In this step we open an Java file and add the code :-
```java
package com.rsmacademy.text2speech;  
  
import android.os.Bundle;  
import android.speech.tts.TextToSpeech;  
import android.view.View;  
import android.widget.Button;  
import android.widget.EditText;  
  
import androidx.activity.EdgeToEdge;  
import androidx.appcompat.app.AppCompatActivity;  
import androidx.core.graphics.Insets;  
import androidx.core.view.ViewCompat;  
import androidx.core.view.WindowInsetsCompat;  
  
public class MainActivity extends AppCompatActivity {  
  
    EditText edText;  
    Button btn;  
    TextToSpeech textToSpeech;  
  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        EdgeToEdge.enable(this);  
        setContentView(R.layout.activity_main);  
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {  
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());  
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);  
            return insets;  
        });  
  
  
//==============================================================  
        edText = findViewById(R.id.edText);  
        btn = findViewById(R.id.btn);  
  
  
//=============================================================  
        textToSpeech = new TextToSpeech(MainActivity.this, new TextToSpeech.OnInitListener() {  
            @Override  
            public void onInit(int status) {  
  
            }  
        });  
  
  
//============================== Step 1 =================================  
        btn.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                textToSpeech.speak("hello", TextToSpeech.QUEUE_FLUSH, null, null);  
            }  
        });  
  
  
//============================ Step 2 ================================  
        btn.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                textToSpeech.speak(""+edText.getText().toString(), TextToSpeech.QUEUE_FLUSH, null, null);  
            }  
        });  
  
  
//============================= Step 3 =============================================  
        btn.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                if (edText.getText().toString().length() > 0) {  
                    textToSpeech.speak("" + edText.getText().toString(), TextToSpeech.QUEUE_FLUSH, null, null);  
  
                } else {  
                    edText.setError("Please, Enter Your Text");  
                }  
            }  
        });  
  
  
  
    }  
}
```
