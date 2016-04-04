title: dispatchTouchEvent
tags:
---

##局部变量
1. mFirstTouchTarget，触摸链第一个target
2.

##方法
1. cancelAndClearTouchTargets(ev),取消和清除所有touch targets，
   reset the cancel next up flag.

2.

##流程
1. 如果 down 事件 ，cancelAndClearTouchTargets()
 向每个child target 分发 cancel事件
 清除整个touch 链

2. 检查是否要拦截事件
   如果是down事件或者mFirstTouchTarget不为空，则调用onInterceptTouchEvent方法
   否则(没有touch target 且不是 down 事件)均拦截

3. 检查是否cancel

4. 如果既不拦截也不cancel， newTouchTarget

5. 分发至touch targets
   若果mFirstTouchTarget为空，当做普通view处理，调用view的dispatchTouchEvent
   否则 分发至

   如果拦截，向所有target发送cancel事件



##TouchTarget
描述一个被触碰的View
是一个链表，this.next -> next touch target
通常只有一个


##总结
- firstTouchTarget 为down时触摸到的第一个可见、无动画且能消费down事件的子view
- down事件或firstTouchTarget存在时，事件都会经过oninterceptTouchEvent()
  方法，除非disallowIntercept。
- 如果 intertcept down 为true 则 或者没有firstTouchTarget，事件都会走普通view的分发函数
- 如果有子view处理了down事件，所有后续event都会直接分发给它。
