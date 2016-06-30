# Titanium 知识点

## 打开另外一个应用，如果没有安装，提示下载
```javascript
if(OS_ANDROID) {
	try{
	    var intent = Ti.Android.createIntent({
	    	className: "com.ishang.fetalmovement.activity.SplashActivity",
		    packageName: "com.ishang.fetalmovement"
		});
		Ti.Android.currentActivity.startActivity(intent);
	} catch(e) {
		Ti.API.info("未安装胎动点点，跳转至下载页");
		Utils.openWindowNoIndex(Alloy.createController("download_babymove").getView());
	}
} else {
	var can =  Titanium.Platform.canOpenURL("babymove://");
	if(can){
		Titanium.Platform.openURL("babymove://");
	} else {
		Ti.API.info("为安装胎动点点，跳转至下载页");
		Utils.openWindowNoIndex(Alloy.createController("download_babymove").getView());
	}
}
```

## 下载其它应用，Android跳转应用市场，IOS跳转AppStore
```javascript
if(OS_ANDROID) {
    try{
		Ti.Platform.openURL("market://details?id=" + "com.ishang.fetalmovement");
	} catch(e) {
		Ti.API.info("无法打开应用市场");
	}
} else {
	Ti.Platform.openURL("https://itunes.apple.com/tw/app/tai-dong-dian-dian-zhun-ma/id1102315802?mt=8");
}
```
