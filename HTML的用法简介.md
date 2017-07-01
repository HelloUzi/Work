**HTML表单用于收集用户输入，表单元素定义HTML表单，表单标签的动作属性定义在提交表单时执行的动作，方法属性规定在提交表单时所用的HTTP方法（获取或发布）**
	
	`<form acti**on="#" mothod="get/post">`
形式主要包含以下表单元素：

（1）输入元素，元素根据不同的输入属性，可以变化为多种形态：

文本单行文本输入框，例：
用户名：
`<input type="text" name="username">`


密码密码输入框，字段中的字符会被做掩码处理（显示为星号或实心圆），例：
密码：
`<input type="password" name="pwd">`


无线电单选按钮，同一组需要设置相同的名称值，单选按钮允许用户在同一组选项中选择其中之一，通过添加检查属性来定义预定义选项，例：
性别：
`<input type="radio" name="gender" value="male">男`

`<input type="radio" name="gender" value="female">女`


复选框，多选按钮，通过添加检查属性来定义预定义选项，例：

爱好：
	`<input type="checkbox" name="hobby" value="reading" checked>读书`

	`<input type="checkbox" name="hobby" value="music">音乐`

	`<input type="checkbox" name="hobby" value="photography" checked>摄影`

	`<input type="checkbox" name="hobby" value="fishing">钓鱼`

按钮普通按钮，例：

	`<input type="button" value="按钮">`


提交提交表单数据的按钮，例：

	`<input type="submit" value="提交">`

重置重置按钮，点击后清空用户填写的未提交数据，例：

	`<input type="reset" value="重置">`


更多内容参考

（2）选择元素，定义下拉列表;选项元素定义待选择的选项列表通常会把首个选项显示为被选选项，通过添加选择的属性来定义预定义选项，例：

所在城市：
	`<select name="city">`

				`<option value="shanghai">上海</option>`
				`<option value="beijing" selected>北京</option>`
				`<option value="shenzhen">深圳</option>`
		  	`</select>`

（3）textarea的元素定义多行输入字段（文本域），例：


`<textarea name="message">留言备注</textarea>`


（4）按钮元素定义可点击的按钮，例：


	`<button>点击</button>`


（5）标签标签为输入元素定义标注。它为鼠标用户改进了可用性。如果您在标签元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上.label标签的属性应当与相关元素的id属性相同，以下两种写法均可：


	`<label>用户名：<input type="text" name="username"></label>`
	`<label for="user">用户名：</label> <input type="text" name="username" id="user">`
