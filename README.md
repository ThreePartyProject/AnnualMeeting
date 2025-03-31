
## 抽奖流程：

1、回车键开始抽奖\停止抽奖
2、由中奖名单页面跳转到首页
3、D键清除中奖记录

PS：滚动鼠标滚轮，可以放大或缩小球体


```js
var options={
  dragControl:false,//鼠标控制,true则鼠标点击可以拖动,不点击没效果,false则根据鼠标位置旋转
  initial:[-0.2, 0],//初始旋转,水平和垂直为数组,这个是鼠标未进行操控时的旋转
  freezeActive  :true,//设置为true以在突出显示标记时暂停移动。这个必须是在dragControl:false才有效
  maxSpeed: 0.05,//最大旋转速度,设置小一点,转的慢一点
  decel: 0.95,//鼠标离开画布时的减速率,设置0,鼠标离开就停止,设置1,鼠标离开还一直转
  frontSelect:true,//设置为true以防止在云后面选择标记。
  minSpeed:0.0,//鼠标离开画布时的最小旋转速度
  interval:20,//动画帧之间的间隔,以毫秒为单位,这个东西设置大了速度会变快,但是会卡,基本20是最好的
  minBrightness:0.1,//最远点的标签亮度(0.0-1.0)
  textColour: '#fff',//标记文本的颜色,文字颜色和大小是没法用style控制的,得在这里写
  textHeight:15,//标记文本字体的大小(以像素为单位)
  depth:1,//控制透视图(0.0-1.0),you can try 一 try,1以内好像都没啥用,建议试试2和3
  txtOpt:true,//文本优化,将文本标签转换为图像以获得更好的性能。
  reverse:true,//设置为true以反转相对于鼠标位置的移动方向。这个还是true好呀,false鼠标都追不上标签
  wheelZoom:false,//使用鼠标滚轮或滚动手势可以放大和缩小云。
  shape:'Sphere',//目前支持的是Sphere,hcylinder 或vcylinder 三种形状显示,分别是圆形,立着的卷发棒,躺着的卷发棒
  lock : 'x',//'x'只能竖着转,'y'只能横着转,但是我设置了'x'没用,只有'y'有用
  outlineMethod: 'size',//鼠标指到的元素变化类型, /outline:显示边框线(有深度),classic:显示边框线,block:改变背景颜色为边框线颜色,colour:改变颜色,颜色属性为outlineColour:'#fff',size:改变文本大小,大小属性为outlineIncrease:20,none:不突出显示
  activeCursor:'pointer',	//鼠标悬停在标签上时要使用的CSS光标类型,可选值auto | crosshair | default | pointer | move | e-resize | ne-resize | nw-resize | n-resize | se-resize | sw-resize | s-resize | w-resize | text | wait | help | progress ,太多了大家自行尝试吧
  animTiming:'Smooth'	,//与RotateTag和TagToFront函数一起使用的动画定时功能。可用的值为'Smooth' 和'Linear'.
  bgColour:'tag',//标签的背景颜色,tag是标签本身的背景颜色(即加在tags的标签中的颜色)
  bgOutline:'tag',//标签轮廓的背景颜色,tag是标签本身的背景颜色(即加在tags的标签中的颜色)
  outlineColour:'#fff',//活动标签周围的框的颜色,可选值tag:标签的颜色,tagbg:标签的背景颜色
  outlineThickness:2,//轮廓的粗细(以像素为单位)
  outlineOffset:5,//轮廓与文本的距离,以像素为单位
  bgRadius:5,//背景圆角的半径(以像素为单位)。
  centreFunc:function (){},//中心绘图函数,具体参考: https://www.goat1000.com/tagcanvas-centre.php
  centreImage:null,//在云的中心绘制的图像。使用内置的centreFunc回调函数在画布中间以全尺寸绘制图像。
  clickToFront:0,//如果设置为数字,则选中的标签将在激活之前的这么多毫秒内移到最前面。
  dragThreshold:4,//光标拖动这么多像素云才会移动
  fadeIn:1000,//标签淡入的时间
  freezeDecel:false,//设置为true时freezeActive变成减速而不是暂停
  imageAlign:'centre',//水平图像对齐,可选值centre,left,right。
  imageMode:null,//可选值null:有图片则图片,没图片则文本,image:仅显示图片,text:仅显示文本,both:文本和图像都使用该位置
  imagePadding:2,//使用imageMode“ both”时图像和文本之间的距离。
  imagePosition:'left',//当使用imageMode“ both”时,图像相对于文本的位置。可选值centre,left,right。
  imageRadius:0,//图像角的半径,以像素为单位。还支持使用必须包含在字符串中的百分比,例如'20%'。
  imageScale:1,//缩放图像的数量-默认值1使用图像在页面上显示的尺寸。如果不缩放(使用实际图像尺寸),请将其设置为null。
  imageVAlign:'middle',//垂直图像对齐方式,可选值middle,top,bottom
  maxBrightness:1.0,//云前端标签的亮度(不透明度)(0.0-1.0)。
  minTags:200,//最少标记数,如果少于这个就会重复tags的内容
  noMouse:false	,//设置为true防止任何鼠标交互。该initial选项必须用于为云设置动画,否则它将一动不动。
  noSelect:false,//	设置为true防止选择标签。
  noTagsMessage:true,//当没有可用标签时,显示“无标签”而不是空白画布。
  offsetX:0,//水平偏移云的中心(以像素为单位)
  offsetY:0,//垂直偏移云的中心(以像素为单位)	当没有可用标签时,显示“无标签”而不是空白画布。
  padding:0,//文本周围和背景内部的空间量。
  pinchZoom:false,//设置为true通过捏合触摸屏设备来启用放大和缩小云。
  outlineRadius:5,//轮廓框上的圆角半径(以像素为单位)
  padding:0,//文本周围和背景内部的空间量。
  pinchZoom:false,//设置为true通过捏合触摸屏设备来启用放大和缩小云。
  repeatTags:0,//在云中重复标签列表的次数。支持的最大值为64。此选项将覆盖该minTags选项。
  radiusX:1,//云整体倾斜的角度和方向
  radiusY:1,//云整体倾斜的角度和方向
  radiusZ:1,//云整体倾斜的角度和方向
  scrollPause:0,//滚动页面时的动画延迟(以毫秒为单位)。适用于页面上的所有TagCanvas实例。
  shuffleTags:false,//设置为true随机化标签的顺序。
  splitWidth:0,//如果大于0,则当该行长于该值时,将标签在单词边界处分成多行。行在<br>标签处自动断开。
  stretchX:1,//水平拉伸或压缩云。
  stretchY:1,//垂直拉伸或压缩云。
  textAlign:'centre',//水平对齐文本,可选值centre,left,right。
  textVAlign:'middle',//垂直对齐文本,可选值middle,top,bottom
  这后面的我基本都没用了,大家自行尝试哈
  textFont  :'Helvetica, Arial, sans-serif',//标签文本的字体系列
  pulsateTo:1.0,//脉动轮廓不透明度(0.0 - 1.0),这两个东西没搞懂,设置后也没啥变化
  pulsateTime:300,//脉搏率,以每秒的秒数为单位
  txtScale:2,//在txtOpt模式下转换为图像时文本的缩放系数。
  hideTags :false,//如果TagCanvas成功启动,则设置为true以自动隐藏标记列表元素。
  zoom:1,//调整画布中标签云的相对大小。较大的值将放大到云,较小的值将缩小。跟depth差不多,不过这个看起来舒服点
  zoomStep:0.05,//每次移动鼠标滚轮时缩放变焦量。
  zoomMax:3,//最大缩放值。
  zoomMin:0.3,//最小缩放值。
  shadow: '#fff',//每个标签后面阴影的颜色。
  shadowBlur:100,//标记阴影模糊量,以像素为单位。
  shadowOffset: [5,0],//标记阴影的X和Y偏移量,以像素为单位。
  weight:false,//设置为true以打开标签的权重。
  weightMode: 'size',//用于显示标记权重的方法。应该是尺寸,颜色或两者之一。
  weightSize:1,//用于在使用大小或两者的重量模式时调整标签大小的乘数。
  weightGradient:{0:'#f00', 0.33:'#ff0', 0.66:'#0f0', 1:'#00f'},//使用颜色权重模式或两者时,用于着色标签的颜色渐变。
  weightFrom:null,//用于获取标记权重的link属性。默认值为null表示权重取自计算出的链接字体大小。
  outlineDash:0,//行进蚂蚁的大小用于轮廓/经典高光,0表示无破折号
  outlineDashSpace:0,//行进的破折号之间的距离大小,0等于 outlineDash
  outlineDashSpeed:1,//行进蚂蚁动画的速度,0表示不移动,负号表示反向
  tooltip[3]:null,//设置工具提示显示方法：null无工具提示；native用于操作系统工具提示；div基于div的。
  tooltipClass[3]:'tctooltip',//工具提示div的类别。
  tooltipDelay[3]:300,//在显示工具提示div之前鼠标不移动时暂停的时间(以毫秒为单位)。
}
```