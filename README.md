# named_entity_recognition
命名实体识别实操——详细步骤(raw数据+标注+dataloader+crf)
### 任务目标
* * *
从一些工厂、单位的日常检查日志中，识别出隐患设备和隐患地点，如下表：
||  隐患日志   | 隐患地点 |隐患设备|
|-| ------- | --- |---|
|1|  轧钢部一轧反吹压力表未校验  |  轧钢部 |反吹压力表|
|2|   铸管4.0施工现场多处气瓶间距不符合要求   |  铸管、4.0施工现场 |气瓶|
||……|……|……|
|121|煤气职业危害告知牌检测数据未更新||煤气职业危害告知牌|

ps：  
①如表格最后一行显示，我们可以允许有的描述没有隐患地点，且我们的真实数据就是121条。  
②上表的顺序仅是实例展示，不代表selected_data.xlsx中的真实情况。  
实验步骤：  
1、将每一句话用BIO标注方式标注  
2、使用crf模型训练  
下面我们介绍详细的标注工具及步骤  
* * *
### 数据标注：  
善其事而先利其器，故采用[YEDAA](https://github.com/jiesutd/YEDDA)这个python开源工具包来标注。  
使用时几点注意：  
1、操作方法是用英文写的，基本能涵盖你的使用要求(花几分钟时间随便建一个txt练练就会了)；  
可以通过在配置目录下新增或修改配置文件，实现用字母一键标注功能  
2、目前（2020.11）只支持Python2，我用conda创建了一个py2环境，使用前切换一下虚拟环境就好；  
3、支持直接导入文件（open按钮），我使用的是txt格式；  
3、支持导出形式设置  
4、其他快捷键命令  

