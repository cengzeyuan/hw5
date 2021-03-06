# hw5
# 数字图像处理第五次作业  
**学生姓名：曾泽源  
班级：自动化65  
学号：2160504116  
提交日期：2019/3/30**  
**摘要：**  本次报告主要记录第五次作业中的各项任务完成情况。频域滤波在图像处理领域的重要工具之一；频域滤波器主要分为高通滤波器和低通滤波器；低通滤波用于平滑、模糊、以及去除噪声；而高通滤波器则突出变化剧烈的部分，增强尖锐的细节，如边缘等，但同时也将降低图像的对比度。本次实验基于MATLAB2018a，对相应附件图片进行了频域低通滤波器（包括butterworth和Gaussian）和频域高通滤波器（包括butterworth，Gaussian，Laplace和Unmask）处理，讨论处理后图像的效果和算法的适用情况，同时比较并讨论了空域低通高通滤波（Project3）与频域低通和高通的关系。  
**关键词：** butterworth，Gaussian，Laplace，Unmask，空域低通高通滤波，频域低通高通滤波 
  
Project5：  
----------------------------------------
1频域低通滤波器：设计低通滤波器包括 butterworth and Gaussian (选择合适的半径，计算功率谱比),平滑测试图像test1和2;分析各自优缺点；  
2频域高通滤波器：设计高通滤波器包括butterworth and Gaussian，在频域增强边缘。选择半径和计算功率谱比，测试图像test3,4：分析各自优缺点；  
3其他高通滤波器：拉普拉斯和Unmask，对测试图像test3,4滤波；分析各自优缺点；  
比较并讨论空域低通高通滤波（Project3）与频域低通和高通的关系；  
按标准格式提交报告；   
  
结果讨论  
----------------------------------------   
  
## 1.  
####  butterworth低通滤波器  
二维Butterworth低通滤波器中D0表示通带的半径，n是Butter-worth的阶数（此次实验都取2），次数过大会导致振铃现象越来越明显，在2阶的时候振铃很微小。  
**结果展示：**  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.1.jpg)   
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.2.jpg)   
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.3.jpg)   
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.4.jpg)   
**结果分析：**  
首先可以清楚的得知Butterworth低通滤波器能够达到平滑、模糊图像的处理，也能在一定的程度上对一些特定噪音进行处理；  
截止频率的选择，决定了滤波的效果，当截止频率越小，图像处理后越模糊，通过的功率在总功率中的占比也更小。  
#### gaussian低通滤波器  
二维gaussian低通滤波器中D(u , v)表示高斯曲线的拓展程度，D0则是低通滤波器的截至频率，由于gaussian低通滤波器的傅里叶反变换也是高斯的，故而通过变换和反变换后得到的空间gaussian滤波器将没有振铃效应。  
**结果展示：**  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.5.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.6.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.7.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/1.8.jpg)  
**结果分析：**  
首先可以清楚的得知gaussian低通滤波器能够达到平滑、模糊图像的处理，也能在一定的程度上对一些特定噪音进行处理；  
其次也和Butterworth低通滤波器相仿，截止频率的选择，决定了滤波的效果，当截止频率越小，图像处理后越模糊，通过的功率在总功率中的占比也更小。  
**对比：**  
通过两个滤波器的对比我们可以发现两个滤波器对图像处理的基本效果是一致的，但是在同样通带的选择下，由于过渡带的差异，得到的功率谱并不相同（相同截止频率D0下，Butterworth低通滤波器功率谱相较更大），最后图像的显示效果也有一定的差异。 
  
