# maze
绘制迷宫的第一个版本，鼠标按下并移动绘制迷宫，键盘控制token的方向，通过form实现保存迷宫，以及输入名字，获取迷宫，采用的是localStorage实现的本地存储。也可以存成json文件，然后用ajax来模拟从后台获取json数据，完成存储迷宫的读取。此外，在绘制迷宫的过程中发现，应该有橡皮擦功能，否则绘制出错就要重新绘制。橡皮擦功能在后期加入。
(1)自定义墙对象，token对象，把对象存到数组中，然后统一调用他们的draw方法
``` javascript
for(var i=0;i<everything.length;i++){
  everything[i].draw();
}
```
(2)localStorage只能存储字符串，利用数组的方法完成墙的信息的存储及读取
```javascript
arr.push()向数组尾部插入元素，不生成新数组
arr.split()将字符串用特定字符分割，然后存储到数组中  字符串——数组
arr.join()将数组元素用特定符号相连，生成新的数组   数组————字符串
```
（3）获取鼠标坐标 考虑兼容性
```javascript
function getMouse(ev){
if(ev.layerX||ev.layerX==0){
  mx=ev.layerX;
  my=ev.layerY;
}
else if(ev.offsetX||ev.offsetX==0){
mx=ev.layerX;
my=ev.layerY;
}
}
```
(4)获取键盘按键
```javascript
if(event==null){
keyCode=window.event.keyCode;
else{
keyCode=event.keyCode;
}
```
(5)canvas元素是行内元素，要设置成块级元素，才能margin:auto；有效，横向居中·
(6)可以用name来取元素
```javascript
<form name='f>
  <input type='text' name='typeIn'>
  <input type='text' name='typeIn'>
</form>
document.f.typeIn------是个数组，数组元素为两个input标签
```
(7)表单自动提交，刷新页面的问题
当表单中只有一个type=text的标签时，当按下提交按钮，会发生自动刷新页面的问题，给form添加onsubmit="return false;"就可以避免自动刷新问题
(8)window.preventDefault()阻止默认行为
(9)获取焦点事件 focus
  失去焦点 blur
(10)利用obj.addEventListener('click',move,'false');事件监听来实现功能，最好不用obj.onclick=funciton(){}这种方法，onclick只能执行最后一个绑定的事件，把之前的动作都覆盖掉，而addEventListener不会。addEventListener不要绑定匿名函数，这样会解绑不掉。

