# 点灯游戏介绍
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