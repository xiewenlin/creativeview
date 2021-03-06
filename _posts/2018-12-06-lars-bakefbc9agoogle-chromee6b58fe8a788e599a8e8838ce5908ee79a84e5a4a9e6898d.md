---
ID: 794
post_title: >
  Lars Bak：Google
  Chrome浏览器背后的天才
author: WelonMusk
post_excerpt: ""
layout: post
permalink: 'http://creativeview.cn/2018/12/06/lars-bak%ef%bc%9agoogle-chrome%e6%b5%8f%e8%a7%88%e5%99%a8%e8%83%8c%e5%90%8e%e7%9a%84%e5%a4%a9%e6%89%8d/'
published: true
post_date: 2018-12-06 17:12:26
---
<h4>痛点描述：网页浏览器都不赚钱，无论是IE、Safari、还是火狐。那么，谷歌为什么要投入时间和精力在免费产品上，而这些又不能给公司带来收入？答案不在浏览器本身，而在于它能访问的内容：也就是网络应用程序。这些才是给谷歌带来收入的东西。</h4>

<!--more-->
<img src="https://www.wailian.work/images/2018/12/06/image3c215.png" alt="image3c215.png" border="0" />

V8 引擎是 JS 语法事实上的标准实现，Chrome 浏览器和 Node 的底层都用了它。它名字里面的<span data-type="color" style="color:rgb(41, 47, 51)"><span data-type="background" style="background-color:rgb(255, 255, 255)"> V 代表虚拟机（virtual machine），8 表示这是作者 Lars Bak 写的第8个虚拟机。</span></span>

Lars Bak 是一个传奇的丹麦程序员，在 V8 之前，他还写过 Java虚拟机、Smalltalk虚拟机、Dart虚拟机。下面是2009年英国《金融时报》的报道。

<blockquote>
  <span data-type="color" style="color:rgb(79, 79, 79)"><span data-type="background" style="background-color:rgb(255, 255, 255)">奥尔胡斯（Aarhus）是丹麦第二大城市，在该市郊外5英里的地方，有一座改造过的农舍。房子的主人叫 Lars Bak，是一个年轻的编程天才，他之所以把家安在这里是因为他非常不愿意让别人找到自己。他最近的作品 V8 是 Chrome 浏览器的一部分。</span></span>> <span data-type="color" style="color:rgb(79, 79, 79)"><span data-type="background" style="background-color:rgb(255, 255, 255)">1991年，他在 Sun 公司工作，后来成为业界最佳程序员之一，开发了 Java HotSpot。2000年初，他离开了硅谷，回到了丹麦。搬家是为了他的女儿们（他想让她们上丹麦语学校），也为了自己的身心健康。美国的工作很紧张，生活方式不健康。</span></span>
  <span data-type="color" style="color:rgb(79, 79, 79)"><span data-type="background" style="background-color:rgb(255, 255, 255)">他并不特别想找新项目：他有足够的钱养家糊口，也有各种打发时间的方式，包括粉刷农舍的计划。他估计得要一年时间。这时，Google 的电话就来了。对于 Google，他是编写 JavaScript 引擎的最佳人选。巴克接受了这份工作，但不会回到加州。事实上他从没打算再次回加州，虽然谷歌的人性化办公室闻名远近，餐厅里的美食，还可以免费理发，巴克却宁可在家工作离总部5000英里，相差9个时区。</span></span>
</blockquote>

奥尔胡斯（Aarhus）是丹麦第二大城市，也是日德兰半岛（Jutland）的非正式首府。在该市郊外5英里的地方，有一座改造过的农舍。里面有宽敞的木地板和拱形的顶（曾经是马厩的一部分），在距离DVD播放机不远的地方摆着一个大的棕色皮沙发。从外面看，这座房子看上去仍略显陈旧：粗糙的石子路，凹陷得小窗；但正是这里孕育了互联网未来的关键部分之一。

从哥本哈根开车到这里的路程比预期的更漫长，房子也很难找。房子的主人叫拉斯•巴克，是一个年轻的编程天才，他之所以把家安在这里是因为他非常不愿意让别人找到自己。他的阿尔萨斯牧羊犬，米奇，见到我们也有些受惊：主人把它看住之后我才敢下车。

