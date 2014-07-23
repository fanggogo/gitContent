#JavaScript直接通过ID获取节点对象
###我们通常通过id获取元素的方法是document.getElementById()，殊不知可以通过节点的id名字，直接获取元素节点，看看下面的例子吧：


	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
	<html lang="en">
	<head>
		<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
		<title></title>
		<style type="text/css">
		#test {height:50px; background:green;}
		</style>
	</head>
	
	<body>
		<p id="test"></p>
	</body>
	</html>
	
	<script type="text/javascript">	
		test.style.background="yellow";	//直接获取id名字修改样式	
	</script>

###如果这样的话，获取id岂不是会很方便了，但是他的方便也会给我们带来很多的坑，所以不推荐这种不规范的编程方式，下面看看这个例子：

openid.html

	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
	<html lang="en">
	<head>
	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
	<title></title>
	<style type="text/css">
		#openid {height:100px; background:red;}
		#test {height:50px; background:green;}
	</style>
	</head>

	<body>
	<div id="openid"></div>
	<p id="test"></p>
	</body>
	</html>

	<script type="text/javascript">
		document.addEventListener("DOMContentLoaded",function (){
			var openid = document.getElementById("test");
			//恰巧我们获取id="test"时，起的名字正好是当前页面已经存在的id名字，即id="openid"
			alert("test节点"+openid);
			//弹出:test节点[object HTMLParagraphElement]		

			var oS = document.createElement("script");
			oS.src="test.js";
			var oHead=document.getElementsByTagName('head')[0];
			oHead.appendChild(oS);
		});

	</script>

openid.js

	alert("openid节点"+openid);
	//弹出:openid节点[object HTMLDivElement]
	/*由于在openid.html中var openid = document.getElementById("test");是局部变量，
	  在openid.js中的openid是获取到的id="openid"这个节点，如果没有id="openid",
	  则会报错openid is not defined */



*guofang*