#instanceof的秘密

> instanceof 操作符检查右边的函数原型（一般来说就是指函数的prototype对象）是否存在于操作符左边的对象的原型链上。小心函数的原型可以随时发生改变

    function P () {};
	function N () {};
	P.prototype = new P() // 创建一个P实例将P的原型对象赋给N。
	var n = new N();
	
	console.log(n instanceof N) // true
	console.log(n instanceof P) // true 这里说明了 instanceof的原理

> 正因为这种情况存在， 那么我们在用instanceof做判断的时候应该注意，实例对象的原型继承的一些情况