那是丹麦寒冷十二月的一天。这地方比爱丁堡还靠北，但天色如同东英格兰沼泽地的一样，灰蒙蒙一片。我们握手的时候，巴克看上去很不自在，我觉得他好像压根不想让我靠近他的居所。不过，我们还是走进了放有棕色皮沙发的拱形顶房子里。现在这里是家庭影院，之前曾是他编程的办公室。温度只比外面稍高一点。我拿出笔记本的时候还在瑟瑟发抖。“好吧，您想了解些什么呢？”巴克发问了。我们有四个小时的采访时间。

拉斯•巴克并非家喻户晓的名字——至少这个拉斯•巴克不是。在丹麦还有一个拉斯•巴克更出名，那是一位职业自行车选手。但是这位巴克可比任何运动员对你生活的影响更加深远。他最近的计算机软件程序V8是Chrome浏览器（谷歌商业计划的关键）的一部分。

网页浏览器都不赚钱，无论是IE、Safari、还是火狐。那么，新浏览器对谷歌的重要性何在？为什么要投入时间和精力在免费产品上，而这些又不能给公司带来收入？答案不在浏览器本身，而在于它能访问的内容：也就是网络应用程序。这些才是给谷歌带来收入的东西。比如，该公司对Google文档寄予厚望，这是一套在线办公软件，和微软的当代企业工具桌面版Office程序（Word, Excel和PowerPoint）类似。但为了更好地体验获得这些程序和其他在线应用，用户需要更好的浏览器，以便更好地运行相关代码。我们很多人已经在使用网络程序了，比如Hotmail, Yahoo邮箱或Gmail，不过它们都相对简单，比起一般的桌面软件，它们的复杂性相形见绌。

浏览器已经无法处理日益复杂的网络应用。就好比是很多高性能的跑车跑在辙颠簸不平的路上一样。但是没有哪家跑车制造商会出钱修路，毕竟自己修路对手也会沾光，更不要提高昂的费用。软件开发的成本不高，但依然存在竞争问题。不过谷歌说它不在乎，它说：没有好的浏览器，大家伙儿都会遭殃。

通过网络访问复杂程序的能力被称为“云计算”，并且谷歌并非唯一一家声称领先的公司。即使微软，桌面应用软件和操作系统的代名词，也在跃跃欲试。史蒂夫•鲍尔默，微软的首席执行官，已经承诺研发“在互联网中运行的操作系统”——他称之为“视窗云”，不过要想真正实现云计算，必须改进浏览器。

恰在此时，巴克出现了。这个丹麦人首次在加州硅谷引起人们的注意是在1991年，那时他在Sun公司工作，后来成为业界最佳程序员之一。1994年，他离开Sun，帮助创建了Animorphic系统，该公司后来被Sun收购。再次回到Sun之后，巴克开发了后来成为Java HotSpot（行业标准计算系统之一）的程序。

可是2000年初，他却离开了计算机世界的核心，回到了丹麦，搬家是为了幸福生活，为了他的女儿们（他想让她们上丹麦语学校），为了自己的身心健康。美国的开发者社区工作很紧张，生活方式不健康。当巴克回到丹麦时，两个月之内他减了20斤（多亏了美国的阿式饮食疗法【Atkins diet】），而且再也没有反弹。

2002年，巴克在奥尔胡斯创建了一家名为OOVM的公司。2004年，他将公司卖给了一家瑞士公司Esmertec，然后又在该公司干了两年，帮助两个公司的融合。离开Esmertec时，他并不特别想找新项目：他有足够的钱养家糊口，也有各种打发时间的方式，包括粉刷农舍的计划。他估计得要一年时间。

然后Google的电话就来了。对于Google，巴克是不二选择——他编写了JavaScript引擎（Chrome的核心部分）。对于巴克，为Google工作就是 “小菜一碟”。“我不在乎当什么高级经理。我在乎的是推动技术边界。”巴克接受了这份工作，但不会回到加州。事实上他从没打算再次回加州——虽然谷歌的人性化办公室闻名远近，餐厅里的美食，还可以免费理发，巴克却宁可在家工作——离总部5000英里，相差9个时区。谷歌做好了“信任我的准备。他们知道我不会消磨时间。”重新装修农场的计划要搁置一下。“最后，”他说，“我只有14天的时间（粉刷）。涂料还留着呢。”

