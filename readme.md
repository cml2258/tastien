# 塔斯汀小程序模仿项目
- 本项目归塔斯汀所有， 只做学习所用， 请尊重原厂版权
- fiddler 抓包工具抓取图片

- 界面模仿采用markman做标记
  1. 我们没有设计稿，如何使用1：1 还原小程序？
  2. 拍屏得到小程序截图
  3. 使用在线大小[转换工具](https://www.gaitubao.com/)，将图片改成750 以后在写wxss的时候，直接量像素就可以写进去，因为小程序以750rpx作为设计稿标准大小帮助我们自动适配，很好用。
  4. 使用[markman](http://www.getmarkman.com/) 先标记，再写样式
    以后呢，上班就不用了，有设计师给标记好。
    现在，让我们中自己来 LOL 吧

- 项目配置在根目录下app.json
  - 隐藏并定制 navigationBar
    "navigationStyle": "custom"
  - 启动权限 定位功能

- 使用BEM 国际css命名规范
  tst_banners 广告位 Block
  tst_banners Element

- css 技巧
  1. 能不用定位就不要用定位
    脱离文档流 降低性能
  2. 移动端多用弹性布局（父元素和多个子元素之间关系）

- git 提交 
  - 第一次git 命令行提交
      git  git config --global user.name "名字"
                  git config --global user.eamil "邮箱"
      初始化项目，变成git项目   git init
                              git add .
                              git  commit -m 'first commit'
      git remote add origin https://github.com/cml2258/tastien.git 和远程联系起来
      git push -u origin master
      提交成功

    全局配置
  1. 
    git config --global http.sslVerify false
    git config --global user.name "shunwuyu"  换成你的github 名字
    git config --global user.email "shunwu2001@163.com" 换成你的github 注册邮箱

  2.  ssh-keygen -t rsa -C '邮箱'  换成你在上面填的邮箱   
    一路回车   会在 C:\Users\86199\.ssh\       86199 你的目录下
    cat id_rsa.pub   选中所有的输出内容
    打开网页  https://github.com/settings/profile
    https://github.com/settings/keys
    点击 New SSH key
    title 随便取   Key  设置为
    刚刚选中的内容
    点击添加
  3. 回到 项目目录   /tastien
    git init    如果之前初始化过 忽略
    git  add .   
    git  commit -m 'first commit'
    git push -u origin master

    上传成功， git 能看到本地代码成功

- 滴滴swiper 多页活动菜单功能 可变高度的
   用户体验问题  less is more
    菜单太多，用户的密集恐惧症， 把重要的放在首页
    其他的可以多放一些
    （为用户创造体验 不显得臃肿 看的少一些，解决的多一些
    先放两行 后放三行）

   技术难度
   1. swiper > 2 swiper-item
   2. swiper 高度 变化的   等高的
    2行
    4行高度
    swiper height 响应式的数据
  3. class="didi_menus {{'higher_menus'}}" 
    占位符{{}} 返回值是替换的值
    js运行区域
  4. swiper bindchange  事件
    event 对象中 （事件发生就有event对象）
      event.detail.current 当前是第几个swiper-item?
      menu_type
      this.setData()
- 数据响应式编程
  它是一个思想，有别于DOM编程API
  设置一些页面效果，操作的不是DOM，
  操作是数据，因为数据一旦发生变化，页面会自动刷新。
  1. 滴滴可变高度的首页菜单
  2. tabbar 组件
    data 添加 tab属性 ，表示当前哪个tab被激活
    tab-item 添加bindtap 事件
    tab-item data-tab 数据属性 data-  （给html标签添加数据，会在dataset里面）
    e.currentTarget 点击当前元素
    e.currentTarget.dataset.tab数据
  3. 外卖品类级菜单数据设计
    2 个scroll-view, 数据具有相关性
    2层嵌套的json解构
    分类数组：[
      
      {
        菜品数组：[
          ...
        ]
      }
    ]
- css的技巧
  1. 选择器优先级 会相加的
        后代选择器（空格） 指定元素后代的所有元素 
            div p{

            }
        子选择器（>）指定元素子元素的所有元素
            div > p{

            }
        相邻兄弟选择器（+）指定元素的相邻同级的元素 元素必须具有相同的父元素，“相邻”的意思是“紧随其后”
            div + p{

            }
            紧随div的，且具有想同父元素的p元素
        通用兄弟选择器（~）
            div ~ p{

            }
    p.md2  11
    p.md2 + div.md2  11+11 22
    标签 1分< 类名 10分< id 100分< 计算表达式
    行内样式，优先级更高 少用
     ！important 最高 慎用
  2. 弹性布局
    移动端 flex 可以解决大部分问题
    div 块级
    布局的其中一种 跟外部不一样的布局，桃花源记
    flex 内部   块级能力丢失  BFC
    Block formating content 格式化的环境
  3. BEM 国际命名规范
    Block 开始 rx_tab 新的组件
    Element 内部元素的声明 rx_tab__item
    Modifier rx_tab__item-on 某种状态 '-'中横线

- 