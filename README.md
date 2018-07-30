## 小程序 - Modal
> 模态对话框，对微信开发能力做了集成(基于mpvue框架)。

### 概述

鉴于微信小程序对授权接口以及开放能力进行的调整，目前都需要通过`<button open-type="xxxx">`引导用户主动进行授权操作。同时日常开发中许多产品需求需要通过modal框来完成微信开放能力授权的步骤，如以下场景：

> - 引导用户到小程序客服发送指定内容来获取详细信息。
> 
> ![](http://os9glxm8s.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-07-30%20%E4%B8%8A%E5%8D%889.40.59.png)
> 
> - 部分小程序必须在用户授权后才能正常使用，在用户取消授权后弹出modal二次确认，提供授权入口
> 
> ![](http://os9glxm8s.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-07-30%20%E4%B8%8A%E5%8D%889.39.18.png)
> 
> - 定位授权在用户第一次拒绝后需要在小程序设置里手动打开
> 
> ![](http://os9glxm8s.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-07-30%20%E4%B8%8A%E5%8D%889.41.54.png)
> 
> ······




**API** ： 


| 属性名 | 类型 | 默认值 | 必填 | 说明 |
| ------------- | ------------- | -------- | ------ | ------ |
| visible | Boolean | 无 | 是 | 对话框是否可见 |
| openType | String | 无 | 否 | 微信开放能力，支持getPhoneNumber、contact、getUserInfo、openSetting |
| title |  String | 无 | 否 | 提示的标题 |
| content | String | 无 | 是 | 提示的内容 |
| showCancel | Boolean | true | 否 | 是否显示取消按钮 |
| cancelText | String | 取消 | 否 | 取消按钮的文字，最多 4 个字符 |
| cancelColor | String | #353535 | 否 | 取消按钮的文字颜色 |
| confirmText | String | 确定 | 否 | 确定按钮的文字，最多 4 个字符 |
| confirmColor | String | #3CC51F | 否 | 确定按钮的文字颜色 |
| @close | Function | 无| 是 | 点击遮罩层或取消按钮的回调，用来关闭弹框 |
| @confirm | Function | 无 | 否 | 点击确定后回调，当openType传值时，用来处理授权后的回调，包括bindgetuserinfo、bindcontact、bindgetphonenumber、bindopensetting |
