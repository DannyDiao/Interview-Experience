# Android关键技术

##### 1、滚动嵌套机制

滚动嵌套主要用于列表嵌套等场景，主要有以下几种实现方式：

- **纯事件拦截与分发方案**
- **基于NestedScroll的方案**
  - 外部控件实现NestedScrollParent接口
  - 内部控件实现NestedScrollChild接口
- **基于CoordinatorLayout与Behavior的方案**