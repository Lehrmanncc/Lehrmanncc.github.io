---
title:  OpenCV 基础操作
tag: 图像处理
mathjax: true
---
## 图像上的算术运算

### 图像融合

* **图像融合即也是图像加法，但它是对每个图像乘以相应的权重，使其具有融合或透明的感觉。根据以下等式进行运算。**
  $$
  G(x)=(1-\alpha)f_1(x)+\alpha f_2(x),\quad \alpha\in[0,1]
  $$

* **f(x)可作为输入的图像，则上式可变为：**
  $$
  dst=\beta\cdot img_1+\alpha\cdot img_2+\gamma\\
  \beta+\alpha=1
  $$

* **在OpenCV中进行图像融合的函数为cv.addWeighted(img1,$\beta$,),其有四个参数**

## 阈值分割



### 固定阈值分割

- **阈值分割简单来说，即大于阈值的变成一种值，小于阈值的为另一种值**   

- 在python的cv2库中实现固定阈值分割的为**cv2.threshold()函数**。

 ```python
  import cv2 as cv
  import numpy as np
  import matplotlib.pyplot as plt
  
  img = cv.imread(r'D:\Python\image_processing\exercise\imori.jpg',0)
  ret, th1 = cv.threshold(img, 127, 255, cv.THRESH_BINARY)
  ret,th2=cv.threshold(img,127,255,cv.THRESH_BINARY_INV)
  ret,th3=cv.threshold(img,127,255,cv.THRESH_TOZERO)
  ret,th4=cv.threshold(img,127,255,cv.THRESH_TOZERO_INV)
  ret,th5=cv.threshold(img,127,255,cv.THRESH_TRUNC)
  
  titles=['Org','Binary','Binary_inv','Tozero','Tozero_inv','Trunc']
  images=[img,th1,th2,th3,th4,th5]
  
  for i in range(6):
      plt.subplot(2,3,i+1)
      plt.imshow(images[i],'gray')
      plt.title(titles[i],fontsize=16)
      plt.xticks([]),plt.yticks([])
  
  plt.show()
  
   ```

  运行结果如图所示：

  <img src="images\1.png" alt="运行结果图" style="zoom:50%;" />

  

- **cv2.threshold()函数由4个参数组成，img为传入函数的图像，127为设置的阈值大小(threshold)，255为阈值设定方式里的阈值最大值(maxval)，THRESH_BINARY为阈值设定的方式。**      

- **ret代表当前的阈值。**

- **matplotlib.pyplot中subplot(2,3,i+1)即为将窗口分为2行3列，i+1表示当前的第i+1个子图，imshow()则是对图像进行处理，它不会让图片进行显示，图像显示需要show()**

- **阈值设定有5种方法，分别为:**

  1. **THRESH_BINARY:**

  $$
  dst(x,y)=\begin{cases}
  maxval &\ if\ src(x,y)>thresh\\
  0 &\ otherwise
  \end{cases}
  $$

  ​		当原像素值大于阈值，原像素值变为maxval，除此之外为0。

  ​	2.**THRESH_BINARY_INV:**
  $$
  dst(x,y)=\begin{cases}
  0 &\ if \ src(x,y)>thresh\\
  maxval &\ otherwise
  \end{cases}
  $$
  ​		该阈值方法与上述阈值方法相反，从图像也可以观察得到。

  ​	3.**THRESH_TOZERO:**
  $$
  dst(x,y)=\begin{cases}
  src(x,y) &\ if\ src(x,y)>thresh\\
  0 &\ oherwise
  \end{cases}
  $$
  ​		当原像素值大于阈值时，原像素值保持不变，除此之外，原像素值变为0。

  ​	4.**THRESH_TOZERO_INV:**
  $$
  dst(x,y)=\begin{cases}
  0 &\ if \ src(x,y)>thresh\\
  src(x,y) &\ otherwise
  \end{cases}
  $$
  ​		该阈值方法与上述阈值方法相反。

  ​     5.**THRESH_TRUNC:**
  $$
  dst(x,y)=\begin{cases}
  threshold &\ if \ src(x,y)>thresh\\
  src(x,y) &\ otherwise
  \end{cases}
  $$
  ​		放原像素值大于阈值，则原像素值变为阈值，除此之外，原像素值保持不变。

------



### 自适应阈值分割

* 













