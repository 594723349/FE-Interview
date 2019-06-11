# 错误处理try catch

```javascript
// 例如捕获后台接口报错等
try {
        const res = await dangerUserList(ops);
        if (res.code === 1) {
          const { data } = res;
          this.list = data;
        } else {
          this.$msg.error((res.error && res.error.msg) || '获取列表数据失败！');
        }
        this.loading = false;
      } catch (error) {
        this.$msg.error('获取列表数据失败！');
        this.loading = false;
      }
```
