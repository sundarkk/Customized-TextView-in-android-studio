# Customized-TextView-in-android-studio


New Custome TextView Class and use scanario

Step 1

Resouce in Value folder in create:
 R>VALUES>attr.xml
 
 R>VALUES>attr.xml

<?xml version="1.0" encoding="utf-8"?>
<resources>

    <declare-styleable name="MyTextView">
        <attr name="fontName" format="string" />
    </declare-styleable>
</resources>

Step 2 

Create Class MyTv and paste below code. (You must add package name in R like(import com.sundar.R;))

import android.content.Context;
import android.content.res.TypedArray;
import android.graphics.Typeface;
import android.util.AttributeSet;
import android.util.Log;
import android.view.Gravity;
import android.view.ViewGroup;

import androidx.appcompat.widget.AppCompatTextView;

import com.sundar.R;
import com.sundar.classes.Constants;

public class MyTv extends AppCompatTextView {
    private String tag = "MTTag";

    public MyTv(Context context, AttributeSet attrs) {
        super(context, attrs);
        readAttr(context, attrs);
        if (this.getWidth() == ViewGroup.LayoutParams.WRAP_CONTENT) {
            this.setGravity(Gravity.FILL);
        }
//        this.setPadding(this.getPaddingLeft() + 1, this.getPaddingTop() + 1, this.getPaddingRight() + 1, this.getPaddingBottom() + 1);

//        this.setTypeface(Typeface.createFromAsset(context.getAssets(), Constants.appfontRegular));
    }

    private void readAttr(Context context, AttributeSet attrs) {
        TypedArray a = context.obtainStyledAttributes(attrs, R.styleable.MyTextView);

        // Read the title and set it if any
        String fontName = a.getString(R.styleable.MyTextView_fontName);
        if (fontName != null && fontName.endsWith(".ttf")) {
            // We have a attribute value and set it to proper value as you want
            this.setTypeface(Typeface.createFromAsset(context.getAssets(), fontName));
            Log.d(tag, fontName);
        } else {
            this.setTypeface(Typeface.createFromAsset(context.getAssets(), Constants.appfontRegular));
        }
        a.recycle();
    }
}


Step 3 String folder in add ttf file.

   <string name="appfontRegular">Comfortaa-Regular.ttf</string>
    <string name="appfontMedium">Comfortaa-Light.ttf</string>
    <string name="appfontBold">Comfortaa-Bold.ttf</string>
	
Step 4 Use Xml file in Texview

 <com.appcrunk.raimentz.custom_classes.MyTv
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:textSize="@dimen/_15sdp"
                    android:text="@string/woman_satin"
                    android:textColor="@color/light_sky_blue"
                    app:fontName="@string/appfontBold"/>
					
Step 5 TextView in use 
 app:fontName="@string/appfontBold"
					
					