巴克在日德兰半岛的居家办公室，他和妻子，孩子还有宠物阿尔萨斯牧羊犬米奇住在一起

巴克开始工作，在现在是家庭影院的地方建立了办公室。农舍是围绕院子修的，家就在办公室对面。每天，他走过石子路到办公室，然后开始写代码。每天结束时，他又穿过院子，走回家，把工作彻底放下。在这些行走之间，他投入到浏览器开发中，有了这种浏览器，其他人就有更多机会做他所做的事：在家工作，与总部连接，所需要的全部工具就是互联网的力量。

巴克也许是个计算天才，但他是上大学之后才开始接触计算机的。“高中的计算机室又黑又臭，只有书呆子才去，”他说，“我喜欢运动。弹板跳水–特酷。我后来才成为书呆子的。”

在《局外人》中，Malcolm Gladwell探讨了天才和成功的本源，作者陈述了这样的观点，你需要苦练10000小时才能在所选择的领域里真正成功。我问巴克，你做足10000小时了么？我能看出来他觉得这压根不相关；他对此也不感兴趣。“我只是很高兴大器晚成”，他再次强调，“而不是年少就成名。”

也许是因为大器晚成，巴克从不热衷于传说中那种靠咖啡提神彻夜写编程代码的故事。不过这可能也缘于巴克精通的程序类型：“虚拟机”，这是计算机科学家Gerald Popek 和他的项目伙伴Robert Goldberg早在1970年代所探讨的一个想法。虚拟机器名副其实——真正机器的计算机世界版，能够在单机程序或整套程序上使用。Chrome浏览器属于后者。V8，巴克的虚拟机器，编辑不同程序通用的代码，以便减少冗余，让网络应用程序更快运行。

“虚拟机是头怪兽，”Bak说，“没有完美的解决方案，你只能为“最佳时机”进行优化。有很多技术含量在其中。这是个漫长的游戏，你玩不完的。

“工作量是恒定的，”他补充说，“所以我总要停下来吃饭。你可以有正常生活。”对巴克而言，这意味这家庭和隐私。工作/生活平衡的问题在谈话中一再冒出来——虽然他不反对美式生活，但显然他更喜欢丹麦的生活方式。“在美国，需要进取和格外自信。欧洲的生活方式则不然。而在美国，你能有晋升机会，能与技术发展保持同步。在欧洲，你就只能做办公室当经理，没有活可干。”通过在丹麦为谷歌工作，巴克意在一箭双雕，同时享受两个世界中最好的东西。

巴克将他的V8项目成为笑话：V8引擎就好像汽车镀铬发动机罩下面安装的那个东西 ——“而Google就那么酷——不论项目最初的名字是什么，以后不会改变。不会因适应市场营销而改变名字。”

从开展谷歌项目的第一天，巴克就征募了他以前的学生卡斯帕•伦德的帮助。伦德年轻也更外向，他同意来农舍上班。他还有其他作用——让巴克娱乐。伦德和他那竞争力很强的老板习惯于用乒乓和Wii网球来调剂工作。谁的乒乓能赢，我在想；巴克回答说：“问卡斯帕。”哦，那么卡斯帕能赢喽。“不是。”稍后，他透了口风：“他打得比我好，不过还是我赢。”他们的关系已经从师生变得更像同事，但又不完全是；有朋友把这比作巫师和学徒。

许多程序都是用以前的版本或相关代码创建的，但V8是白手起家——一片空白。后来当我在丹麦之旅中遇见伦德时，他很乐于强调这一点：“这是最纯粹的编码形式。”巴克显然有共识——在伦德说话的时候，他不停地微笑。

随着V8深入，项目扩展，巴克和伦德把编写代码从农舍搬到奥尔胡斯的一座大学，巴克在此任教。骑车需要30分钟，把通勤当作锻炼和巴克将工作和生活平衡的哲学不谋而合。

