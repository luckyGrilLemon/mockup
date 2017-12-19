# 魔卡——高保真原型交付工具

虽然已经提倡前后端开发分离很几年了，但由于历史原因和显示原因，还有很多团队还是传统后端开发套页面方式。

此时，前端页面重构人员需要交付的是HTML静态页面。

然而，普通静态HTML页面不少问题，例如头尾无法公用，20多个页面，如果公用头部变化了，一改该好多地方，累！
ajax请求无法模拟，想要模拟需要自己装环境。好不容易自己这边跑顺了，结果开发那边预览时候又有问题，无论你用Apache还是iis模拟，开发那边不一定要同样环境。

这样的痛点促使了“魔卡”的出现。

## 功能简介

* HTML import功能，头部和尾部可以公用啦
* 基于文件夹的CSS和JS资源合并
* 支持qcss快速书写
* 本地http环境一键开启，post/get请求轻松模拟

## 其它简要说明

### 目录结构
./src/  为开发目录
./dist/ 为生成目录，原型预览，和静态资源交付都在这个文件夹下

### 原型预览
1. 可以直接双击./dist/views/html/*.html文件预览，但无法显示ajax请求交互效果。
2. 如果希望看到请求交互效果，需要跑下run.js，然后：http://127.0.0.1:2017/views/html/*.html 访问。这里2017是可变的，基于当前年份设置的。

### 开发说明

./src/目录下开发。

开发时候需要跑下run.js，步骤如下：

1. 安装[node.js](https://nodejs.org/zh-cn/)
2. 命令行node run。windows系统可以双击run.bat

run.js这个node.js脚本纯原生，不依赖任何包，直接执行即可！

执行后会自动开启watch，以及本地服务功能。

### TO后端开发
注意！联调或者是项目上线后的日常维护，只能修改./src/目录下CSS和JS，dist目录下的是工具合并生成的，如果修改，日后会被覆盖。

## 详细说明

### 一些注意事项

* 参照项目示意文件结构进行开发，css, js, images, html等目录名称和层级是不能调整的，否则run.js会跑不起来。如果进行了修改，需要同步修改run.js相关路径。
* css, js及其以下子目录，目前仅支持1级文件夹结构，名称可以任意。
* images文件夹下目录层级任意。

### 合并规则说明

先说说为什么要合并。

合并规则具体：

...