## 2.  
####  butterworth高通滤波器  
Butterworth高通滤波器中D0表示截止频率到原点的距离，N表示BHPF的阶数，只需在Butterworth低通滤波器的基础之上，修改滤波器函数H，其余操作不变。  
**结果展示：**   
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.1.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.2.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.3.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.4.jpg)  
**结果分析：**  
对比每组原图和处理之后图像结果，可以清晰的知道高通滤波器和低通滤波器效果上的差别，高通滤波器增强的是图像的边缘，滤除了低频分量，保留变化剧烈的高频分量。
滤波半径的选择在很大程度上影响了滤波的效果，半径越小，提取出来的边缘越明显；当半径过大时，可能会出现将边缘也一同滤除的“错误”。而随着半径的增大，功率谱变小，即滤波后包含的高频分量越来越少，与低通滤波器刚好相反。  
####  gaussian高通滤波器  
Gaussian高通滤波器实际上是在其低通滤波器的基础上做一个简单的数学变换。其中同样的D0表示了高斯曲线的拓展程度；同样由于高斯滤波器在Fourier变换和反变换上的特殊性，得到的高斯空间滤波器没有振铃效应。在之前Gaussian低通滤波器的基础上修正滤波模板H；其余操作不变。  
**结果展示：**  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.5.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.6.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.7.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/2.8.jpg)  
**结果分析：**  
同样的，对比每组原图和处理后的图像结果，可以清晰的知道高通滤波器和低通滤波器效果上的差别，高通滤波器增强的是图像的边缘，滤除了低频分量，保留变化剧烈的高频分量。
同时，滤波半径的选择在很大程度上影响了滤波的效果，半径越小，提取出来的边缘越明显；当半径过大，甚至可能将边缘也以同滤除。而随着半径的增大，功率谱变小，即滤波后包含的高频分量越来越少，与低通滤波器刚好相反。  
**对比：**  
对比两种高通滤波器的效果，可以知道两种滤波器达到的基本效果是一致的，都可以增强图像边缘，滤除低通分量，保留高频分量，但在相同的截止频率得到的滤波器功率谱由于滤波器在过度边缘的差异，有所区别。对比功率谱可知，在相同半径的情况下，Butterworth高通滤波器功率谱更大，即保留的高频信息更多。  
  
## 3.  
####  Laplace高通滤波器  
Laplace高通滤波器实际上是在其低通滤波器的基础上做一个简单的数学变换。在之前的算法框架面前改变滤波模板H即可；  
**结果展示：**  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.1.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.2.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.3.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.4.jpg)  
**结果分析：**  
对比每组图像处理结果中的原始图像和滤波后的图像，可以看到滤波器的边缘增强效果。   
由于Laplace高通滤波器将原始图像完全加回滤波后的结果，虽然解决了Butterworth滤波器和Gaussian滤波器出去傅里叶变换0频率分量的问题，使背景的强度和亮度都增加，但是同时也会引入噪声干扰，使图像出现一定程度上的失真。  
####  Unmask高通滤波器  
Unmask高通滤波器将原图像减去低通滤波后的图像得到Gmask图像，再将原图像加上k倍Gmask得到边缘增强的图像，得到增强图像边缘的效果。  
**结果展示：**  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.5.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.6.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.7.jpg)  
![](https://github.com/cengzeyuan/hw5/blob/master/2160504116tow/3.8.jpg)  
**结果分析：**  
对比每组图像处理结果中的原始图像和滤波后的图像，可以看到滤波器的边缘增强效果。   
经过反锐化掩膜后图像的边缘信息相较前面三种高通滤波器会更加清晰，但同时也会带来过度锐化的问题，出现多重的轮廓。同时对于原图附带的噪音，反锐化掩模并没有抑制作用，k的倍数越大，噪音效果越明显。  
## 比较并讨论空域低通滤波高通滤波与频域低通和高通的关系  
空间域和频率域通过卷积定理相互联系，空间域和频率域的滤波器之间互为傅里叶变换；空间域的滤波是滤波器和图像之间的卷积；而频率域中的滤波则是通过频域的相乘的操作实现的；两者之间可以相互转化相互辅助；  
空域滤波主要包括平滑滤波和锐化滤波；平滑滤波的目的是消除噪声，而噪声通常对应了频率变化较大的信号，故而平滑滤波可以与低通滤波器相互转换和对应；同样的锐化滤波是要增强图像边缘，而边缘处通常是频率变化较大的信号，故而应该对应的是频率域的高通滤波器；  
在频率域中分析更为直观也容易理解；在空域中分析则对于滤波器的硬件实现更有优点；  
但是，两者在实现的技术上实际上是有一定区别的。空域滤波器技术无论使用点操作异或模板操作，每次运算都只是基于部分点像素的性质，相较更依赖于图像的局部特征；而频域滤波器技术每次运算都利用图像中所有点像素的数据（频率依赖于傅里叶变换，如果某个像素点变化，图像傅里叶变换后矩阵的每个值都可能会发生变化），具有更好的全局性，相对能更好地体现所处理的图像的整体特性。  
  
参考文献：  
----------------------------------------
[1]《数字图像处理（第三版）》Rafael C.Gonzalez、Richard E.Wodds等著；阮秋琦 阮智宇等译、电子工业出版社  
[2]CSDN，数字图像处理之低通滤波器实现原理及方法（Matlab)，  https://blog.csdn.net/qq_29721419/arti-cle/details/53142320  
[3]百度百科，频域平滑滤波， https://baike.baidu.com/item/频域平滑滤波/7247903?fr=aladdin   
[4]cnblogs，数字图像处理-频域滤波-高通/低通滤波，https://www.cnblogs.com/laumians-notes/p/8592968.html  
