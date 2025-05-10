## Ex.No:9 Develop a simple calculator using android studio.
## AIM:
To develop a program to develop a simple calculator in Android Studio.

## EQUIPMENTS REQUIRED:
Android Studio(Latest Version)

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Display the calculator operation in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:

"Program to print the text “calculator operation”.

Developed by:Sanjay.R
Registeration Number :212222220038

## Activity main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/resultText"
        android:layout_width="match_parent"
        android:layout_height="80dp"
        android:gravity="end|center_vertical"
        android:textSize="30sp"
        android:background="#ECECEC"
        android:text="0"
        android:padding="8dp" />

    <GridLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:columnCount="4"
        android:rowCount="5"
        android:layout_marginTop="16dp">

        <!-- Row 1 -->
        <Button android:id="@+id/btnClear" android:text="C" style="@style/CalcButton"/>
        <Button android:id="@+id/btnDivide" android:text="/" style="@style/CalcButton"/>
        <Button android:id="@+id/btnMultiply" android:text="*" style="@style/CalcButton"/>
        <Button android:id="@+id/btnDelete" android:text="DEL" style="@style/CalcButton"/>

        <!-- Row 2 -->
        <Button android:id="@+id/btn7" android:text="7" style="@style/CalcButton"/>
        <Button android:id="@+id/btn8" android:text="8" style="@style/CalcButton"/>
        <Button android:id="@+id/btn9" android:text="9" style="@style/CalcButton"/>
        <Button android:id="@+id/btnSubtract" android:text="-" style="@style/CalcButton"/>

        <!-- Row 3 -->
        <Button android:id="@+id/btn4" android:text="4" style="@style/CalcButton"/>
        <Button android:id="@+id/btn5" android:text="5" style="@style/CalcButton"/>
        <Button android:id="@+id/btn6" android:text="6" style="@style/CalcButton"/>
        <Button android:id="@+id/btnAdd" android:text="+" style="@style/CalcButton"/>

        <!-- Row 4 -->
        <Button android:id="@+id/btn1" android:text="1" style="@style/CalcButton"/>
        <Button android:id="@+id/btn2" android:text="2" style="@style/CalcButton"/>
        <Button android:id="@+id/btn3" android:text="3" style="@style/CalcButton"/>
        <Button android:id="@+id/btnEqual" android:text="=" style="@style/CalcButton"/>

        <!-- Row 5 -->
        <Button android:id="@+id/btn0" android:text="0" style="@style/CalcButton" android:layout_columnSpan="2"/>
        <Button android:id="@+id/btnDot" android:text="." style="@style/CalcButton"/>
    </GridLayout>

</LinearLayout>

```
## Main Activity.java
```
package com.example.calculator;


import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import net.objecthunter.exp4j.Expression;
import net.objecthunter.exp4j.ExpressionBuilder;

public class MainActivity extends AppCompatActivity {

    private TextView resultText;
    private StringBuilder expression;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        resultText = findViewById(R.id.resultText);
        expression = new StringBuilder();

        int[] buttonIds = {
                R.id.btn0, R.id.btn1, R.id.btn2, R.id.btn3, R.id.btn4,
                R.id.btn5, R.id.btn6, R.id.btn7, R.id.btn8, R.id.btn9,
                R.id.btnAdd, R.id.btnSubtract, R.id.btnMultiply,
                R.id.btnDivide, R.id.btnDot
        };

        View.OnClickListener listener = v -> {
            Button b = (Button) v;
            expression.append(b.getText().toString());
            resultText.setText(expression.toString());
        };

        for (int id : buttonIds) {
            findViewById(id).setOnClickListener(listener);
        }

        findViewById(R.id.btnClear).setOnClickListener(v -> {
            expression.setLength(0);
            resultText.setText("0");
        });

        findViewById(R.id.btnDelete).setOnClickListener(v -> {
            if (expression.length() > 0) {
                expression.setLength(expression.length() - 1);
                resultText.setText(expression.length() == 0 ? "0" : expression.toString());
            }
        });

        findViewById(R.id.btnEqual).setOnClickListener(v -> {
            try {
                Expression exp = new ExpressionBuilder(expression.toString()).build();
                double result = exp.evaluate();
                resultText.setText(String.valueOf(result));
                expression = new StringBuilder(String.valueOf(result));
            } catch (Exception e) {
                resultText.setText("Error");
                expression.setLength(0);
            }
        });
    }
}

```
## OUTPUT

![WhatsApp Image 2025-04-30 at 11 06 58 AM](https://github.com/user-attachments/assets/753eeeca-a21c-43dd-b004-580d429b8c6a)
![WhatsApp Image 2025-04-30 at 11 06 18 AM (1)](https://github.com/user-attachments/assets/b0cb69cc-5cb4-463a-8f24-685746d88290)
![WhatsApp Image 2025-04-30 at 11 06 18 AM](https://github.com/user-attachments/assets/b173afd8-f8c9-4d6e-96b5-896a53ed35f4)


## RESULT
Thus a Simple Android Application develop a program to create simple calculator in Android Studio is developed and executed successfully.
