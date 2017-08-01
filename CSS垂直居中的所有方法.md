# CSS垂直居中的所有方法

标签（空格分隔）： css技巧

---

## 1.利用padding垂直居中(line-height用于单行文本居中)
**不需要设置高度 ***
```
.parent {
  border: 1px solid red;
  padding: 15px 0;
}
```
> [示例](http://js.jirengu.com/jopih/7/edit?html,css,output)

## 2.利用table垂直居中（兼容IE）
**需要设置父元素高度 ***
``` html
    <table>
      <td>
      <div class="child">
          table垂直居中table垂直居中table垂直居中table垂直居中
      </div>
     </td>
    </table>
```
>[示例](http://js.jirengu.com/zipug/6/edit?html,css,output)

## 3.利用外部包裹垂直居中
**需要设置父元素高度 ***

```
  <div class="parent">
    <span class=before></span>
    <div class="child">
      外部包裹
    </div>
    <span class=after></span>
  </div>
```
用伪元素优化一下：
```
  <div class="parent">
    <div class="child">
      外部包裹
    </div>
  </div>
```
```
.parent::after{
  content: '';
  clear:both;
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}
```
> [示例](http://js.jirengu.com/wotum/5/edit)




## 4.div设置table垂直居中
**需要设置父元素高度 ***
```
<div class="table">
      <div class="td">
        <div class="child">
         div设置table
        </div>
    </div>
```
> [示例](http://js.jirengu.com/yuqeg/5/edit)

## 5.负margin垂直居中(兼容IE)
**绝对定位 ***
**需要设置父子元素高度 ***
**居中内容过多会出现溢出 ***
```
.child{
  border: 1px solid green;
  width: 300px;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-left: -150px;
  height: 100px;
  margin-top: -50px;
}
```
> [示例](http://js.jirengu.com/yahev/1/edit)

## 6.transform垂直居中
**绝对定位 ***
**需要设置父元素高度 ***
```
.child{
  border: 1px solid green;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}
```
> [示例](http://js.jirengu.com/ratip/1/edit?html,css,output)

## 7.margin:auto垂直居中(兼容IE)
**绝对定位 ***
**需要设置父子元素高度 ***
**居中内容过多会出现溢出 ***
```
.child{
  border: 1px solid green;
  position: absolute;
  width: 300px;
  height: 200px;
  margin: auto;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
```
> [示例](http://js.jirengu.com/fuheq/2/edit)

## 8.flex垂直居中(除IE外都兼容)
**CSS3解决方案 ***
**需要设置父元素高度 ***
**真简单~ ***
```
.parent{
  height: 600px;
  border: 3px solid red;
  display: flex;
  justify-content: center;
  align-items: center;
}
```
> [示例](http://js.jirengu.com/qorop/2/edit)


