# 微信小程序API

## 设置顶部导航栏标题
```javascript
wx.setNavigationBarTitle({    // 可以动态的设置顶部导航栏标题
    title: that.data.content.title
})
```
## 加载中
```javascript
wx.showLoading({
    title: '加载中',
})
```
## 获取用户基本信息
```javascript
 wx.getUserInfo({
    success: function(res) {
    console.log(222222,res)
    }
})
```
## 发送网络请求
```javascript
wx.request({
    url: 'http://localhost:3000', //后台数据API接口地址
    // 携带的参数
    data: {
        x: '' ,
        y: ''
    },
    header: {
        'content-type': 'application/json'
    },
    success (res) {
        console.log(res.data)
    },
    fail (err) {
        console.log(err)
    }
})
```
## 获取登录凭证
```javascript
wx.login({
    success (res) {
        console.log(res.code)
        if (res.code) {
        //发起网络请求
        wx.request({
            url: 'https://test.com/onLogin',
            data: {
            code: res.code
            }
        })
        } else {
        console.log('登录失败！' + res.errMsg)
        }
    }
})
```
## 设置和取出stroage数据
```javascript
// 设置stroage
wx.setStorage({
    key: "num",
    data: 1
})
// 取出stroage
wx.getStorage({
    key: 'num',
    success (res) {
    console.log(res.data)
    }
})
```
## 弹窗
```javascript
wx.showModal({
    title: '提示',
    content: '这是一个模态弹窗',
    success (res) {
        if (res.confirm) {
        console.log('用户点击确定')
        } else if (res.cancel) {
        console.log('用户点击取消')
        }
    }
})
```