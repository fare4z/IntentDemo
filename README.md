## IntentDemo

This is a simple Android application demonstrating how to use implicit intents to open a webpage.

### Steps to Implement:

1. **Create a new Android project:**
   - Open Android Studio.
   - Click on "Start a new Android Studio project".
   - Follow the prompts to set up your project with the desired settings (e.g., project name, package name, etc.).

2. **Design the layout:**
   - Open the `activity_main.xml` layout file.
   - Design your layout with an EditText for input and a button to trigger the action.

   Example layout (`activity_main.xml`):
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
      <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:app="http://schemas.android.com/apk/res-auto"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:orientation="vertical"
          tools:context=".MainActivity">
      
          <LinearLayout
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              android:layout_gravity="center"
              android:layout_marginLeft="30dp"
              android:layout_marginTop="30dp"
              android:layout_marginRight="30dp"
              android:layout_marginBottom="30dp"
              android:orientation="vertical">
      
              <TextView
                  android:id="@+id/textView"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:fontFamily="@font/akaya_telivigala"
                  android:text="Implicit Intent"
                  android:textSize="48sp" />
      
              <EditText
                  android:id="@+id/etUrl"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:layout_marginTop="20dp"
                  android:ems="10"
                  android:hint="Please enter URL"
                  android:inputType="text|textUri" />
      
              <Button
                  android:id="@+id/btnGo"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:text="Go!" />
      
              <TextView
                  android:id="@+id/textView2"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:fontFamily="@font/akaya_telivigala"
                  android:text="Explicit Intent"
                  android:textSize="48sp" />
      
              <EditText
                  android:id="@+id/etName"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:ems="10"
                  android:hint="Name"
                  android:inputType="text" />
      
              <Button
                  android:id="@+id/btnSubmit"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:text="Submit" />
      
          </LinearLayout>
      </LinearLayout>
   ```

3. **Implement the functionality in MainActivity.java:**
   - Open `MainActivity.java`.
   - Retrieve the URL from the EditText.
   - Set an OnClickListener on the button to open the webpage using an implicit intent.

   Example implementation (`MainActivity.java`):
   ```java
         package com.fare4z.intent;
         
         import androidx.appcompat.app.AppCompatActivity;
         
         import android.content.Intent;
         import android.net.Uri;
         import android.os.Bundle;
         import android.view.View;
         import android.widget.Button;
         import android.widget.EditText;
         
         public class MainActivity extends AppCompatActivity {
         
             EditText etUrl, etName;
             Button btnGo, btnSubmit;
         
             @Override
             protected void onCreate(Bundle savedInstanceState) {
                 super.onCreate(savedInstanceState);
                 setContentView(R.layout.activity_main);
         
                 etUrl = findViewById(R.id.etUrl);
                 btnGo = findViewById(R.id.btnGo);
                 etName = findViewById(R.id.etName);
                 btnSubmit = findViewById(R.id.btnSubmit);
         
         
                 btnGo.setOnClickListener(new View.OnClickListener() {
                     @Override
                     public void onClick(View v) {
         
                         String url = etUrl.getText().toString().trim();
                         if (!url.isEmpty()) {
                             Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(etUrl.getText().toString()));
                             startActivity(intent);
                         }
         
                     }
                 });
         
                 btnSubmit.setOnClickListener(new View.OnClickListener() {
                     @Override
                     public void onClick(View v) {
                         String name = etName.getText().toString();
                         Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                         intent.putExtra("key_name", name);
                         startActivity(intent);
         
   
                     }
                 });
             }
         }
   ```

4. **Test your application:**
   - Run your application on an emulator or a physical device.
   - Enter a URL in the EditText and click the "Open URL" button to open the webpage in a browser.


#### Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/fare4z/IntentDemo.git
2. Open the project in Android Studio.
3. Run the examples on an Android emulator or device.

