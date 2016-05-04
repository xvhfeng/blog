---
layout: post
categories: [heart]
title: "今年的应届生面试总结"
tags: [ALbianj,java]
---

今年还是和去年一样，参加了公司组织的应届生招聘面试。去年出卷、阅卷都是
同事完成的，我只参加了最后的面试阶段。今年我参加了出卷、阅卷和初面的过
程。这里说说我这一次的感受。

首先说一下出卷。今年前面的基础理论出卷的是北京的同事，这部分每个考生都
是一样的答题，基本上就是一些基础的计算机理论。后面，由各个业务部门出自
己部门的业务题。我们技术部门题目也由北京的同事代劳了，因为我这边比较特
殊，我这边现在主要是部门或者说公司内部唯一一个主用c解决问题的，所以我
也除了一道题，但是因为考虑到题目的难度，我把题目作为了附加题。题目如下：
在一般的无锁编程中，我们经常会使用CAS这个原语，一些cpu对于CAS也有支持，
请你论述：CAS和mutex locker之间的差别。已知有两个系统，A系统为纯内存操
作，B系统为带有IO操作，请为A和B各选一个合适自己的线程安全模型，并说明
为什么？

设一文件服务器模型如下描述:
整个服务器分成3个module，main、network、task。
Main module单线程，主要负责accept socket，然后发送给network module；
network module多线程，负责接收socket传输的数据，再发送给task module处理；
task module多线程。架设这个服务器用在存储文件，task把接收到的数据写入文件；
请设计一种性能最高，完全无锁的模型。并说明原因（提示CAS并不是解决方案）。

有兴趣可以自己做一下，文章的最后会公布答案。

然后说一下阅卷。今年我们一共拿到70多份的试卷，从数量上来说，今年明显比
去年少了很多，大概少一半不到一点。去年我记得是130份，一个同事整整批了
一天。也不知道是我们下手慢了，还是现在的孩子已经都找到了孩子，还是和别
家公司冲突了，还是我们公司的知名度不够（这里说一下，我们公司今年才成立，
是由3家公司组成，创世、腾讯文学、起点，合并成了现在的阅文集团，所以现
在品牌知名度应该确实是一个问题）。反正人数就是不对。因为人数不对，直接
的问题就是导致了质量的下降。去年及格的试卷很多，导致去年及格中我们还要
挑一下控制一下面试的数量，而今年批完试卷，加起来一共20+的试卷及格，算
上应届生的多offer情况，这个比率已经很低了，初面的通过率基本上就要控制
在50%以上了。

接着说一下答题的质量，是我阅的那几份试卷中，没有一个人答对附加题的。就
前面的质量来说，大题2道中，第一道算法题正确率稍高，第二道sql查询有4问，
只有一个人全部答对，2个人错了一空。更多的人是只对了一个。第一道题基本
上只要稍微写过一些算法就能做出来，明显是送分的，没有什么难度。sql题基
本上同学们对于join比较陌生，特别是left join或者是right join，谁主谁副，
连接的时候到底是谁保留的多没有概念，导致了这道题超高的错误率。这个可能
和学校的教育方式和教育方向也有关系。现在的学校像数据库可能还是在用80年
代的书，更有还在用foxpro的，这也是醉了。sql的语句教的也不多，和市面上
的实际应用脱离比较严重。

在我同事的阅卷过程中，有3个人答对了附加题。其中有个交大的孩子前面做的
一塌糊涂，后面附加题答对，我们破例给他了面试机会。其实在我出题的时候，
当时我在部门就断言，能做对附加题的，应该面前会一塌糊涂。因为这道题明显
不是理论，学校里面的好学生都听着老师的话，啃着书本的理论，哪里动过手？
我和hr开了一个后面，直接让他们把这个人安排给我面。后面的面试果然印证了
我的想法。

然后我们说说面试的过程。今年面试的过程被安排在了公司附近的一家宾馆，个
人感觉这个安排不太好，在一个大会议室，太嘈杂，像菜市场一样。吐槽完了，
说正事。上午被安排了5个，下午是6个，上午2个没来，下午1个没来。中间hr还
给塞了2个，因为我同事来不及面，我还帮忙面了一个。一共面了14个人，最后
过了3个，一个待定。

过程就不一一表述了，只说一下给我留下特别印象的：

