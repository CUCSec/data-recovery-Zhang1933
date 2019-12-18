# <font color=#0099ff>用Wenhex分析文件记录并恢复被删除文件</font>

## 实验开始前准备工作
在本地磁盘e里创建一个txt之后写入一些文字使文件变为非常驻属性。
![creat](/img/creat.PNG)
 删除磁盘的那个txt之后（包括回收站）。

![de](/img/delet.PNG)

## <font color=#0099ff>Let's begain!!</font>

*  打开winhex，以管理员身份运行
*  依次在上方栏点开tool>>open disk>>选择刚才所删除文件所在的盘。

  就可以发现那个被删除的文件。
  ![findit](/img/finddelet.PNG)
---
  如果没有发现就依次点击tool>>disk tools>>take new volume snapshot 刷新一下
![fresh](/img/refresh.PNG)

* 点击那个删除了的图标
* 点击鼠标右键点击navigation>>seek file record跳转到文件记录
  

  ### 开始分析
  根据老师所提供的资料:
  文件记录头的偏移列表
  ！！！注意在算偏移的时候打开程序员计算器转换成10进制。
  ![dog](/img/head.PNG)
  属性头的偏移列表
  ![goods](/img/属性头.PNG)
  常见属性-标准信息0x10
  ![dog](/img/常见属性.PNG)
  常见属性-文件名0x30
  ![dog](/img/name.PNG)  
  常见属性-数据0x80
  ![dog](/img/defult.PNG)
  （如果文件为常驻属性，0x18后面就直接是文件内容）
  然后就开始分析，注意偏移值要换算成10进制。

  ####  <font color=#0099ff>分析结果：</font>
  * 蓝色圈出来分别表示文件有
  文件名有6个字符
  
  
  * 文件实际大小就是0x160个也就是352个字符。
  ![dog](/img/anlalisy.PNG)
  * 紫色就是datarun
  文件内容占0x01个簇，文件具体开始簇的位置是0x008e。
  然后用0x008e换算10进制出来要跳转142个簇。
  最后用winhex的跳转就可跳转到对应的扇区
  ![dog](/img/gosector.PNG)
  在sector里填刚才换算的142。
  * 跳转成功
  ![dog](/img/goodgame.PNG)
  * 鼠标右键点击recover，然后选择你的路径。点击ok
  恢复成功！
  ![dog](/img/finish.PNG)

                                                         




  
