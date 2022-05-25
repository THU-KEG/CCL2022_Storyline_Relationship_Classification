# CCL2022 新闻脉络关系检测任务评测

## 一、任务简介

### 1.任务背景
互联网已经成为人们获取新闻的主要媒介，从海量新闻中挖掘有价值的新闻及其故事脉络是一项重要的研究课题。故事脉络以有向图的方式组织和连接热点事件，以易理解和友好的方式展现给用户。高质量的故事脉络不仅可以辅助分析热点事件的起因、经过和结果，也能帮助决策者进行舆情分析、突发事件应急处理等工作。

然而，由于现有研究缺乏大规模、高质量和全面的故事脉络相关数据资源，这阻碍了相关领域的发展。
为了提供高质量故事脉络相关数据资源，清华大学KEG实验室联合华为构建了一个大规模中文故事脉络数据集CStory。该数据集包含了15211个新闻事件，112945个人工标注的新闻脉络关系对和49832个作为新闻脉络关系判断依据的关键句。

本次新闻脉络关系检测任务就是基于CStory中的部分数据进行的。
本评测集构建了数万条的新闻脉络关系实例的大规模数据集，覆盖了二十余个新闻领域，以评测当前现有技术对通用领域的普遍的新闻脉络关系语义的检测能力。同时该评测鼓励探索新闻之间的实体共现关系等信息对事件检测的帮助作用。

### 2.任务定义

新闻脉络关系检测任务的定义是：给定按照顺序排序好的两篇新闻，其中每篇新闻包含新闻的文本内容。标注者需要判断这两篇新闻是否具有【新闻脉络关系】。具有新闻脉络关系的新闻对标注为1，不具有新闻脉络关系的新闻对标注为0。



### 3.任务描述与解释

**新闻脉络关系**指的是两篇新闻按照时间顺序，围绕一个主要实体，在同一个话题下具有内容的**相关性**和**连续性**。其中，相关性和连续性缺一不可。

**相关性**指的是两篇新闻共享主要实体。从叙事学的角度来说，每个故事都是一系列按时间顺序排列的、有逻辑联系的事件，涉及一个或多个主体。每个故事都有一个作者最想告诉读者的一个事件，本文称之为主要事件。涉及到的主体在本文定义为主要实体。主要实体指的是能够作为主要事件的发起者、参与者或者承担者的实体，常见的主要实体有人物、组织、政府部门、团体、商品等。
每个故事都有一个焦点人物，一个特殊的参与者，从他的角度来讲述故事。因此，需要聚焦于每个新闻事件的主要人物，而不纠结于一些可有可无的参与者。这也是判断新闻脉络关系的一个重要的原则。具有共同出现的主要实体是判断两个新闻事件是否具有新闻脉络关系的一个必要条件。

**连续性**是指新闻对之间具有逻辑关系。所谓的逻辑关系，也分为若干种：

（1）因果关系。前一篇新闻描述的事件和后一篇新闻所描述的事件互为因果；

（2）时序关系，也叫做顺承关系。这种关系指的是后一篇新闻是前一篇新闻内容的发展和自然延伸，具有事件发展的顺承性。

（3）提及的临近性。例如，提及广州疫情，那么自然而然会想到临近广州的深圳疫情。事件在内容和背景上的相似性也是一种重要的逻辑关系。

（4）连带关系。连带关系可以认为是一种较弱的因果关系。即前后两篇新闻在内容上有关联，甚至前者对后者具有一定的促进作用，但是达不到互为因果这样强的联系。这种情况下就可以成为连带关系。


示例输入：

文档1：台铁太鲁阁号再出事故撞死一位闯入轨道妇人据台湾官方通讯社报道，台铁402次太鲁阁号今天上午7时11分在头城到礁溪间东正线吉祥路平交道撞上1位闯入轨道的妇人…

文档2：台铁事故拟处罚12人：台铁副局长记过1次4月2日，致49人死亡、218人受伤的台铁太鲁阁事件震惊全世界…

示例输出：
Label=1





## 二、评测数据

### 1.数据获取与生成

