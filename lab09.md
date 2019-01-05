# 简析”自顶向下，逐步求精“
## 自顶向下

自顶向下（top-down）的分析算法通过在最左推导中描述出各个步骤来分析记号串输入。将大型的数字电路设计分割成大小不一的小模块来实现特定的功能，最后通过由顶层模块调用子模块来实现整体功能，这就是Top-Down的设计思想。

![all](/images/42.jpg)

## 逐步求精

将现实问题经过几次抽象（细化）处理，最后到求解域中只是一些简单的算法描述和算法实现问题。即将系统功能按层次进行分解，每一层不断将功能细化，到最后一层都是功能单一、简单易实现的模块。求解过程可以划分为若干个阶段，在不同阶段采用不同的工具来描述问题。在每个阶段有不同的规则和标准，产生出不同阶段的文档资料。

![all](/images/43.jpg)

#### 下面以洗衣机的代码实现为例分析这种方法：

首先，通过对问题的分析画出洗衣机工作的流程图：

![all](/images/44.png)

然后，再根据流程图书写伪代码，并逐步求精得到结果：

<pre>
Read mode/*选择洗衣模式*/
If 
    正常洗衣 
Then 
    Read time/*选择浸泡时间*/
end if
    Read water/*选择水量*/
While getwatervolume()
     water_in_switch(open)/*开注水口*/
end while
    water_in_switch(close)/*关注水口*/
If 
    正常洗衣 
Then
    wait(time)
end if
While timecounter()
    motorrun(left)
    motorrun(left)
    motorrun(right)
    motorrun(right)
end while/*漂洗*/
While getwatervolume()>0
     water_out_switch(open)/*排水*/
end while
While timecounter()/*脱水时间*/
    motorrun(left)
    motorrun(left)
    motorrun(right)
    motorrun(right)
end while/*脱水*/
halt()/*停机*/

Function wait(time)
While timecounter()
    time
end while/*浸泡时间*/
</pre>

## 总结

在解决一个复杂的问题的时候要学会将问题分解成小问题，自顶向下的，逐步的将每一个问题解决，再综合起来使结果精确、完美。