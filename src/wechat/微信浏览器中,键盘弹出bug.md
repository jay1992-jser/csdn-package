##### 复现：

```
1、ios12微信H5页面里，输入框获取焦点弹起输入法，点击空白处或点击键盘的“完成”收起键盘后，页面没有下来，底部有一片灰色空白区域。。。
2、微信IOS 6.7.4 键盘弹起页面上滑，键盘收起页面不会回到原位置，导致弹框(css设置position为fixed会有问题，absolute不会有问题)后按钮响应区域错位
```

##### 解决方案：

```
FastClick.attach(document.body)
FastClick.prototype.focus = function(targetElement) {
  let length
  // 兼容处理:在iOS7中，有一些元素（如date、datetime、month等）在setSelectionRange会出现TypeError
  // 这是因为这些元素并没有selectionStart和selectionEnd的整型数字属性，所以一旦引用就会报错，因此排除这些属性才使用setSelectionRange方法
  if (!!navigator.userAgent.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/) && targetElement.setSelectionRange && targetElement.type.indexOf('date') !== 0 && targetElement.type !== 'time' && targetElement.type !== 'month' && targetElement.type !== 'email') {
    length = targetElement.value.length
    targetElement.setSelectionRange(length, length)
    // 修复bug ios 11.3不弹出键盘，这里加上聚焦代码，让其强制聚焦弹出键盘
    targetElement.focus()
  } else {
    targetElement.focus()
  }
}
```

