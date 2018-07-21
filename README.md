# Professional-JavaScript-for-Web-Developers 

# 一、JS简介
JavaScript是不同于Java的动态语言，创造之初是为了在浏览器中提供一些实现逻辑，当时网速较慢，如果一个表单输入提交后，等了几十秒才返回某个字段是必填的，则用户体验非常不佳，此时JS应运而生。
JS包含ES(ECMAScript)、DOM、BOM，ES是JS的标准规范，DOM则是一个页面中的不同标签，BOM则是页面外的一些浏览器信息，例如location中的URL信息，naviator中的浏览器信息，cookies的操作，XMLHttpRequest和MicroSoftXMLHttp等ajax对象，screen获取浏览器视窗信息等等。

# 二、在HTML中使用JS
在html中使用JS，可以在页面中使用script标签，可以直接在页面中静态写死，也可以在JS中异步插入。一般会把script标签放在页面底部，因为页面在解析过程中如果遇到script标签，会停止解析，然后去执行script标签中的JS，如果是引入外部文件，那么就会等到文件下载完成后才继续解析，如果script引入的文件过大或者内容过多，那么会造成浏览器长时间空白，用户体验不佳。
script标签有两个属性比较重要，分别是defer(延迟加载)和async(异步)，如果有defer属性，那么脚本会在HTML文档完全呈现之后才执行，而且会按照指定它们的顺序，并且先于DOMContentLoaded执行(规范要求，但实际不保证)。如果有async属性表示当前脚本不会阻塞HTML文档的呈现，也不必等待其他脚本，但是不能保证脚本会按照在页面出现的顺序执行。注意异步脚本不要在加载期间修改DOM，因为不保证在DOMContentLoaded事件触发之后执行，但能保证会在load事件触发之前执行。
一般会采取外部引入文件的形式加载脚本，这样的好处是可维护和可缓存。

# 三、基本概念

# 四、变量、作用域及内存问题
JS中的变量分为基本类型和引用类型，基本类型有undefined、null、number、string、boolen，ES6中的symbol，引用类型就是对象，而函数，数组，正则都是对象。
typeof操作符可以返回变量的类型，其中会将null返回object，所以一般判定类型都会使用Object.propotype.toString.call()，会返回"[object XXXX]"，XXX为对应类型的名称。
想要获得函数的参数情况，可以在内部使用arguments进行获取，它是一个类似数组的变量，可以使用[].slice.call()，将其中的值复制出来。函数传参的时候，如果参数是基本类型，那么会是值复制的形式处理，如果是对象，那么复制的值就是对象的地址，也就是指向堆中的指针，这两种方式都会在函数内部生成一个变量去储存，也即是局部对象。
