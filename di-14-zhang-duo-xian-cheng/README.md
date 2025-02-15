# 第14章 多线程

利用对象，可将一个程序分割成相互独立的区域。我们通常也需要将一个程序转换成多个独立运行的子任务。

象这样的每个子任务都叫作一个“线程”（Thread）。编写程序时，可将每个线程都想象成独立运行，而且都有自己的专用CPU。一些基础机制实际会为我们自动分割CPU的时间。我们通常不必关心这些细节问题，所以多线程的代码编写是相当简便的。

这时理解一些定义对以后的学习狠有帮助。“进程”是指一种“自包容”的运行程序，有自己的地址空间。“多任务”操作系统能同时运行多个进程（程序）——但实际是由于CPU分时机制的作用，使每个进程都能循环获得自己的CPU时间片。但由于轮换速度非常快，使得所有程序好象是在“同时”运行一样。“线程”是进程内部单一的一个顺序控制流。因此，一个进程可能容纳了多个同时执行的线程。

多线程的应用范围很广。但在一般情况下，程序的一些部分同特定的事件或资源联系在一起，同时又不想为它而暂停程序其他部分的执行。这样一来，就可考虑创建一个线程，令其与那个事件或资源关联到一起，并让它独立于主程序运行。一个很好的例子便是“Quit”或“退出”按钮——我们并不希望在程序的每一部分代码中都轮询这个按钮，同时又希望该按钮能及时地作出响应（使程序看起来似乎经常都在轮询它）。事实上，多线程最主要的一个用途就是构建一个“反应灵敏”的用户界面。

