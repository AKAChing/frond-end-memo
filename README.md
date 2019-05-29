# 如何判断一个函数或构造方法是通过new运算符调用的

## new.target属性允许你检测函数或构造方法是否是通过new运算符被调用的。在通过new运算符被初始化的函数或构造方法中，new.target返回一个指向构造方法或函数的引用。在普通的函数调用中，new.target 的值是undefined。

``` javascript
  function Foo() {
    if (!new.target) throw "Foo() must be called with new";
    console.log("Foo instantiated with new");
  }

  Foo(); // throws "Foo() must be called with new"
  new Foo(); // logs "Foo instantiated with new"
```

# 多个文件的export统一放到一个文件里
``` javascript
  export * from 'path/to/multipleExportFile'
  export { default } from'path/to/exportDefaultFile' 
  export { default as xxx } from'path/to/exportDefaultFileToBeNamed' 
```