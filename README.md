# datepicker
xml file-
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <Button
        android:id="@+id/btnShow"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="200dp"
        android:layout_marginStart="20dp"
        android:layout_marginEnd="20dp"
        android:text="Pick Date"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
    <TextView
        android:id="@+id/txtResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="22dp"
        android:textSize="25sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/btnShow" />

</androidx.constraintlayout.widget.ConstraintLayout>

java file-
package com.example.datepicker;

import androidx.appcompat.app.AppCompatActivity;
import android.annotation.SuppressLint;
import android.app.DatePickerDialog;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import java.util.Calendar;
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        TextView textView = findViewById(R.id.txtResult);
        @SuppressLint({"MissingInflatedId", "LocalSuppress"})
        Button button = findViewById(R.id.btnShow);
        button.setOnClickListener(view -> {
            final Calendar calendar = Calendar.getInstance();
            int year = calendar.get(Calendar.YEAR);
            int month = calendar.get(Calendar.MONTH);
            int day = calendar.get(Calendar.DAY_OF_MONTH);
            DatePickerDialog dialog = new DatePickerDialog(MainActivity.this, (datePicker, year1, month1, day1) ->
                    textView.setText(day1 + "-" + (month1 + 1) + "-" + year1), year, month, day);
            dialog.show();
        });

    }
}
