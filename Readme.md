# 点灯游戏介绍  （U201611887）
 本游戏名为点灯游戏，在如4*4的格子中，通过鼠标点击来一次改变某一格与其上下左右的格子颜色，当玩家将所有格子颜色均涂满时则游戏胜利。
 
 其制作过程分为如下几个步骤：制作欢迎界面与结束界面等、设置鼠标左键与右键功能、判断玩家是否获得胜利。

 以下分几点加入代码进行说明。


## 初始化欢迎界面

```c++
void welcome()
{
// 初始化窗口
initgraph(640, 480);
// 输出屏幕提示
cleardevice();
settextcolor(RGB(0, 255, 0));
settextstyle(64, 0, L"华文彩云");
outtextxy(70, 50, L"点灯游戏");
settextcolor(YELLOW);
settextstyle(16, 0, L"华文彩云");
outtextxy(100, 200, L"每点一个格子，上下左右的格子也会做出于现状相反的动作");
outtextxy(100, 240, L"总共11关，左键填色，右键重来，中键退出");
settextstyle(16, 0, L"华文彩云");
// 实现闪烁的"按任意键继续"
int c = 255;
while (!_kbhit())
{
settextcolor(RGB(0, c, 0));
outtextxy(280, 400, L"按任意键继续");
c -= 8;
if (c < 0) c = 255;
Sleep(20);
}
_getch();
cleardevice();
}
```

## 鼠标左键点击

    设置鼠标左键点击时，上下左右四个格子均改变自己的颜色。

```c++

nx = (int)(m.x - grid.left) / G_length;
ny = (int)(m.y - grid.top) / G_length;
// 转换格子状态
grid.array[nx][ny] = -grid.array[nx][ny];
if (nx >= 0 && nx < num - 1) grid.array[nx + 1][ny] = -grid.array[nx + 1][ny];
if (nx > 0 && nx <= num - 1) grid.array[nx - 1][ny] = -grid.array[nx - 1][ny];
if (ny >= 0 && ny < num - 1) grid.array[nx][ny + 1] = -grid.array[nx][ny + 1];
if (ny > 0 && ny <= num - 1) grid.array[nx][ny - 1] = -grid.array[nx][ny - 1];
// 扫描填色
for (nx = 0; nx
for (ny = 0; ny
{
if (grid.array[nx][ny] == 1)
setfillcolor(GREEN);
else
setfillcolor(BLACK);

```

## 鼠标右键点击

    设置鼠标右键点击为清空所有颜色

```c++
OnRButtonDown(grid.num);
break;
case USER_MBUTTONDOWN:
return 1;
break;
}
return 0;
}
```

## 游戏判断输赢

```c++
int JudgeFull(int num, int array[MaxNum][MaxNum])
{
int c = -1;
int nx = 0, ny = 0;
while (nx > c)
{
for (nx = 0; nx++)
for (ny = 0; ny++)
if (array[nx][ny] == 1)
continue;
else
return c;
}
c = 1;
return c;
}
```

以下为示例图片

![示例图片](image/1.jpg "点灯游戏")


# **贪吃蛇小游戏介绍** （U201611893）
*等待界面*
---
运行后需等待3秒方可开始游戏
![等待界面](image/等待中.png "这是等待界面")

---
*游戏界面*
---
开始游戏之后
![游戏界面](image/游戏中.png "这是游戏界面")

---
*结束界面*  
游戏结束  
![结束界面](image/游戏结束.jpg "这是游戏结束界面")
## *游戏规则*
操控小蛇移动，控制他去吃到$果实，每吃一块果实都会使小蛇变长

---
## *积分规则*
初始等级为1，初始分数为0

每吃一块分数加100

分数累计至400时，升级为等级2

之后每增加800分，等级+1

---

## *游戏结束*
当贪吃蛇触碰边界或者触碰自己身体时，游戏结束，程序退出



# **贪吃蛇游戏**（U201611896）
**贪吃蛇游戏是一款经典的益智游戏，该游戏通过控制蛇头方向吃蛋，从而使得蛇变得越来越长。**

***

## 游戏规则
通过WASD操控Snake的上左下右的移动，目标是吃到food。
当Snake触碰到Wall或者自身时，游戏结束。

***

## 游戏界面
### *开始界面*
![gamestart](image/gamestart.png "开始界面")
    开始时Snake具有三个长度，即food=3。可以看到第一个food出现在右侧。Stage的规格是20x20。
### *结束界面*
![gameover](image/gameover.png "结束界面")
    可以看到Snake触碰到上侧的Wall，Snake死亡，游戏结束。Stage下侧出现“Game over”和分数（即food的值）

***

## 程序进度
### *已实现*
* 操作Snake移动
* 基本游戏规则
* 显示死亡画面
### *待实现*
* 选择/自调整难度
* 高级死亡画面
* 更多...


# 第一次作业 （U201611905）
## 一、暑期demo源码
```html
<html>
<head>
<script type="text/javascript">
var d=new Date()
var weekday=new Array(7)
weekday[0]="星期日"
weekday[1]="星期一"
weekday[2]="星期二"
weekday[3]="星期三"
weekday[4]="星期四"
weekday[5]="星期五"
weekday[6]="星期六"
document.write( weekday[d.getDay()])
</script>
</body>
<script type="text/javascript">
function startTime()
{
var today=new Date()
var h=today.getHours()
var m=today.getMinutes()
var s=today.getSeconds()
m=checkTime(m)
s=checkTime(s)
document.getElementById('txt').innerHTML=h+":"+m+":"+s
t=setTimeout('startTime()',500)
}
function checkTime(i)
{
if (i<10) 
  {i="0" + i}
  return i
}
</script>
</head>
<body onload="startTime()">
<div id="txt"></div>
</body>
<body>
<body background="/i/eg_background.jpg">
<h4>DEMO：</h4>
<form action="">
姓名:<br>
<input type="text" name="" value ="" size="10">
<br>
性别:<br>
<form>
男：
<input type="radio" checked="checked" name="Sex" value="male" />
<br />
女：
<input type="radio" name="Sex" value="female" />
</form>
班级:<br>
<input type="text" name=""" size="10">
</form>
<br>
学号：<br>
<input type="text" name=""" size="10">
<br>
专业:<br>
<form>
<select name="专业">
<option value="电气">电气</option>
<option value="机械">机械</option>
<option value="土木">土木</option>
<option value="建规">建规</option>
</select>
</form>
尺码：<br>
<form>
<select name="尺码">
<option value="s">s</option>
<option value="m">m</option>
<option value="l">l</option>
<option value="xl">xl</option>
<option value="2xl">2xl</option>
<option value="3xl">3xl</option>
<option value="4xl">4xl</option>
</select>
</form>
<br>
<form>
<input type="button" value="确定">
<form>
<input type="button" value="取消">
</form>
</body>
</html>
```
---
## 二、功能介绍与说明
       1.因为对微信小程序比较感兴趣，所以自学了html的一点知识，这个demo主要是一些简要的html功能。 
       2.demo的前半部分为一个时间显示，可以展示当天为星期几，并显示实时具体时间，精确到秒数。
       3.demo的后半部分相当于一个简单的信息收集功能，运用了html的几个基本框架，如输入框、下拉框、按钮等等，进入界面后可在其中输入信息或者选择相应信息。
       下面是效果图
  ![](image/xiaoguotu1.png )
 ![](image/xiaoguotu2.png )