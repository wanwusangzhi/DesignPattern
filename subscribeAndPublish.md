# 发布-订阅模式

## 场景

购买者与商家，购买者订阅各产品，商家发布产品消息。
```
var publish = {};// 发布者
var subObj = {}; // 订阅者
var subcribe = []; // 订阅者

var _id = 0;

class person {
  constructor(name) {
    this.id = _id++;
    this.name = name;
    subObj[this.id] = this;
  }
  listen(fn){
    shop.listen(fn.bind(this));
  }
}

class shop {
  static listen(fn){
    subcribe.push(fn);
  }
  trigger(){
    subcribe.forEach((item)=>{
      item.apply(null, arguments)
    })
  }
}

var p1 = new person('ha1');
var p2 = new person('ha2');
p1.listen(function(color, size){
  console.log(this.name, color, size)
})
p2.listen(function(color, size){
  console.log(this.name, color, size)
})

var s = new shop();
s.trigger('red', '40' )

```