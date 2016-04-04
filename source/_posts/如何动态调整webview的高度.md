title: 如何动态调整webview的高度
date: 2014-03-11 11:40:31
tags: webview
---

如果你的使用webview的高度不是FILL\_PARENT而是WRAP\_CONTENT的话，你可能会发现 Android的webview存在一个问题：高度不会随内容高度动态调整。具体来说就是，当你动态改变同一个webview的加载内容或改变字体大小时，webview的高度能随内容高度变大而变大，但是内容高度变小时，不会随之变小，导致下发留下一片空片。

网上提的一些解决方法：
1，每次改变内容时都重新reload，
2，每次创建新的webview对象

但是这些方法有明显的缺陷，一是每次重新加载影响性能，再者必然导致页面刷新闪烁，影响体验。

你可能想到另一种方法：获取页面内容的高度，然后动态调整webview的layoutparam.heigh的值.

获取html content的高度需要调js:
var contentHeight = document.body.clientHeight;

实际高度像素值还需乘上webview的scale值：
LayoutParams lp = webview.getLayoutParams();
lp.height = contentHeight \* webview.getScale();
webview.setLayoutParams(lp);

存在的问题：
  如果页面包含图片的话，图片未完全加载时，获取的高度是不完整的。

  还好我们项目中html页面使用膜拜动态生成的，里面的图片尺寸也是事先知道的，不存在这个问题。 :)