训练集、验证集和评测集的所有新闻数据均是从各大权威中文新闻网站搜集得到。所有新闻的发表日期均在2021年。为了防止信息泄漏，训练集、验证集和评测集中的新闻没有重复的部分。

### 2.数据分布

训练集共有30222条数据，正负样本比为1:1.42

验证集共有2983条数据，正负样本比为1:1.65

测试集共有4405条数据，正负样本比为1:1.82

### 3.数据下载


## 三、评价指标

本任务采用精准率（Precision, P）、召回率（Recall, R）以及F1-Measure作为评测指标。

精准率（precision）=检测出来的新闻脉络关系和标注相同的数量/检测出来的新闻脉络关系总数

召回率（recall）=检测出来的新闻脉络关系和标注相同的数量/标注的新闻脉络关系总数

F1=(2*precision*recall)/(precision+recall)

最终的队伍成绩排名根据测试集F1的排名确定。测试集F1的值越高，队伍排名越靠前。


## 四、报名方式及规则

发送报名表到[cstory_ccl@163.com](cstory_ccl@163.com)

评测使用的数据集以[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)协议分发，报名参赛即视为接受此协议。

参赛选手需确保注册时提交信息准确有效，所有的比赛资格及奖金支付均以提交信息为准；

参赛选手在管理系统中组队，参赛队伍成员数量不得超过5个，报名截止日期之后不允许更改队员名单；

每支队伍需指定一名队长，队伍名称不超过15个字符，队伍名的设定不得违反中国法律法规或公序良俗词汇，否则组织者有可能会解散队伍；

每名选手只能参加一支队伍，一旦发现某选手以注册多个账号的方式参加多支队伍，将取消相关队伍的参赛资格；

允许使用开源代码或工具，但不允许使用任何未公开发布或需要授权的代码或工具；

除主办方提供的数据集外，参赛选手允许使用预训练数据（如词向量、字向量、预训练语言模型等），但是不能使用额外的标注数据；



## 五、比赛日程

时间安排初定如下，后续如果有调整，将在讨论组中更新说明。

- 评测任务发布：6月1日

-	报名时间：6月1日—9月15日

-	训练及验证数据发布：6月20日

-	测试数据发布：9月15日

-	提交测试结果：9月31日

-	评测论文提交：9月31日

-	CCL会议日期(评测报告及颁奖)：10月14日—16日


## 六、结果提交方式

验证集发布后，允许参赛队伍多次向[cstory_ccl@163.com](cstory_ccl@163.com)提交结果，将所有预测结果写入一个文件，文件命名为“result.txt”，结果文件提交格式如下:

0

1

1

0

…

其中0或者1代表着该行的两篇新闻是否具有新闻脉络关系。提交结果文件的总行数要等于测试文件的总行数，不允许有空行。

最终提交文件要求：

每一个参赛队需提交的材料如下：

- 结果文件

- 代码

- 方法描述文档（非评测论文，评测论文撰写要求见CCL 2022官网）

代码需打包成zip文件，用“参赛队名_code.zip”命名，要求提交所有的程序代码及相关的配置说明，确保程序能够正确运行，且运行结果与结果文件相一致。方法描述文档用“参赛队名_method.pdf”命名，包含算法描述及参数设置，pdf格式存储，页数不超过5页。



## 七、赛事排名及奖励标准

最终的队伍成绩排名根据测试集F1的排名确定。测试集F1的值越高，队伍排名越靠前。

本评测总奖励50000元，由华为提供，奖金设置如下：

•	第一名20000元

•	第二名15000元

•	第三名10000元

•	技术创新奖5000元

## 八、新闻脉络关系评测组织方

任务组织者：

师凯杰（清华大学知识工程实验室）

侯磊  （清华大学知识工程实验室）

肖镜辉（华为诺亚方舟实验室）

吴敬桐（华为终端云服务部）

雍定钰（华为终端云服务部）

李涓子（清华大学知识工程实验室）

刘群  （华为诺亚方舟实验室）

任务联系人：

新闻脉络关系评测组委会：cstory_ccl@163.com 

师凯杰：             skj19@mails.tsinghua.edu.cn

柳孟阳：             619090934@qq.com



