
# Ex.No:5 Develop a program to create a simple calculator using Android Studio.


## AIM:

To develop a program to create a simple calculator using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as `Calculativour` and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:

### MainActivity.java
```
package com.example.exp5;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText editText;
    TextView resultText;

    String value1 = "", value2 = "";
    String operator = "";

    boolean isOperatorClicked = false;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText = findViewById(R.id.editText2);
        resultText = findViewById(R.id.resultText);

        Button num1 = findViewById(R.id.num1);
        Button num2 = findViewById(R.id.num2);
        Button num3 = findViewById(R.id.num3);
        Button num4 = findViewById(R.id.num4);
        Button num5 = findViewById(R.id.num5);
        Button num6 = findViewById(R.id.num6);
        Button num7 = findViewById(R.id.num7);
        Button num8 = findViewById(R.id.num8);
        Button num9 = findViewById(R.id.num9);
        Button zero = findViewById(R.id.zero);

        Button add = findViewById(R.id.add);
        Button sub = findViewById(R.id.sub);
        Button mul = findViewById(R.id.mul);
        Button div = findViewById(R.id.div);

        Button dot = findViewById(R.id.dot);

        Button ac = findViewById(R.id.clear_text);
        Button answer = findViewById(R.id.submit);

        // Number Button Listener
        View.OnClickListener numberClick = new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                Button b = (Button) v;

                editText.append(b.getText().toString());

                if (!isOperatorClicked) {
                    value1 += b.getText().toString();
                } else {
                    value2 += b.getText().toString();
                }
            }
        };

        num1.setOnClickListener(numberClick);
        num2.setOnClickListener(numberClick);
        num3.setOnClickListener(numberClick);
        num4.setOnClickListener(numberClick);
        num5.setOnClickListener(numberClick);
        num6.setOnClickListener(numberClick);
        num7.setOnClickListener(numberClick);
        num8.setOnClickListener(numberClick);
        num9.setOnClickListener(numberClick);
        zero.setOnClickListener(numberClick);

        // Dot Button
        dot.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                editText.append(".");

                if (!isOperatorClicked) {
                    value1 += ".";
                } else {
                    value2 += ".";
                }
            }
        });

        // Operator Buttons
        add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                if (!value1.isEmpty()) {

                    operator = "+";

                    isOperatorClicked = true;

                    editText.append("+");
                }
            }
        });

        sub.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                if (!value1.isEmpty()) {

                    operator = "-";

                    isOperatorClicked = true;

                    editText.append("-");
                }
            }
        });

        mul.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                if (!value1.isEmpty()) {

                    operator = "*";

                    isOperatorClicked = true;

                    editText.append("×");
                }
            }
        });

        div.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                if (!value1.isEmpty()) {

                    operator = "/";

                    isOperatorClicked = true;

                    editText.append("÷");
                }
            }
        });

        // ANSWER Button
        answer.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                if (!value1.isEmpty() &&
                        !value2.isEmpty()) {

                    double num1 =
                            Double.parseDouble(value1);

                    double num2 =
                            Double.parseDouble(value2);

                    double result = 0;

                    switch (operator) {

                        case "+":
                            result = num1 + num2;
                            break;

                        case "-":
                            result = num1 - num2;
                            break;

                        case "*":
                            result = num1 * num2;
                            break;

                        case "/":

                            if (num2 == 0) {
                                resultText.setText("Error");
                                return;
                            }

                            result = num1 / num2;
                            break;
                    }

                    resultText.setText(
                            String.valueOf(result)
                    );
                }
            }
        });

        // AC Button
        ac.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                editText.setText("");

                resultText.setText("0");

                value1 = "";
                value2 = "";
                operator = "";

                isOperatorClicked = false;
            }
        });
    }
}
```

### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:background="#E0FBFC"
    android:padding="20dp"
    android:gravity="center_horizontal">

    <!-- Calculator Title -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="CALCULATOR APP"
        android:textSize="28sp"
        android:textStyle="bold"
        android:textColor="#005F73"
        android:layout_marginBottom="25dp"/>

    <!-- Display Section -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:background="#FFFFFF"
        android:padding="20dp"
        android:elevation="4dp"
        android:layout_marginBottom="25dp">

        <!-- Entered Value -->
        <EditText
            android:id="@+id/editText2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:textAlignment="textEnd"
            android:textSize="36sp"
            android:textStyle="bold"
            android:textColor="#005F73"
            android:hint="0"
            android:background="@null"
            android:focusable="false"/>

        <View
            android:layout_width="match_parent"
            android:layout_height="2dp"
            android:background="#CCCCCC"
            android:layout_marginTop="10dp"
            android:layout_marginBottom="10dp"/>

        <!-- Big Answer -->
        <TextView
            android:id="@+id/resultText"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="0"
            android:textAlignment="textEnd"
            android:textSize="42sp"
            android:textStyle="bold"
            android:textColor="#0A9396"/>
    </LinearLayout>

    <!-- Calculator Buttons -->
    <TableLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:stretchColumns="*">

        <!-- Row 1 -->
        <TableRow>

            <Button
                android:id="@+id/num1"
                style="@style/CalcNumButton"
                android:text="1"/>

            <Button
                android:id="@+id/num2"
                style="@style/CalcNumButton"
                android:text="2"/>

            <Button
                android:id="@+id/num3"
                style="@style/CalcNumButton"
                android:text="3"/>

            <Button
                android:id="@+id/add"
                style="@style/CalcOpButton"
                android:text="+"/>
        </TableRow>

        <!-- Row 2 -->
        <TableRow>

            <Button
                android:id="@+id/num4"
                style="@style/CalcNumButton"
                android:text="4"/>

            <Button
                android:id="@+id/num5"
                style="@style/CalcNumButton"
                android:text="5"/>

            <Button
                android:id="@+id/num6"
                style="@style/CalcNumButton"
                android:text="6"/>

            <Button
                android:id="@+id/sub"
                style="@style/CalcOpButton"
                android:text="-"/>
        </TableRow>

        <!-- Row 3 -->
        <TableRow>

            <Button
                android:id="@+id/num7"
                style="@style/CalcNumButton"
                android:text="7"/>

            <Button
                android:id="@+id/num8"
                style="@style/CalcNumButton"
                android:text="8"/>

            <Button
                android:id="@+id/num9"
                style="@style/CalcNumButton"
                android:text="9"/>

            <Button
                android:id="@+id/mul"
                style="@style/CalcOpButton"
                android:text="×"/>
        </TableRow>

        <!-- Row 4 -->
        <TableRow>

            <Button
                android:id="@+id/dot"
                style="@style/CalcOpButton"
                android:text="."/>

            <Button
                android:id="@+id/zero"
                style="@style/CalcNumButton"
                android:text="0"/>

            <Button
                android:id="@+id/clear_text"
                style="@style/CalcOpButton"
                android:text="AC"/>

            <Button
                android:id="@+id/div"
                style="@style/CalcOpButton"
                android:text="÷"/>
        </TableRow>

    </TableLayout>

    <!-- Answer Button -->
    <Button
        android:id="@+id/submit"
        style="@style/SubmitButton"
        android:text="ANSWER"
        android:layout_marginTop="20dp"/>

    <!-- Your Name -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="212223040122"
        android:textSize="18sp"
        android:textStyle="bold"
        android:textColor="#005F73"
        android:layout_marginTop="30dp"/>

</LinearLayout>
```

### styles.xml
/values.styles.xml
```
<?xml version="1.0" encoding="utf-8"?>
<resources>

    <!-- Number Buttons -->
    <style name="CalcNumButton">
        <item name="android:layout_width">70dp</item>
        <item name="android:layout_height">70dp</item>
        <item name="android:layout_margin">6dp</item>
        <item name="android:backgroundTint">#005F73</item>
        <item name="android:textColor">#FFFFFF</item>
        <item name="android:textSize">20sp</item>
        <item name="android:textStyle">bold</item>
    </style>

    <!-- Operator Buttons -->
    <style name="CalcOpButton">
        <item name="android:layout_width">70dp</item>
        <item name="android:layout_height">70dp</item>
        <item name="android:layout_margin">6dp</item>
        <item name="android:backgroundTint">#0A9396</item>
        <item name="android:textColor">#FFFFFF</item>
        <item name="android:textSize">20sp</item>
        <item name="android:textStyle">bold</item>
    </style>

    <!-- Submit Button -->
    <style name="SubmitButton">
        <item name="android:layout_width">match_parent</item>
        <item name="android:layout_height">wrap_content</item>
        <item name="android:layout_marginTop">20dp</item>
        <item name="android:backgroundTint">#005F73</item>
        <item name="android:textColor">#FFFFFF</item>
        <item name="android:textSize">18sp</item>
        <item name="android:textStyle">bold</item>
        <item name="android:paddingTop">14dp</item>
        <item name="android:paddingBottom">14dp</item>
    </style>

</resources>
```

## OUTPUT
<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/18df5b2b-4260-444a-8601-23b6146f2b48" />



## RESULT
Thus a Simple Calculator Application using Android Studio is developed and executed successfully.
