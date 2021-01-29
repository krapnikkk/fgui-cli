## 写在前面

<font size=4>本工程仅作学习研究使用，本意用于工程项目不幸破损，通过发布出来的资源文件进行紧急还原，请勿用于资源破解侵权等行为，否则后果自负！！</font>

## 下载

```
git clone git@github.com:krapnikkk/fgui-restore.git
```

## 安装 

```sh
npm install
```
## 使用方法

```
node restore ./test/MainMenu.bin ./output 
```

## 支持版本

数据版本 [向下兼容] : buffer.version： 5

编辑器版本：[FairyGUI Editor: 2020.3.3](https://fairygui.com/product.html)

【已测试官方DEMO工程99%高度还原，还原出来的包资源文件推荐使用最新版编辑器打开】

### 还原程度
 - 将合并的纹理图片还原成碎图【统一png格式】
 - 将碎图和package.xml关联绑定
 - 将组件xml和package.xml关联绑定
 - 将动画Movieclip还原成jta文件【动画设置以帧频：24为基准进行还原】
 - 将位图字体文件还原成fnt文件【二进制格式资源包统一还原成UIBuilder默认格式】
 
  
### 无法还原项
 - 骨骼动画资源还原
 - 项目设置中的默认设置项
 - 不被打包合并的资源或者不支持的资源【比如:swf,仅单纯放置到包内】
 - 设计辅助功能配置【比如:[组件]组件设计图、元件保持比例和背景颜色[装载器]发布时清除等】
 - 普通组元件无法还原
 - 部分数值由于浮点数精度问题会有一位小数上的偏差

### 资源文件内容一览
 - package.xml
 - sprites.bytes
 - .xml
 - .fnt
 - .jta

## xml解析流程
 - 解析发布出来的资源文件
 - 根据文件格式版本分布解析二进制和压缩描述文件
 - 将发布的资源文件解析还原为xml
 - 【image】图片资源根据id还原name 和 文件路径 packageDescription.resources[0].image
 - 【movieclip】packageDescription.resources[0].movieclip
 - 【sound】packageDescription.resources[0].sound

## 文件解析流程
 - createObject 【UIPackage】
 - constructFromResource【 GComponent | GImage | GMovieClip 】
 - controller.setup【controller】
 - setup_beforeAdd 【component-child-GObject】
 - relations.setup【relations】
 - setup_afterAdd 【component-child-GObject】
 - gear.setup 【GObject】
 - trans.setupp 【transion】
 - constructExtension 【extension】

## todo list [maybe]
 [x] 【组件】组件自定义属性还原
 [x] 【组件】组件出入场音效还原
 [x] 【组件】属性控制中对原始属性的判断进行还原
 [x] 【标签】标签中的标题为输入文本相关属性还原
 [x] branch分支相关逻辑处理
 [x] fnt文件初始化完善
 [x] 校验需要还原文件的合法性&合理性及异常处理
 [x] 浮点数数值精准还原
 [x] 属性默认值及属性顺序精准还原
 [x] BMFont字体文件还原
 [x] and more

### License ###
MIT
