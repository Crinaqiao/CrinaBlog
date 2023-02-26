---
title: '安卓模块冲突--Suggestion: add tools:replace=android:***'
tags:
  - Android
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=198233
feature: false
date: 2022-10-08 15:30:54
---
# 一、报错场景
> 类中创建了一个继承自Application的类，并在AndroidManifest.xml注册。编译报错，提示“Suggestion: add 'tools:replace="android:fullBackupContent"' to <application> element at AndroidManifest.xml:10:5-57:19 to override.”

# 二、解决办法
> 在AndroidManifest.xml的根标签下加上 `xmlns:tools="http://schemas.android.com/tools"`，然后在application标签下加入`tools:replace="android:name"`,`name`是当前报错的模块，例如我这里就是`fullBackupContent`报错。如下所示:

```XML
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
         xmlns:tools="http://schemas.android.com/tools"
         package="com.**">
   <application android:name="com.**.App"
                android:allowBackup="true"
                android:icon="@mipmap/app_icon"
                android:label="@string/app_name"
                android:supportsRtl="true"
                android:theme="@style/AppTheme"
                tools:replace="android:name">
   </application>
</manifest>
```