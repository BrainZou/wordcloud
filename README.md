# wordcloud
博客地址http://blog.csdn.net/zou249014591/article/details/78270327
    看完了如何做词云的教程，试用wx聊天记录做一个demo练手。关于词云，网上有大量的教程，可随意参看，注意python的版本问题即可。
##WX聊天记录导出
用到的工具是一款wx聊天记录查看软件，分享如下，侵权则删。 
链接: https://pan.baidu.com/s/1c1EDh52 密码: 129q 
使用：需要一个root后的手机，然后导出即可，对于使用了没有root的手机可以使用wx的聊天记录转移功能，将聊天记录转移到已root的手机，记得设置为只转移文字哦，不然效率很低。 
由于我已经把记录删了，所以就不截图了，软件比较简单，自己琢磨即可。 
导出后可以查看，但是不能直接导成文本（收费），没办法，只能手动复制粘贴。然后把昵称时间什么的 ctrl+h替换一下，（20171018 20:06）可以用正则表达式\([^\)]*\)来替换哦。
##词云
ps：写demo建议使用Anaconda，挺方便。
```python
%pylab inline
import jieba
#jieba用来对中文分词
import matplotlib.pyplot as plt
from wordcloud import WordCloud
filename = "miao.txt"
#聊天记录
with open(filename,encoding='UTF-8') as f:
    mytext = f.read()
#打开文本
mytext = " ".join(jieba.cut(mytext))
photo_coloring = imread('2016.jpg')
#词云背景图片白底
wordcloud = WordCloud(background_color="white",font_path="simsun.ttf",max_words=200,mask=photo_coloring).generate(mytext)
#中文注意下载simsun.ttf中文字体来替换
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
```
##wordcloud几个参数
font_path : 使用的字体的路径 
width : int (default=400) //输出的画布宽度，默认为400像素 
height : int (default=200) //输出的画布高度，默认为200像素 
设置图片默认的大小,但是如果使用背景图片的话,那么保存的图片大小将会按照其大小保存(测试好像只是白底变大了) 
mask：就是文字所在的背景图啦，建议使用颜色较深的图。 
其他参数可自行搜索wordcloud所有参数。
哦对，最后结果：
![这里写图片描述](http://img.blog.csdn.net/20171018104500022?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvem91MjQ5MDE0NTkx/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
妈的 智障！
