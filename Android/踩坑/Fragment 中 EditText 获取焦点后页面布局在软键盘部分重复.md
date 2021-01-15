# Fragment 中EditText 获取焦点后弹出软键盘，键盘部分布局重复

> xml 布局文件：

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="@color/m_grey_blue"
    android:focusableInTouchMode="true">

    <ScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">


            <RelativeLayout
                android:id="@+id/btnLoad"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginStart="@dimen/dimen_16dp"
                android:layout_marginTop="@dimen/dimen_16dp"
                android:layout_marginEnd="@dimen/dimen_16dp"
                android:layout_marginBottom="@dimen/dimen_16dp"
                android:background="@drawable/border_grey_1"
                android:padding="@dimen/dimen_1dp">


                <ImageView
                    android:id="@+id/ivLoad"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_horizontal"
                    android:background="@color/gray_alpha_80"
                    android:minHeight="@dimen/dimen_256dp"
                    android:scaleType="fitCenter" />

                <TextView
                    android:id="@+id/tvTip"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_alignStart="@id/ivLoad"
                    android:layout_alignTop="@+id/ivLoad"
                    android:layout_alignEnd="@+id/ivLoad"
                    android:layout_alignBottom="@+id/ivLoad"
                    android:background="@drawable/plain_btn"
                    android:backgroundTint="@color/m_grey_blue"
                    android:gravity="center"
                    android:text="@string/click_to_upload_img"
                    android:textColor="@color/m_green" />
            </RelativeLayout>

            <RelativeLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content">

                <EditText
                    android:id="@+id/etMsg"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginStart="@dimen/dimen_16dp"
                    android:layout_marginTop="@dimen/dimen_16dp"
                    android:layout_marginEnd="@dimen/dimen_16dp"
                    android:layout_marginBottom="@dimen/dimen_16dp"
                    android:background="@drawable/border_radius_4dp"
                    android:backgroundTint="@color/white"
                    android:gravity="start"
                    android:hint="@string/encrypt_msg"
                    android:maxLines="8"
                    android:minLines="7"
                    android:paddingStart="@dimen/dimen_8dp"
                    android:paddingEnd="@dimen/dimen_8dp"
                    android:paddingBottom="@dimen/dimen_16dp" />

                <TextView
                    android:id="@+id/tvCharCount"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_alignEnd="@id/etMsg"
                    android:layout_alignBottom="@id/etMsg"
                    android:layout_marginEnd="@dimen/dimen_16dp" />
            </RelativeLayout>
         </LinearLayout>
    </ScrollView>
</androidx.constraintlayout.widget.ConstraintLayout>
```

> 解决办法：

将顶级父布局，即 `androidx.constraintlayout.widget.ConstraintLayout` ，设置为

```xml
android:layout_width="match_parent"
android:layout_height="match_parent"
```