1. 附加题答对的“怪胎”：这哥们后来了解到是写协议的，对于linux和网络协议
   栈很熟悉，但是人家只写到3层就结束了，4层以上他很少写过。我和他除了
   聊了一些基本的信息，我就和他聊了半小时的那道题。其实他不知道CAS是什
   么，答对第一问是猜的，或者说是排除法。他说第二问有io操作，所以选择
   mutex应该没有多大的影响，所以第一问全内存应该是cas。这哥们有点意思，
   逻辑还挺强。那么我问他怎么做出来第三问的时候，他和我说这道题其实考
   的是操作系统，要无锁的话必须全程自己写调度算法。而上面的CAS其实是幌
   子，他说到这里的时候，我已经决定给他S了，这是我们这次面试的最高等级。
   他不仅做出来了，而且确实看懂了题目。唯一影响他没有得到S+的是，他第
   一想法还是想阻塞在内容，而不是操作，这样的话，只要说是阻塞在内容，
   那么就一定会有锁出现，或者是使用CAS。所以这个回答影响了他成为唯一一
   个S+。从这个哥们看下来，在大学还是要自己研究一点东西，至少这些东西
   能给你带来面试被录取的机会。这哥们可能最后不会来，我有这种预感，但
   是我还是和他说了一下我们下来的规划和一些项目情况，希望他能来。

2. 还有一个给我印象比较深刻的哥们是一个已经在点评实习的孩子。这孩子是
   被hr塞过来的，起初没当一回事。但是坐下来后的言语让我惊了。哥们发表
   了一下关于自己对于语言和平台的喜好，这个也算正常，但是摆出了一副非
   java不做的态度就有点让人感觉不好了，这是其一。其二，作为应届生，不
   是我看人低，但是确实还没有到挑肥拣瘦的地步。给我的感觉就是情商不高，
   加上第一眼感觉有点呆呆的，就给我留下了不好的印象。不过我还是耐着性
   子和他聊了聊，感觉这哥们技术还是不错的，对于一些平台的认知确实有一
   些，但是对于优缺点基本上就是网上看来的那种“语言、平台偏见”之流了。
   自己也建有github，上面还有挺多的项目，自己也维护了一个多年来的国内
   发生事故的一个字典库，这个是他们实验室的零散的东西，但是他花了很长
   的时间把他整理出来，并且格式化成xml，可以让使用者直接使用，这方面的
   想法和耐得住寂寞、耐心的整理还是很难得的。
   鉴于技术还不错，最后也给了过，给他留一个机会让我领导喝一壶，哈哈。

3. 第三个有印象的哥们是一个被外包或者说是被学校的毒害的。在大学几年，
   他跟着老师做各种项目，有c#的，有php的，有java的。但是呢每个都不深入，
   对于一个平台的研究也没有定性。其实技术的问题倒还是其次，重要的是这
   种模式让他本人没有了一个明确的定位。老师值顾着自己挣钱，一个项目十
   几万，他们实验室的人一个月1k，真tmd是压迫和剥削。比旧社会的资本家还
   不如。而且还害了他们。这哥们面试的是cx的职位，但是他最差的就是c，他
   自己也直言c是最差的，我问他那么为什么投c，他说想用这个当一个敲门砖，
   敲开企业的门。最后我和他说，你还是要固定住一个平台，先把这个弄懂，
   弄清楚，多做一些平台是对的，但是不能都是只在一个会做的水平。希望这
   个哥们寒假能好好的攻一下php吧。下一份工作能顺利一点。

4. 还有几个个人感觉是比较奇葩的。一个是做遥感测绘的，这个哥们做了一个
   项目，就是监测地铁的隧道那种细微的变形的，可以说对我们的日常生活很
   有帮助，保证了我们的安全。而且这个项目还拿了国家的奖，确实很牛逼。
   第二个哥们是光电的，也做了一个很牛的项目，用激光检测某种气体的浓度，
   先用光照射某个地方，然后把光的反射的光和原来的光转换成电信号，然后
   用电信号做比较，最后得出浓度。这个项目也有论文登在EA上，并且也拿了
   国家级的奖，这哥们还是交大的班长。就是面试比较经常，导致我们hr以为
   他笔试的时候是代考的。还有一个是做虚拟现实的，这个哥们一般，没有什
   么过人的地方。但是他们有个共同的点，就是想转互联网。这个说明现在互
   联网确实挺热的。但是他们几个人有个共同的特点，就是为了转而转。具体
   表现在，考卷分数挺高，但是对于行业一点都不了解。甚至都不了解这个行
   业到底是怎么做的，自己过来做什么。现在开源社区那么多，也没有关心过。
   这是很不应该的，既然想转了，至少要对这个行业有个了解，要不然就算放
   你进来你一看和想的不一样，这样对个人和对自己都有损失。

