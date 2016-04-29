# Requirejs 支持的配置项

## baseUrl

所有模块的查找路径。

```js
<script src="scripts/require.js"></script>
<script>
  require.config({
    baseUrl: "/another/path",
    paths: {
        "some": "some/v1.0"
    },
    waitSeconds: 15
  });
  require( ["some/module", "my/module", "a.js", "b.js"],
    function(someModule,    myModule) {
        //This function will be called when all the dependencies
        //listed above are loaded. Note that this function could
        //be called before the page is loaded.
        //This callback is optional.
    }
  );
</script>
```

所以上面的示例中, `my/module`的标签src值是`/another/path/my/module.js`。当加载纯.js文件(依赖字串以/开头，或者以.js结尾，或者含有协议)，不会使用baseUrl。因此a.js及b.js都在包含上述代码段的HTML页面的同目录下加载。

如未显式设置baseUrl，则默认值是加载require.js的HTML所处的位置。如果用了data-main属性，则该路径就变成baseUrl。

baseUrl可跟require.js页面处于不同的域下，RequireJS脚本的加载是跨域的。唯一的限制是使用text! plugins加载文本内容时，这些路径应跟页面同域，至少在开发时应这样。优化工具会将text! plugin资源内联，因此在使用优化工具之后你可以使用跨域引用text! plugin资源的那些资源。

## paths

path映射那些不直接放置于baseUrl下的模块名。设置path时起始位置是相对于baseUrl的，除非该path设置以"/"开头或含有URL协议（如http:）。在上述的配置下，`some/module`的script标签src值是"/another/path/some/v1.0/module.js"。

用于模块名的path不应含有.js后缀，因为一个path有可能映射到一个目录。路径解析机制会自动在映射模块名到path时添加上.js后缀。在文本模版之类的场景中使用require.toUrl()时它也会添加合适的后缀。

在浏览器中运行时，可指定路径的备选(fallbacks)，以实现诸如首先指定了从CDN中加载，一旦CDN加载失败则从本地位置中加载这类的机制。

## shim

为那些没有使用define()来声明依赖关系、设置模块的"浏览器全局变量注入"型脚本做依赖和导出配置。


