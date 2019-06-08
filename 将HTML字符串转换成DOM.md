#对DOM的一些操作
## 将HTML字符串转换为DOM元素
> **HTML字符串转DOM结构不是特别。事实上，它主要用到了一个大
家都很熟悉的工具：innerHTML属性。**
* 确保HTML字符串是合法有效的。

    const tags =/^(area|base|br|col|embed|hr|img|input|keygen|link|menuitem|meta|param|source|track|wbr)$/i; // 使用正则表达式匹配我们不需要关心的元素名
    function convert(html) {
		// 转换函数，通过使用正则表达式将自闭合标签转为“正常”形式的标签对
    	return html.replace( /(<(\w+)[^>]*?)\/>/g, (all,front, tag) => {
    		return tags.test(tag) ? all : front + "></" + tag + ">";
    	});
    }
	convert("<a/>") // "<a></a>"

- 将它包裹在任意符合浏览器规则要求的闭合标签内。
- 使用innerHTML将这串HTML插入到虚拟DOM元素（可以实文档碎片）中。
- 提取该DOM节点。

* 为了快速插入DOM节点，请使用DOM片段，因为可以在单个操作
中注入片段，从而大大减少了操作次数。

* DOM元素属性和特性，尽管挂钩，但并不总是相同！我们可以通
过使用getAttribute和setAttribute方法读取和写入DOM属性，同时也
可以使用对象属性符号方式写入DOM属性。
* 元素style属性是一个对象，它含有与元素标记中指定的样式值相对
应的属性。要获得计算后样式，需要同时考虑样式表中设置的样
式，请使用内置的getComputedStyle方法。
* 当代码对DOM进行一系列连续的读取和写入操作时，浏览器每次
都会强制重新计算布局信息，这会引起布局抖动。这进而导致Web
应用程序运行和响应速度变慢。

* 请批量处理DOM