唧唧歪歪说了那么多，经历了一天面14个人，那种下班直接就是不想再说一句话
了。作为一个面试官，还是有一定的感受：

首先，同学们要为面试做一定的准备，但是不要去准备算法啊啥的啊，
面试的过程中，有同学问我为什么不问他算法什么的？我反问他，为什么要问他
算法？算法这种题目一般笔试都了解了，面试就是聊一聊，看看你对于即将用到
的知识的掌握程度或者是熟悉程度，而不是生硬的算法。再说如果我要问，我也
会问数据结构，在我的概念中，数据结构比算法远远重要的多；

其次，如果你想换行，那就先对这个行业有个基本的了解。对你的工作，对于说
使用的工具，和这些工具能产生的效应都有一个基本的了解。如果可以，也需要
对这个公司，这个部门，或者是这里面的一些人有一定的了解。这样才能打入敌
人内部啊。千万不要一问三不知，还反过来问面试官，你说我来了我能干啥？拜
托，你自己都没想好你能干啥，你让我怎么给你做决定？我录用了你，用不合适
一丢就完事，但你的损失就大了，第一份工作很重要，对于99%的孩子来说就是
决定你以后命运的工作，换行业很难的，没有想象中，或者是网上看到的那么简
单，所以还是请学生们要考虑清楚；

再次，请使用你最擅长的本事找工作。除非你是实在不想在这一行混，否则你还
是老老实实的用你最擅长的。一来，你对这一行也有很深入的了解，二来，你在
擅长的方面应该也会有一定的经验，三来，没有了换行的苦恼，四来，对于用人
单位也是一个保证。所以你看，有那么多的有点，你为什么不用呢？

最后，说点学校的事情吧。学生在学校首要的任务是完成学业，这是必须的。但
是就我个人对学校的认知，我还是觉得在学校60分就够了。导师给的项目也是要
做的，这毕竟会影响你的文凭。但是在导师布置的之外，个人还是要想一下以后
的发展，如果是本科呢，大二就可以开始考虑了；如果是研究生了，那么入学就
可以开始考虑了。这样你有大把的时间可以熟悉你以后的工作的内容。如果面试
的时候，有人和我说我看了互联网很多高并发编程的源码，我会用简单的gdb调
试，我会用vim或者emacs，并且有配置，我linux很熟悉等等，这些中哪怕是有
一条，那么基本上你被录取的可能性就是在99%了。

好吧，最后公布一下我们实践中得到的附加题的答案：（PS：只说重点）

1：CAS是一个CPU级别的线程安全的操作，由底层支持；mutex其实是一种编程原
语，它只是一种人为约定的规则，并不是必须的；

2：CAS适用于A，mutex适用于B。性能问题：CAS其实在多线程中并没有吹嘘的那
么块，原因是CAS是靠轮训CPU，榨取CPU的性能，抢占线程的控制权来达到目的。
而mutex是靠让线程投入sleep，让出cpu时间片来打到目的。因为A为纯内存操作，
cpu时间片会相当快，所以多使用几次无碍，带有io操作的是系统慢操作，一般
需要线程等待很久的时间才能写完，所以用cas会不停的抢占时间片，但是除了
消耗cpu并无一点用处，还不如直接让线程通过mutex让出时间片，供io来操作，
这样会节省cpu的时间片，减少无谓的抢占。

3：服务器接收到的操作，对于同一个对象的操作请求，保证分配到相对的固定
一个线程来操作就可以。同时来的操作需要进行排队。总之在无锁的情况下保证
一个对象只被一个线程处理，并且同时对一个对象的多个操作进行顺序化处理。  

PS：如果答题者说用队列阻塞内容，请酌情给分。最最正确的答案是阻塞在操作
上，因为阻塞在内容，对于内容是多线程操作，所以还是会有锁或者是CAS解决。