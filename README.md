# PDF.js

PDF.js is a Portable Document Format (PDF) viewer that is built with HTML5.

PDF.js是使用HTML5构建的便携式文档格式（PDF）查看器。

PDF.js is community-driven and supported by Mozilla Labs. Our goal is to
create a general-purpose, web standards-based platform for parsing and
rendering PDFs.
PDF.js是社区驱动的，由Mozilla实验室支持。 我们的目标是创建一个通用的基于Web标准的平台，用于解析和呈现PDF。

## Contributing

PDF.js is an open source project and always looking for more contributors. To
get involved, visit:
PDF.js是一个开源项目，一直在寻找更多的贡献者。 要参与，请访问：

+ [Issue Reporting Guide](https://github.com/mozilla/pdf.js/blob/master/.github/CONTRIBUTING.md)
+ [Code Contribution Guide](https://github.com/mozilla/pdf.js/wiki/Contributing)
+ [Frequently Asked Questions](https://github.com/mozilla/pdf.js/wiki/Frequently-Asked-Questions)
+ [Good Beginner Bugs](https://github.com/mozilla/pdf.js/issues?direction=desc&labels=5-good-beginner-bug&page=1&sort=created&state=open)
+ [Projects](https://github.com/mozilla/pdf.js/projects)

Feel free to stop by #pdfjs on irc.mozilla.org for questions or guidance.
在irc.mozilla.org上的#pdfjs随时停下来提问或指导。

## Getting Started 入门

### Online demo 在线示例

+ https://mozilla.github.io/pdf.js/web/viewer.html

### Browser Extensions 浏览器扩展

#### Firefox (and Seamonkey)

PDF.js is built into version 19+ of Firefox, however, one extension is still available:

+ [Development Version](http://mozilla.github.io/pdf.js/extensions/firefox/pdf.js.xpi) - This extension is mainly intended for developers/testers, and it is updated every time new code is merged into the PDF.js codebase. It should be quite stable but might break from time to time.
此扩展主要面向开发人员/测试人员，每当新代码合并到PDF.js代码库中时，它将被更新。 它应该是相当稳定的，但可能会不时打破。

  + Please note that the extension is *not* guaranteed to be compatible with Firefox versions that are *older* than the current ESR version, see the [Release Calendar](https://wiki.mozilla.org/RapidRelease/Calendar#Past_branch_dates).
  请注意，扩展名为*不*保证与现有ESR版本的*旧版本的Firefox版本兼容，请参阅

  + The extension should also work in Seamonkey, provided that it is based on a Firefox version as above (see [Which version of Firefox does SeaMonkey 2.x correspond with?](https://wiki.mozilla.org/SeaMonkey/FAQ#General)), but we do *not* guarantee compatibility.
  扩展程序也应该在Seamonkey中工作，只要它基于上面的Firefox版本（参见[SeaMonkey 2.x与哪个版本的Firefox相对应？]，但我们做*不*保证兼容性。

#### Chrome

+ The official extension for Chrome can be installed from the [Chrome Web Store](https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm).
Chrome的官方扩展程序可以从[Chrome网上应用店]安装
*This extension is maintained by [@Rob--W](https://github.com/Rob--W).*
此扩展由[@Rob--W]
+ Build Your Own - Get the code as explained below and issue `gulp chromium`. Then open
Chrome, go to `Tools > Extension` and load the (unpackaged) extension from the
directory `build/chromium`.
构建您自己的 - 获取如下所述的代码，并发出“gulp铬”。 然后打开
Chrome，请转到“工具>扩展”，然后从中加载（未打包的）扩展名
目录`build / chromium`。

## Getting the Code 获取代码

To get a local copy of the current code, clone it using git:
要获取当前代码的本地副本，请使用git克隆它：

    $ git clone git://github.com/mozilla/pdf.js.git
    $ cd pdf.js

Next, install Node.js via the [official package](http://nodejs.org) or via
[nvm](https://github.com/creationix/nvm). You need to install the gulp package
globally (see also [gulp's getting started](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md#getting-started)):
接下来，通过[官方软件包]（http://nodejs.org）或通过安装Node.js
[NVM]（https://github.com/creationix/nvm）。 你需要安装gulp包
（参见[gulp的入门]）

    $ npm install -g gulp-cli

If everything worked out, install all dependencies for PDF.js:
如果一切顺利，请安装PDF.js的所有依赖项：

    $ npm install

Finally, you need to start a local web server as some browsers do not allow opening
PDF files using a `file://` URL. Run:
最后，您需要启动本地Web服务器，因为某些浏览器不允许打开
使用“file：//”URL的PDF文件。 运行：

    $ gulp server

and then you can open:
然后你可以打开：

+ http://localhost:8888/web/viewer.html

Please keep in mind that this requires an ES6 compatible browser; refer to [Building PDF.js](https://github.com/mozilla/pdf.js/blob/master/README.md#building-pdfjs) for usage with older browsers.
请记住，这需要一个ES6兼容的浏览器; 请参阅[构建PDF.js]以用于旧版浏览器。

It is also possible to view all test PDF files on the right side by opening:
也可以通过打开右侧的方式查看右侧的所有测试PDF文件：

+ http://localhost:8888/test/pdfs/?frame

## Building PDF.js 构建PDF.js

In order to bundle all `src/` files into two production scripts and build the generic
viewer, run:
为了将所有`src /`文件捆绑成两个生产脚本并构建通用的
查看器，运行：

    $ gulp generic

This will generate `pdf.js` and `pdf.worker.js` in the `build/generic/build/` directory.
Both scripts are needed but only `pdf.js` needs to be included since `pdf.worker.js` will
be loaded by `pdf.js`. The PDF.js files are large and should be minified for production.
这将在`build / generic / build /`目录中生成`pdf.js`和`pdf.worker.js`。
这两个脚本都是必需的，但是只有`pdf.js`需要包括在内，因为`pdf.worker.js`将会
由`pdf.js`加载。 PDF.js文件很大，应该细化生产。

## Using PDF.js in a web application 在Web应用程序中使用PDF.js

To use PDF.js in a web application you can choose to use a pre-built version of the library
or to build it from source. We supply pre-built versions for usage with NPM and Bower under
the `pdfjs-dist` name. For more information and examples please refer to the
[wiki page](https://github.com/mozilla/pdf.js/wiki/Setup-pdf.js-in-a-website) on this subject.
要在Web应用程序中使用PDF.js，您可以选择使用库的预构建版本
或从源代码构建它。 我们提供用于NPM和Bower的预制版本
`pdfjs-dist`的名字。 有关更多信息和示例，就此问题请参阅[wiki页]。

## Learning 学习

You can play with the PDF.js API directly from your browser using the live demos below:
您可以使用下面的现场演示直接从浏览器播放PDF.js API：

+ [Interactive examples](http://mozilla.github.io/pdf.js/examples/index.html#interactive-examples)

The repository contains a hello world example that you can run locally:
存储库包含一个您可以在本地运行的hello world示例：

+ [examples/helloworld/](https://github.com/mozilla/pdf.js/blob/master/examples/helloworld/)

More examples can be found in the examples folder. Some of them are using the pdfjs-dist package, which can be built and installed in this repo directory via `gulp dist-install` command.
更多示例可以在examples文件夹中找到。 其中一些使用pdfjs-dist软件包，可以通过`gulp dist-install`命令构建并安装在这个repo目录中。

For an introduction to the PDF.js code, check out the presentation by our
contributor Julian Viereck:
有关PDF.js代码的介绍，请查看我们的演示文稿
贡献者Julian Viereck：

+ http://www.youtube.com/watch?v=Iv15UY-4Fg8

More learning resources can be found at:
更多学习资源可以在以下网址找到：

+ https://github.com/mozilla/pdf.js/wiki/Additional-Learning-Resources

## Questions 问题

Check out our FAQs and get answers to common questions:
查看我们的常见问题解答并获得常见问题的答案：

+ https://github.com/mozilla/pdf.js/wiki/Frequently-Asked-Questions

Talk to us on IRC:
在IRC上与我们交谈：

+ #pdfjs on irc.mozilla.org

File an issue:
提出问题：

+ https://github.com/mozilla/pdf.js/issues/new

Follow us on twitter: @pdfjs
在Twitter上关注我们：@pdfjs

+ http://twitter.com/#!/pdfjs
