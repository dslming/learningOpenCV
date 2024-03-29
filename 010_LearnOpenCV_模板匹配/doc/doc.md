> 感谢:https://zhaoxuhui.top/blog/2017/06/12/%E5%9F%BA%E4%BA%8EPython%E7%9A%84OpenCV%E5%9B%BE%E5%83%8F%E5%A4%84%E7%90%8614.html#%E6%A8%A1%E6%9D%BF%E5%8C%B9%E9%85%8D

### 模版匹配
模板匹配顾名思义就是给定一幅影像(模板)然后在另一幅 图像中寻找这个模板的操作。它是一种用来在一幅大图中 寻找模板图像位置的方法。在OpenCV中有cv2.matchTemplate() 函数供我们方便调用。它的工作原理与2D卷积函数一样， 将模板图像在输入图像(大图)上滑动，并且在每一个位置对 模板图像和与其对应的输入图像的子区域进行比较。返回 的结果是一个灰度图像，每一个像素值表示了此区域与模板 的匹配程度。

#### 1、步骤
1. 输入原图像(I)和模板图像(T)。在原图像中我们希望找到一块和模板匹配的区域
2. 通过将模板在原图像上滑动来寻找最匹配的区域。 这里所谓的滑动是指模板图像块一次移动一个像素(从左往右，从上往下)。 在每一个位置，都进行一次度量计算，来判断该像素对应的原图像的特定区域 与模板图像的相似度。
3. 对于模板T覆盖在I上的每个位置，把上一步计算的度量值保存在结果图像矩阵R中。 在R中每个位置都包含对应的匹配度量值。
4. 在结果图像矩阵中寻找最值(最大或最小，根据算法不同而不同)。最值所对应的像素的位置即认为是最高的匹配。 以该点为顶点，长宽和模板大小图像一样的矩阵认为是匹配区域。在OpenCV中可以用cv2.minMaxLoc()函数获得最值坐标
