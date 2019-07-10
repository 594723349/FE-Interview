# 示例

```javascript
function sleep(duration) {
        return new Promise(function(resolve, reject) {
            console.log("b");
            setTimeout(resolve,duration);
        })
    }
    console.log("a");
    sleep(2000).then(()=>console.log("c"));
    // a b c
```
