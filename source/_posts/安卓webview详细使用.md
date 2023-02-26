---
title: 安卓webview详细使用
tags:
  - Android
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=189233
feature: false
date: 2022-10-08 16:06:22
---
# 这是博客园一位大佬的文章

https://www.cnblogs.com/linhaostudy/p/14617314.html

# 安卓webview监听页面是否加载成功
1. onPageStarted        开始加载
2. onPageFinished       加载完成
3. onReceivedError      加载失败
4. onReceivedSslError   加载证书错误网页失败
5. onProgressChanged    网页加载进度
6. 注意：onProgressChanged是在mWebView.setWebChromeClient中，其余几个回调是在.setWebViewClient中。

> 通常要监听网页加载失败还是成功，来做是否需要重新加载的处理或者其他处理
但是onPageFinished回调并不能代表网页加载成功了，是无法判断的，因为即使失败了也会调用onPageFinished，而且它和onError的调用顺序不固定，所以失败的判断条件有时候会出错。那么要判断的话应该在onProgressChanged中通过加载进度去判断，因为它必然是在onError调用之后才调用的，所以可以使用在onError中设置变量的方式去判断，是否走过了onError。

```Java
private boolean isWebViewloadError=false;//记录webView是否已经加载出错
mWebView.setWebChromeClient(new WebChromeClient(){
            @Override
            public void onProgressChanged(WebView view, int newProgress) {
                super.onProgressChanged(view, newProgress);
                if (newProgress == 100) {
                    //加载100%
                    Log.d(TAG, "onProgressChanged: " + "webView---100%");
                    if (!isWebViewloadError && View.VISIBLE == btnRetry.getVisibility()){
                        btnRetry.setVisibility(View.GONE);//重新加载按钮
                    }
                }
            }
        });
 
mWebView.setWebViewClient(new WebViewClient(){
            @Override
            public void onPageStarted(WebView view, String url, Bitmap favicon) {
                super.onPageStarted(view, url, favicon);
            }
 
            @Override
            public void onPageFinished(WebView view, String url) {
                super.onPageFinished(view, url);
              
            }
 
            @Override
            public void onReceivedError(WebView view, WebResourceRequest request, WebResourceError error) {
                super.onReceivedError(view, request, error);
                isWebViewloadError=true;
                btnRetry.setVisibility(View.VISIBLE);
            }
 
            @Override
            public void onReceivedSslError(WebView view, SslErrorHandler handler, SslError error) {
              /**如果是证书错误的网页，比如www.baidu123.com，在webview浏览器上打开后显示的是空白页面，是不会调用onReceivedError 的，而是调用onReceivedSslError。如果想要实现的话要super注调，因为拦截就是在super里做的。*/
//                super.onReceivedSslError(view, handler, error);
                if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP) {
                    wvSmallNewLocalRecord.getSettings()
                            .setMixedContentMode(WebSettings.MIXED_CONTENT_ALWAYS_ALLOW);
                }
                handler.proceed();
                isWebViewloadError=true;
                btnRetry.setVisibility(View.VISIBLE);
            }
 
            @Override
            public boolean shouldOverrideUrlLoading(WebView view, String url) {
                view.loadUrl(url);
                return true;
            }
        });
```