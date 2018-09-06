---
title:  React navigation goback() and update parent state
date: 2018-06-19 14:26:49
tags:
---

You can pass a callback function as parameter when you call navigate like this:


```
 const DEMO_TOKEN = await AsyncStorage.getItem('id_token');
  if (DEMO_TOKEN === null) {
    this.props.navigation.navigate('Login', {
      onGoBack: () => this.refresh(),
    });
    return -3;
  } else {
    this.doSomething();
  }
```

And define your callback function:


```
refresh() {
  this.doSomething();
}
```

Then in your another view, before goBack, you can do this:


```
await AsyncStorage.setItem('id_token', myId);
this.props.navigation.state.params.onGoBack();
this.props.navigation.goBack();
```


