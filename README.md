
# deepspeech 环境搭建

新建虚拟环境：conda create -n tensorflow python=3.6

激活虚拟环境：source activate tensorflow

1.安装tensorflow：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple tensorflow==1.13.1

2.安装keras：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple keras==2.2.4

3.安装语音流处理模块：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple soundfile==0.10.2

训练环境安装前三个就可以，测试环境需要后面两个

4.安装beam search解码模块（解码模块使用mozilla项目里面的）：pip install https://index.taskcluster.net/v1/task/project.deepspeech.deepspeech.native_client.v0.5.0-alpha.11.cpu-ctc/artifacts/public/ds_ctcdecoder-0.5.0a11-cp36-cp36m-manylinux1_x86_64.whl

报错platform不支持的话在mozilla的DeepSpeech里面执行进行安装：pip install $(python util/taskcluster.py --decoder)

gpu版：pip install https://index.taskcluster.net/v1/task/project.deepspeech.deepspeech.native_client.v0.5.0-alpha.11.cpu-ctc/artifacts/public/ds_ctcdecoder-0.5.0a11-cp35-cp35m-manylinux1_x86_64.whl

5.读字节流：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pydub

# 模型部署
./speech_model里面放入训练好的pb模型，和训练集的std、mean数据

./LM_model里面放入训练好的n-gram语言模型

入口voice_to_text.py

