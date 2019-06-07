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