大学办公室虽然在距离上与加州山景Googleplex总部遥遥相隔，不过一看就是谷歌的风格。在进门的地方，五颜六色的椅子和小布袋到处都是，然后是两个主要房间，有10来个人在这里工作。不过没有餐厅，只有厨房，里面有坚果贩卖机，还有一冰箱的瓶装水和健怡可乐。巴克引入了无糖政策：“不是完全无糖——你可以从水果里得到自然糖分。不过没有巧克力，没有明目张胆的糖果而已。”

每个人愿意接受这里的管理制度，见证了办公室的忠诚度。好像所有人都骑自行车来上班，下午5点左右就离开。“我们开始的也早，累了还工作没有意义，所以我们就回家，”伦德说。这是两小时前巴克在他的农场上给我讲述的工作生涯的逐字描述。这令人心服口服。但和谷歌的人沟通怎么办？当巴克、伦德和其他成员在奥尔胡斯时间下午5点下班时，旧金山还不过早上9九点。他们是利用硅谷24小时工作的趋势吗，还是并不需要和总部保持联络？伦德说大多数时候用电子邮件就可以了。我采访的当天，在其他同事下班之后，巴克需要参加电话会议。他努力不把情绪流露出来，但很显然，他并不想参加。

编程可以是很单调的事情。虽然巴克和伦德紧密合作，但还是有种遗世独立的感觉。你写代码，测试，修改，再写，周而复始，直到你得到自己需要的。对于巴克，这很简单，也很隐蔽。然后，出于某种原因，外界就想进来干扰——想要认识你，想要了解你的工作。

巴克很看重自己的隐私。在家给他照相也让他明显不自在。但当我告诉他，把他的名字输入谷歌搜索引擎里，得到的都是一页又一页和他同名的自行车手，这肯定遮挡了他本该有的光彩，他耸耸肩，“我老了，不在乎别人说我什么。”

真正让他恼火的是大家误会他的工作——或按他的说法，“技术”。他举了一个例子，在有篇关于他的文章里，记者混淆了Java和JavaScript（前者是可以在线进入的独立程序，而后者是依靠浏览器的脚本语言）。对此我们都笑起来，在那么一瞬间，我觉得巴克和我有了默契。

世界以非同寻常的方式发现了Chrome。故事是通过谷歌早前发布的专门漫画传出去的——显然犯了个错误。公关忙成一团来支持这个消息，匆匆忙忙地举行了电话会议，发表博客日志解释到底发生了什么，随后又是新闻发布会，然后在Googleplex举办产品展示。

在群情激动地讨论为什么谷歌要发布新浏览器，泄密是不是有意而为之时，认真看漫画的人寥寥无几。虽然是由Scott McCloud（也算是漫画界的传奇人物）编撰的漫画，这可是艰难的工作。讨论的是Java Script (不是Java哟！)，CPU和存储器漏洞——大多数都不想知道的计算细节。但是这漫画却显示了Chrome特性背后的思想理念，还有独立小组解决拼图各个部分的方式。巴克和伦德最初出现在第二页上，不过是到了大约三分之一的时候，在第13页，才有对“丹麦V8团队”的介绍，解释了这个“虚拟机器”的开发，不过没有提到为什么V8距离谷歌总部那么远，隔着大陆和海洋。

伦德和巴克喜欢这个漫画。在奥尔胡斯办公室里，整幅漫画都用相框框起，挂在墙上。“开始，我觉得这想法很怪异，”巴克说。“但是我意识到这太有才了。与其他白皮书相比，这要强10倍。大家都觉得这很有趣。”

我怀疑他们俩都喜欢它的原因是它平等地对待巴克和伦德——虽然与巴克相比，伦德可算是个大块头。“让我看上去像个15岁的男孩，”巴克说。他矜持地微笑了。

