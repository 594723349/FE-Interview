# 关于checkbox引发的数据初始化问题

```javascript
// 初始化 每组按钮
this.list.forEach( (item: any) => {
  this.$set(this.checkedGroupRes, item.classId, []);
  // 不能及时更新到组件上  初始化会有些问题  
  // 详情见 接口资源化 AllServiceDetail （内部系统）
  // this.checkedGroupRes[item.classId] = [];
});
```

**比如说：n组循环出来的checkbox，其中每组具有全选和全不选的状态控制，这时候，初始化全选按钮的状态时，以及随着子项更改而全选跟着更改的状态时，这时候的数组或者对象都要用this.$set 触发视图更新，不可直接 checkAll[id] = false 记住！！！**
