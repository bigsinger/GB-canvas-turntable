# GB-canvas-turntable

>

---

## 简介

基于 Canvas 绘制、可配置奖项的转盘抽奖

## 演示 & 文档

<https://blog.givebest.cn/GB-canvas-turntable.html>

## 使用

### Browser

```html
<link rel="stylesheet" href="css/GB-canvas-turntable.css" />
<script src="js/GB-canvas-turntable.js"></script>
```

### 普通

```js
gbTurntable.init({
  id: "turntable",
  config: function (callback) {
    // 获取奖品信息
    // 奖项 text 属性不能为空，用于显示或抽中奖品提示
    // img 为奖品图片地址，如果不为空则转盘奖品按图片方式显示
    callback &&
      callback([
        {
          text: "1元红包",
          img: "images/redpacket.png",
        },
        {
          text: "2元红包",
        },
        {
          text: "3元红包",
        },
        {
          text: "显示器",
          img: "images/display.png",
        },
        {
          text: "5元红宝",
        },
        {
          text: "6元红宝",
        },
      ]);
  },
  getPrize: function (callback) {
    // 获取中奖信息
    var num = (Math.random() * 6) >>> 0, //奖品ID
      chances = num; // 可抽奖次数
    callback && callback([num, chances]);
  },
  gotBack: function (data) {
    alert("恭喜抽中" + data);
  },
});
```

## 感谢他们

演示网页排版来自： [https://github.com/sofish/typo.css](https://github.com/sofish/typo.css)

## License

[MIT](./LICENSE) © 2020 [givebest](https://github.com/givebest)

# 扩展

本项目fork自：<https://github.com/leijee/GB-canvas-turntable>


为了方便使用，计划部署到网站上而不是使用小程序，这样可以跨平台多端使用，也规避了麻烦的上架流程。但是这样也会带来一个新的问题，那就是配置转盘选项的时候会比较麻烦，因此想到了一个方案，那就是预制一些选项的使用场景，然后当我访问网址的时候携带上参数，通过参数来选取不同的场景，这样就方便使用了。这些场景配置都配置到html文件同级目录下的sln子文件夹下面。 目前想到的场景有：

1. 孩子奖励，选项：红包1元 红包2元 红包3元 户外玩耍 周边游 iPad30分钟 iPad10分钟 iPad20分钟；
2. 孩子惩罚，选项：丢垃圾 洗碗 当日无电视 当日无iPad 作业1页 作业2页 唐诗1首；
3. 学生奖励，选项：免作业1次 铅笔1个 钢笔1个 圆珠笔1个 作业1套；

其他场景自行发挥。

## 代码编写

咨询GPT完成。

## 部署

上传`src`目录下的所有文件及文件夹到服务器。

- 测试：访问如下的网址即可使用，手机电脑上均可。

```
https://xxxqqq.com/diy/choujiang/go.html?scene=kids_reward
https://xxxqqq.com/diy/choujiang/go.html?scene=kids_punish
https://xxxqqq.com/diy/choujiang/go.html?scene=students_reward
```

## 更新

参考如下的json格式进行修改即可，默认每个选项的概率是均等的。

```json
{
  "name":"奖励抽奖",
  "prizes":[
    { "text": "谢谢惠顾" },
    { "text": "红包1元" },
    { "text": "红包2元" },
    { "text": "红包3元" },
    { "text": "户外玩耍" },
    { "text": "周边游" },
    { "text": "iPad30分钟" },
    { "text": "iPad10分钟" },
    { "text": "iPad20分钟" }
  ]
}
```

如果想要调整概率，可以增加`weight`字段，这个权重是倍乘系数，如果不会用的话，建议可以采用整体百分制，然后拆分到各个选项即可，例如：

```json
{
  "name":"奖励抽奖",
  "prizes":[
    { "text": "谢谢惠顾" , "weight":20},
    { "text": "红包1元" , "weight":10},
    { "text": "红包2元" , "weight":10},
    { "text": "红包3元" , "weight":10 },
    { "text": "户外玩耍" , "weight":10 },
    { "text": "周边游" , "weight":10 },
    { "text": "iPad30分钟" , "weight":10 },
    { "text": "iPad10分钟" , "weight":10 },
    { "text": "iPad20分钟" , "weight":10 }
  ]
}
```

## 新增

参考如上的`json`配置，在`sln`目录下创建一个名称为`xxx.json`的文件，然后访问网址即可生效

```
https://xxxqqq.com/diy/choujiang/go.html?scene=xxx
```