# 测试结果
100条数据堂电话语音数据上平均字错率0.02，句错率0.06
label    predict    acc
 我不是发给你了么     我不是发给你了吗    0.875
 我们在一起好不好     我们在一起好不好    1
 最后告诉你一句话     最后告诉你一句话    1
 你给我找一个一天     你给我找一个一天    1
 你现在有没有时间     你现在有没有时间    1
 你可不可以读电子书     你可不可以读电子书    1
 我们挺过了世界末日     我们挺过了世界末日    1
 上海市开车怎么走     上海市开车怎么走    1
 知道我叫什么名字吗     知道我叫什么名字吗    1
 下次我们一起去吧     下次我们一起去吧    1
 上班无聊怎么办呀     上班无聊怎么办呀    1
 看到给你发的了吗     看到给你发的了吗    1
 取消明天六点半起床     取消明天六点半起床    1
 你也喜欢吃土豆     你也喜欢吃土的    0.85714286
 你开放还是保守     你开放还是保守    1
 你们为什么分手啊     你们为什么分手啊    1
 你很漂亮你很性感吗     你很漂亮你很性感吗    1
 华光陶瓷集团地址     华光陶瓷集团地址    1
 老师说我失恋了     老师说我失恋了    1
 我的课题作业来的     我的课题作业来的    1
 哇太快了可能我要十一再弄     哇太快了可能我要十一再弄    1
 这我还真不知道呢     这个我还真不知道呢    0.875
 我是个彩民我想使用手机投注需要建帐户     我是个彩民我想使用手机投注需要建帐户    1
 播放梁静茹的歌     播放梁静茹的歌    1
 我是说要想听留言要登什么博客     我是说要想听留言要登什么博客    1
 宁夏石嘴山市西北机械技师学院邮编是多少     宁夏石嘴山市西北机械技师学院邮编是多少    1
 台州职业技术学院     台州职业技术学院    1
 你在我的歌声里     你在我的歌声里    1
 根本就没有可比性     根本就没有可比性    1
 茶叶对身体好吗     查下对身体好吗    0.71428571
 东莞的小姐     东莞的小姐    1
 以后不打电话给你了     以后不打电话给你了    1
 你听日买杯奶茶多谢下我啊     你听日买杯奶茶多谢下我啊    1
 男人跟女人有什么区别     男人跟女人有什么区别    1
 是真实的需要应该     是真实的需要应该    1
 给我放首江南     给我放首江南    1
 跟下级在一起吃饭应说怎样祝福语     更小心在一起吃饭应说怎样祝福语    0.8
 起来了吗起来了吗     起来了吗起来了吗    1
 床前明月光后面是什么     床前明月光后面是什么    1
 几点几分几秒了     几点几分几秒了    1
 我会想你的亲爱的     我会想你的亲爱的    1
 我给你唱个歌要不要     我给你唱个歌要不要    1
 我也不是你喜欢的类型     我也不是你喜欢的类型    1
 帮我推荐一首歌吧     帮我推荐一首歌吧    1
 下个月这个时候吧     下个月这个时候吧    1
 打电话给刘华平     打电话给刘华平    1
 你们明天几点上班啊     你们明天几点上班啊    1
 你太让我伤心了     你太让我伤心了    1
 发张照片来看看嘛     晚上照片来看看吧    0.625
 不然不知道吃什么     不然不知道吃什么    1
 中央军委主席现在是谁     中央军委主席现在是谁    1
 从厦门动车站到泉州要多少钱     从厦门动车站到泉州要多少钱    1
 没有女人没睡好     没有女人没睡好    1
 我不想看我想你告诉我     我不想看我想你告诉我    1
 世上只有妈妈好妈妈不在爸爸好除了他们你最好     世上只有妈妈好妈妈不在爸爸好除了他们你最好    1
 如果有一天你累了     如果有一天你累了    1
 那你也不给我说一声     那你也不跟我说一声    0.88888889
 那你认识我老婆吗     那你认识我老婆吗    1
 海通证券上海合肥路营业部     海通证券上海合肥路营业部    1
 明天什么时候回去     明天什么时候回去    1
 播放早开的晚霞     播放早开的晚霞    1
 你是个很好的女人     你是个很好的女人    1
 我家淘宝上新款啦     我家淘宝上新款啦    1
 你这么快就到家了     你这么快就到家了    1
 如何帮女生挑选内衣和小可爱     如何帮女生挑选内衣和小可爱    1
 自己都不心疼自己     自己都不心疼自己    1
 有哪些设置无线的方法     有哪些设置无线的方法    1
 你怎么还不去上班     你怎么还不去上班    1
 这个活动免费吗九江     这个活动免费吗九江    1
 我也想天天和你在一起     我也想天天和你在一起    1
 真不知道该怎么说了     真不知道该怎么说了    1
 英雄不问出处     英雄不问出处    1
 帮我记录搜狐     帮我记录搜狐    1
 今天就要回学校了     今天就要回学校了    1
 你那有什么服务价格多少     你那里有什么服务价格多少    0.90909091
 我不会让你受伤的     我不会让你受伤的    1
 这是哪里有好玩的地方     这是哪里有好玩的地方    1
 你觉得我像坏人吗     你觉得我像坏人吗    1
 再不行就没办法了     再不行就没办法了    1
 盐城工学院博雅学院     盐城工学院博雅学院    1
 华夏学院     华夏学院    1
 二十一号是世界末日吗     二十一号是世界末日吗    1
 放几首网络歌曲     放几首网络歌曲    1
 嗯你明天去医院看看     嗯你明天去医院看看    1
 今天深圳到襄阳的机票     今天深圳到襄阳的机场    0.9
 什么时候到家的呀     什么时候到家的呀    1
 设置八点叫我起床     十八点叫我起床    0.75
 广东工业大学龙洞校区     广东工业大学龙洞校区    1
 我说你是不是傻     我说你是不是傻    1
 老婆你今天不理我     老婆你今天不理我    1
 冬虫夏草出产地在哪里     冬虫夏草出产地在哪里    1
 大朗到广州坐什么车     大朗到广州坐什么车    1
 你是不是换电话了     你是不是换电话了    1
 溜冰鞋多少钱一双     溜冰鞋多少钱一双    1
 我晚上不回去吃了     我晚上不回去吃了    1
 是我要求的太多了     是我要求的太多了    1
 你说什么对不起啊     你说什么对不起啊    1
 我不是你男朋友吗     我不是你男朋友吗    1
 周末大扫除没空啊     周末大扫除没空    0.875
 还有你不敢的事     还有你不敢的事    1



