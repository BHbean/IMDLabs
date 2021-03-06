# Lab05. Implicit Intents

## Practice:

- running screen shot

  - before opening website -> after opening website
  
  <img src="./Practice/input_website.png" alt="practice_img1" style="zoom:20%;" />     <img src="./Practice/website.png" alt="practice_img2" style="zoom:20%;" />       
  
  - open location
  
    <img src="./Practice/google_map.png" alt="practice_img3" style="zoom:20%;" />
  
  - share text
  
  <img src="./Practice/share_text.png" alt="practice_img3" style="zoom:20%;" />
  
  - display URI with implicit intent receiver
  
  <img src="./Practice/input_uri.png" alt="practice_img3" style="zoom:20%;" />   <img src="./Practice/app_chooser.png" alt="practice_img3" style="zoom:20%;" />  <img src="./Practice/implicit_receiver.png" alt="practice_img3" style="zoom:20%;" />



- running video

  ![practice_video](./Practice/running.gif)



## Homework:

- running screen shot

  - before starting camera  ->  camera launched

  <img src="./Homework/camera_button.png" alt="homework_img1" style="zoom:20%;" />&nbsp;&nbsp; &nbsp; &nbsp;<img src="./Homework/using_camera.png" alt="homework_img2" style="zoom:20%;" />

  

- running video

  ![practice_video](./Homework/running.gif)



- key code

  - MainActivity.java

  ```java
  package com.example.implicitintents;
  
  import androidx.appcompat.app.AppCompatActivity;
  import androidx.core.app.ShareCompat;
  
  import android.content.Intent;
  import android.net.Uri;
  import android.os.Bundle;
  import android.provider.MediaStore;
  import android.util.Log;
  import android.view.View;
  import android.widget.EditText;
  
  public class MainActivity extends AppCompatActivity {
      private EditText mWebsiteEditText;
      private EditText mLocationEditText;
      private EditText mShareTextEditText;
  
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
          mWebsiteEditText = findViewById(R.id.website_edittext);
          mLocationEditText = findViewById(R.id.location_edittext);
          mShareTextEditText = findViewById(R.id.share_edittext);
      }
  
      public void openWebsite(View view) {
          // Get the URL text
          String url = mWebsiteEditText.getText().toString();
  
          // Parse the URI and create the intent
          Uri webpage = Uri.parse(url);
          Intent intent = new Intent(Intent.ACTION_VIEW, webpage);
  
          // Find an activity to hand the intent and start that activity
          if (intent.resolveActivity(getPackageManager()) != null){
             startActivity(intent);
          }
          else {
              Log.d("ImplicitIntents", "Can't handle this!");
          }
      }
  
      public void openLocation(View view) {
          // Get the string indicating a location. Input is not validated; it is
          // passed to the location handler intact.
          String loc = mLocationEditText.getText().toString();
  
          Uri addressUri = Uri.parse("geo:0,0?q=" + loc);
          Intent intent = new Intent(Intent.ACTION_VIEW, addressUri);
  
          if (intent.resolveActivity(getPackageManager()) != null){
              startActivity(intent);
          }
          else {
              Log.d("ImplicitIntents", "Can't handle this!");
          }
      }
  
      public void shareText(View view) {
          String txt = mShareTextEditText.getText().toString();
          String mimeType = "text/plain";
          ShareCompat.IntentBuilder
                  .from(this)
                  .setType(mimeType)
                  .setChooserTitle(R.string.share_text_with)
                  .setText(txt)
                  .startChooser();
      }
  
      public void openCamera(View view) {
          Intent intent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
          startActivity(intent);
      }
  }
  ```

  

