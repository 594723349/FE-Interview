# Vue and Ts

```javascript
import ClassComponent from 'vue-class-component'

ClassComponent.registerHooks([
  'beforeRouteEnter',
  'beforeRouteUpdate'
])

beforeRouteUpdate(to: any, from: any, next: any) {
    console.log(44444444444);
    if (from.name === 'clientResourceAudit') {
      console.log(111111111);
      this.isShowEdit = true;
    } else if (from.name === 'serviceList') {
      console.log(22222222);
      this.isShowEdit = false;
    }
    console.log(this.isShowEdit);
    next()
  }
```

- github 地址
