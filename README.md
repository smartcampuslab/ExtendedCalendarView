ScExtendedCalendarView
======================

ScExtendedCalendarView is a fork of ExtendedCalendarView, a library that permits showing a calendar with the ability to display events on days.

Usage
=====

The best way is to create a new class that extends _ExtendedCalendarView_ (because of the Generics). E.g.:

	package com.exampe.myapp;

	import android.content.Context;
	import android.util.AttributeSet;
	import com.tyczj.extendedcalendarview.ExtendedCalendarView;
	
	public class MyCalendarView extends ExtendedCalendarView<CalendarioEvent> {

		public MyCalendarView(Context context) {
			super(context);
		}
	
		public MyCalendarView(Context context, AttributeSet attrs) {
			super(context, attrs);
		}
	
		public MyCalendarView(Context context, AttributeSet attrs, int defStyle) {
			super(context, attrs, defStyle);
		}
	}

Simply declare it in your layout

	<?xml version="1.0" encoding="utf-8"?>
	<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
	    android:id="@+id/calendar_layout"
	    android:layout_width="match_parent"
	    android:layout_height="match_parent"
	    android:orientation="vertical" >
	
	    <com.example.custom.MyCalendarView
	        android:id="@+id/calendar_view"
	        android:layout_width="match_parent"
	        android:layout_height="match_parent" />
	
	</LinearLayout>
    
and get the view like you normally would

    MyCalendarView calendar = (MyCalendarView) findViewById(R.id.calendar_view);

Calendar Events source
======================

The content provider of the original library is deprecated.

You need to implement the _EventsSource_ interface and the method _getEventsByMonth(Calendar calendar)_.
The argument you need to provide is a _Calendar_ object that has to cointain the date of the month you need.

The method has to return a _SparseArray_ of collections of _Event_ objects (or an object that extends the _Event_ class). The int key of the _SparseArray_ that references to a collection is the day of the month.

After that you need to set the _EventsSource_ instantiated object using the method _setCalendarEventsSource(EventsSource eventSource)_ of the _ExtendedCalendarView_ you got as said before.

In the _Event_ you can specify the color of the event (default is gray).

Please take a look at the code of the _ExtendedCalendarView_ class for other useful methods like _setDuplicatesAvoided(Boolean duplicatesAvoided)_ or _setTodayColor(Color color)_.