在刚推出的100天内，Chrome就已经吸引了一千万用户。虽然这个数字很震撼，可也只代表在线浏览器使用的百分之一。它还需要假以时日方能与火狐、IE及其他产品抗衡。去年12月，谷歌宣布Chrome已经结束研发或Beta（测试）阶段，准备在某些个人电脑上作为预选安装的浏览器发行。这样可以迅速增加用户数量。而且，欧洲委员会与微软就其IE浏览器如何并入视窗（Windows）操作系统所产生的反托拉斯战争以及其他纷争可能会给谷歌这样的竞争者占领市场的机会。

抛开法律和市场份额不说，技术挑战已经存在了。“微软不得不创建比V8更好的东西，”巴克说。很多技术观察家很怀疑他们能够在短时间内完成：在测试中，V8处理JavaScript的速度比最常见的IE浏览器要快56倍。“我们一开始就是高标准，”巴克说。随后谦虚地加了一句：“还算成功啦。”

即使Chrome漫画没有让巴克迅速成名，他的知名度在这几个月中也迅速增加。越来越多的人想了解Chrome背后的这个人。他宁可写虚拟机器，也不愿意管理奥尔胡斯办公室，而且他宁可做其他所有事情，而不是和记者谈话，可那是游戏的一部分，他接受了。话虽如此，他离Facebook的创建者马克•扎克伯格或比尔•盖兹还有很远的距离。我问，在漫画出来之后，你有没有收到粉丝的邮件？他笑了：“没。不过我也没有收到抱怨的邮件。”

<h3><strong>背景知识介绍：浏览器大战</strong></h3>

互联网在其短短历史中，已经看到各种浏览器的产生，但是主角只有四个：网景（Netscape）导航器，IE浏览器，火狐（Firefox）和Chrome。

说到普遍使用，网景浏览器是第一。每个人都用过导航器——部分原因是没有其他正儿八经的替代者——而且它用起来不错。然后是微软的IE浏览器，该产品是公司主导产品Windows操作系统的一部分，从而带动着它的增长。截止1998年，IE在使用方面已经取代了网景。

微软被指控违反了反托拉斯法，但那时已经太迟。IE控制了90%的市场份额，虽然有官司在身，时至今日，它还是以默认浏览器的身份安装在世界上绝大多数个人电脑上。网景被美国在线（AOL）收购了，在历经波折之后，于2007年停止研发。

要不是“开源”社区，事情到此就结束了。开源软件曾是（而且在某种程度上仍然是）微软之鞭。总裁史蒂夫•鲍尔默曾说Linux的开源操作系统是癌症。此类软件由软件开发者团队的人不断改善，他们这么做基本上是什么都不为。劳动果实通常都免费分发。1998年，网景将导航器的代码转换为名为Mozilla的开源项目——火狐正是从此演变而来的。

火狐占了IE市场份额的20%，而且仍在增长。它的众多属性——如分页浏览和读取设置——在其他产品如浏览器Opera上出现得其实还更早，但是得益于口碑相传、出色的市场营销和火狐的对于技术水平较高用户的吸引力，它已然成了IE最强劲的挑战者。而且，它是开源的，第三方开发者可以通过创建新应用程序扩展火狐的容量，让它更加强大。

在2008年谷歌推出Chrome之前，浏览器市场好像成了IE和火狐二者之间的竞争，当然也得提及以Mac为基础的Safari。

Chrome仍然只有百分之一的浏览器份额，但这会增长。有了拉斯•巴克的V8引擎，Chrome简直如虎添翼。该浏览器使用许多开源代码和开放标准，但也引入了一些重要的创新，如独立页面的使用。这听起来很无聊，但其实很至关重要。原因如下：通常，通过浏览器运行几个网络应用程序会导致崩溃。而且当一个浏览器页面崩溃时，整个程序都需要重启，其他页面上的工作或活动都会丢失。

Chrome的运作方式意味着任何浏览器的崩溃都仅限于当页，所以，如果你在一个页面上写邮件，而另一页面的视频崩溃了，你的邮件并不受影响。你可以把崩溃的页面关掉，继续工作。让浏览器以这样的方式工作——好像桌面一样——对于未来网络应用程序至关重要。

当然，Chrome的运行速度也很关键。为了网络应用程序能够成功，它们需要反应迅速，否则用户会郁闷。速度、稳定、安全——这些都是我们未来在线活动的关键方面。而浏览器则是大门。