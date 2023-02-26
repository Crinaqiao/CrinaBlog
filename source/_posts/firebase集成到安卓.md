---
title: firebase集成到安卓
tags:
  - Android
  - FireBase
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=1983849
feature: false
date: 2022-10-08 16:42:16
---
# 一、添加项目
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081645705.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081646327.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081646853.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081648671.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081649409.png)

# 二、添加至安卓
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081650730.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081653438.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081654124.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081659412.png)
添加SDK这一步我按照这个文档手动添加并没有成功，最后是使用Android studio自带的工具添加成功的
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081703481.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081704201.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081705765.png)

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081706797.png)


# 三、添加埋点代码
参考CSDN文章：https://blog.csdn.net/AlpinistWang/article/details/87369279

```Java
public class MainActivity extends AppCompatActivity implements View.OnClickListener{
    private Button btnEvent;

    private FirebaseAnalytics mFirebaseAnalytics;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //初始化Firebase
        mFirebaseAnalytics = FirebaseAnalytics.getInstance(this);
        bindView();
    }

    private void bindView() {
        btnEvent = (Button) findViewById(R.id.btn_event);
        btnEvent.setOnClickListener(this);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btn_event:
                //点击进行事件上报
                Bundle bundleEvent = new Bundle();
                bundleEvent.putLong("click_time",System.currentTimeMillis());
                bundleEvent.putString("key","value");
                mFirebaseAnalytics.logEvent("click_event",bundleEvent);
                break;
        }
    }
}
```

由于事件有延迟，如果我们想立即看到效果，需要使用adb命令开启手机调试，并在FireBase后台的中使用调试视图，这样事件会在触发后的30秒内被记录。
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081712291.png)

要在手机上启用 Analytics（分析）“调试”模式，请执行以下命令行：<package_name>填入app的包名
```bash
adb shell setprop debug.firebase.analytics.app <package_name>
```
“调试”模式将保持启用状态，直至您通过执行以下命令行明确停用“调试”模式：
```bash
adb shell setprop debug.firebase.analytics.app .none.
```

# 四、ADB工具的下载安装
> 没必要下载ADB（前提是你之前有安装Android Studio），Android Studio本身就带有了，在SDK目录下找到ADB的存放路径就行，值得注意的是Android Studio 2.2以后，ADB存放路径有所改变。

- 找到adb根目录
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081718176.png)
- 把路径添加到环境变量中
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081719631.png)
- 打开命令行运行`adb` 命令查看变量是否添加成功
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081720553.png)
