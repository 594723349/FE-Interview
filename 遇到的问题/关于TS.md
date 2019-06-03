# 关于 TS

- 使用ElementUI遇到TS的问题Property ‘resetFields’ does not exist on type ‘Vue’

> resetFields() 并不是 Vue 的方法，而是你某个组件的方法。所以你需要把 this.$refs[formName] 显式标注为那个组件类型，比如：

```javascript

resetForm (formName) {
  (<WhateverForm>this.$refs[formName]).resetFields()

  // 或者不喜欢一堆括号的话：
  const formRef = <WhateverForm>this.$refs[formName]
  formRef.resetFields()
}

import {Form as ElForm} from 'element-ui'

const ref = <ElForm>this.$refs.ruleForm
ref.resetFields()

// 但是这种写法 eslint 不能通过  不允许有 <> 这样的尖括号

// 所以使用类型推断的写法  

const ref = (this.$refs[formName] as ElForm);
```
