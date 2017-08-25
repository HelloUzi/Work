# JS相关概念

## 1.CSS和JS在网页中的放置顺序是怎样的？

	- CSS应该放在页面顶部的`<head>`标签中
		- 由于Render tree是由DOM树和CSSOM树组成的，HTML页面需要等到CSS解析完后才能完成渲染，所以CSS应放在`<head>`标签内，优先下载解析，以避免网页元素由于样式缺失造成的瞬间白页或者给用户带来闪烁感。
	- JS应该放在`<body>`的底部
		- 因为浏览器需要一个稳定的DOM树结构，而且JS中很有可能代码直接改变了DOM树结构，浏览器为了防止出现JS修改DOM树，需要重新构建DOM树的情况，所以就会阻塞其它的下载和呈现。
		- 对于图片和CSS，在加载时会并发加载，但在加载JS时会禁用并发，并且阻止其他内容的下载，所以把JS放在页面顶部会造成白屏现象
		- 如果CSS和JS都在head标签内，则应将JS放在所有CSS的后面JS的执行有可能依赖最新样式。比如，可能会有`var width=$('#id').width`，这意味着，JS代码在执行前，浏览器必须保证在此JS之前的所有CSS（无论外链还是内嵌）都已下载和解析完成。

## 2.解释白屏和FOUC

	- 白屏
		-对于IE浏览器，chrome等（css全部加载后再呈现,有可能等待长），当CSS样式表放在底部的时候，浏览器会先解析HTML部分得到DOM树，而想要页面展现需要有DOM和CSSOM组合成的渲染树，由于CSS在底部尚未加载，所以会出现白屏的现象。
		- 对于图片和CSS, 在加载时会并发加载(如一个域名下同时加载两个文件)。 但在加载 JavaScript 时，会禁用并发，并且阻止其他内容的下载. 所以把 JavaScript 放入页面顶部也会导致白屏现象。

	- FOUC无样式内容闪烁
		- 有些浏览器是边渲染边呈现，比如firefox浏览器，若CSS放置在底部，当解析出DOM树的时候它会直接先展现出来，然后再读取底部的CSS文件时，得到CSSOM树再给网页进行渲染，所以会出现样式闪烁的现象。

## 3.async和defer的作用是什么？有什么区别？

	- 作用
		- `<script src="script.js"></script>`
		没有 defer 或 async，浏览器会立即加载并执行指定的脚本，“立即”指的是在渲染该 script 标签之下的文档元素之前，也就是说不等待后续载入的文档元素，读到就加载并执行。
		- `<script async src="script.js"></script>`
		有 async，加载和渲染后续文档元素的过程将和 script.js 的加载与执行并行进行（异步）。
		- `<script defer src="myscript.js"></script>`
		有 defer，加载后续文档元素的过程将和 script.js 的加载并行进行（异步），但是 script.js 的执行要在所有元素解析完成之后，DOMContentLoaded 事件触发之前完成。

	- 区别


![Alt text](https://user-images.githubusercontent.com/29303882/28419338-34110c1c-6d91-11e7-909d-bbfd988931c4.png)

		- defer 和 async 在网络读取（下载）这块儿是一样的，都是异步的（相较于 HTML 解析）
		- 它俩的差别在于脚本下载完之后何时执行。显然 defer 是最接近我们对于应用脚本加载和执行的要求的
		- 关于 defer，它是按照加载顺序执行脚本的，这一点要善加利用
		- async 则是一个乱序执行的主，反正对它来说脚本的加载和执行是紧紧挨着的，所以不管你声明的顺序如何，只要它加载完了就会立刻执行
		- async 对于应用脚本的用处不大，因为它完全不考虑依赖（哪怕是最低级的顺序执行），不过它对于那些可以不依赖任何脚本或不被任何脚本依赖的脚本来说却是非常合适的，最典型的例子：Google Analytics

## 4.简述网页的渲染机制

![Alt text](https://user-images.githubusercontent.com/29303882/28419697-762a4b8a-6d92-11e7-9fb8-d834ce70489c.png)

	1. 解析 HTML 标签, 构建 DOM 树
	2. 解析 CSS 标签, 构建 CSSOM 树
	3. 把 DOM 和 CSSOM 组合成 渲染树 (render tree)
	4. 在渲染树的基础上进行布局, 计算每个节点的几何结构
	5. 把每个节点绘制到屏幕上 (painting)