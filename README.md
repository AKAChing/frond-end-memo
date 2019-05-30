# 前端备忘录

## 如何判断一个函数或构造方法是通过new运算符调用的

### new.target属性允许你检测函数或构造方法是否是通过new运算符被调用的。在通过new运算符被初始化的函数或构造方法中，new.target返回一个指向构造方法或函数的引用。在普通的函数调用中，new.target 的值是undefined。

``` javascript
  function Foo() {
    if (!new.target) throw "Foo() must be called with new";
    console.log("Foo instantiated with new");
  }

  Foo(); // throws "Foo() must be called with new"
  new Foo(); // logs "Foo instantiated with new"
```

## 多个文件的export统一放到一个文件里
``` javascript
  export * from 'path/to/multipleExportFile'
  export { default } from'path/to/exportDefaultFile' 
  export { default as xxx } from'path/to/exportDefaultFileToBeNamed' 
```

## toLocalString
``` javascript
  new Date().toLocaleString() // "2019/5/30 下午2:55:48"
  new Date().toLocaleString('zh-hans-CN-u-nu-hanidec') // "二〇一九/五/三〇 下午三:〇一:〇一"
  (+ new Date()).toLocaleString({useGrouping: true}) // "1,559,199,448,703"
  (+ new Date()).toLocaleString({useGrouping: false}) // "1559199448703"
  (+ new Date()).toLocaleString('zh-hans-CN-u-nu-hanidec',{useGrouping: false}) // "一五五九一九九六〇五一八三"
```

## document.designMode
``` javascript
  document.designMode = 'on' // 开启编辑模式
  document.designMode = 'off' // 关闭编辑模式
```

## document.hidden
``` javascript
  // 表示当前标签页的显示/隐藏状态
  window.addEventListener('visibilitychange', () => {
    switch(document.visibilityState) {
      case 'prerender':
        console.log('Tab呈现之前');
        break;
      case 'hidden':
        console.log('Tab隐藏');
        break;
      case 'visible':
        console.log('Tab被聚焦');
        break;
    }
  })
```