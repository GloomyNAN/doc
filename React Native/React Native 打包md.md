---
title: React Native 打包
date: 2018-03-06 18:26:22
tags:
---

## RN命令记录
    
### 打包
   
**IOS**

```bash
rn  bundle --entry-file index.js  --platform ios --dev false --bundle-output ./ios/index.jsbundle --assets-dest ./ios/bundle
```

**Android**

```bash
rn bundle --entry-file index.js --platform android  --dev false --bundle-output ./android/app/src/main/bundle/index.android.jsbundle  --assets-dest ./android/app/src/main/res/

cd android && ./gradlew assembleRelease

#证书生成
keytool -genkey -v -keystore com-mojia-ohc-android.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
密码：mojia-ohc
```

## 常用代码记录

**异步网络请求**
1. get方式Demo

```javascript
    requestData = () => {
        (async () => {
            try {
                let response = await fetch('URL');
                let responseJson = await response.json();
                this.setState({
                    key: responseJson.key,
                })
            } catch (error) {
                console.error(error);
            }
        })();
    };
```

2. Post方式Demo


```javascript
    requestData = () => {
        (async () => {
            try {
                let response = await fetch('URL', {
                    method: 'POST',//默认get
                    //Headers可加可不加
                    // headers: {
                    //     'Accept': 'application/json',
                    //     'Content-Type': 'application/json',
                    // },
                    body: 'key1=value1&key2=value2' //只有POST才需要加body参数
                });
                let responseJson = await response.json();
                this.setState({
                     key: responseJson.key,
                })
            } catch (error) {
                console.error(error);
            }
        })();
    };
```

3.Demo3

```javascript
    fetchData = () => {
        fetch('URL')
            .then((response) => response.json())
            .then((responseJson) => {
                this.setState({
                    key: responseJson.key,
                })
            })
    };
```

