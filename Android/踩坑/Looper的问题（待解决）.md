## 在 `Fragment` 中使用 `AlertDialog` 遇到的问题

```java
public static void showAlert(Context context, String msg) {
        if (context==null)return;
        AlertDialog.Builder builder = new AlertDialog.Builder(context);
        builder.setMessage(msg)
                .setNegativeButton("Close", ((dialog, which) -> {
                    dialog.cancel();
                })).show();
    }
```

如上段代码，在 `fragment`中调用时不能成功，改成如下代码时可以：

```java
public static void showAlert(Context context, String msg) {
        if (context==null)return;
    Looper.prepare();
        AlertDialog.Builder builder = new AlertDialog.Builder(context);
        builder.setMessage(msg)
                .setNegativeButton("Close", ((dialog, which) -> {
                    dialog.cancel();
                })).show();
        Looper.loop();
    }
```

但在子线程中，后续代码就停止执行了。