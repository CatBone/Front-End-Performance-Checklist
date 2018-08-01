<h1 align="center">
<br>
  <img src="https://raw.githubusercontent.com/thedaviddias/Front-End-Performance-Checklist/master/images/logo-front-end-performance-checklist.jpg" alt="Front-End Performance Checklist" width="170">
  <br>
    <br>
  前端性能清单
  <br>
</h1>

<h4 align="center">🎮 前端性能清单，让你的网站跑的更快</h4>
<p align="center">单一原则: "在设计和编写时考虑到性能"</p>

<p align="center">
  <a href="http://makeapullrequest.com">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome">
  </a>
  <a href="https://gitter.im/Front-End-Checklist/Lobby?utm_source=share-link&utm_medium=link&utm_campaign=share-link">
    <img src="https://img.shields.io/badge/chat-on_gitter-008080.svg?style=flat-square" alt="Gitter">
  </a>
    <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square" alt="Licence MIT">
  </a>
</p>

<p align="center">
  <a href="#how-to-use">How To Use</a> • <a href="#contributing">Contributing</a> • <a href="https://www.producthunt.com/posts/front-end-performance-checklist">Product Hunt</a>
</p>
<p align="center">
    <span>其他清单：</span>
    <br>
  🗂 <a href="https://github.com/JohnsenZhou/Front-End-Checklist">Front-End Checklist</a> • 💎 <a href="https://github.com/JohnsenZhou/Front-End-Design-Checklist">Front-End Design Checklist</a>
</p>

## 目录

1. **[HTML](#html)**
2. **[CSS](#css)**
3. **[Fonts](#fonts)**
4. **[Images](#images)**
5. **[JavaScript](#javascript)**
6. **[Server](#server) (梳理中)**
7. **[JS Frameworks](#js-frameworks) (梳理中)**

## 概述

性能是一个很大的主题，但它并不总是一个“后端”或“管理（admin）”所要考虑的主题：它也是一个前端需要考虑的。作为前端开发人员，前端性能清单是你在项目中应该检查或者至少需要注意的性能要点的详尽列表。

### 如何使用?

对于每个规则，将有一个段落解释**为什么**此规则很重要以及**如何**解决它。有关更深入的信息，可相应找到可指向的🛠工具，📖文章或📹媒体的链接，以便梳理。

前端性能清单中的所有项目都是获得最高性能得分的基本要素，但是你可以找到一些指标来帮助你最终确定一些规则的优先顺序。以下有3个级别的优先级：

* ![Low][low] 表示该项目的优先级**较低**，对项目有影响。
* ![Medium][medium] 表示该项目具有**中等优先级**并对项目产生影响，开发时需要处理这些项目。
* ![High][high] 表示该项目具有**高优先级**并对项目产生影响，开发时必须要处理这些项目，不然性能将大打折扣。

### 性能测试工具

以下是一些您可以用来测试或监控您的网站或应用程序的工具：

 * 🛠 [WebPagetest - Website Performance and Optimization Test](https://www.webpagetest.org/)
 * 🛠 ☆ [Dareboost: Website Speed Test and Website Analysis](https://www.dareboost.com/) (use the coupon WPCDD20 for -20%)
 * 🛠 [GTmetrix | Website Speed and Performance Optimization](https://gtmetrix.com/)
 * 🛠 [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
 * 🛠 [Pingdom Website Speed Test](https://tools.pingdom.com)
 * 📖 [Pagespeed - The tool and optimization guide](https://varvy.com/pagespeed/)
 * 📖 [Make the Web Faster | Google Developers](https://developers.google.com/speed/)
 * 🛠 [Sitespeed.io - Welcome to the wonderful world of Web Performance](https://www.sitespeed.io/)
 * 🛠 [Calibre](https://calibreapp.com/)

### 参考

 * 📖 [The Cost Of JavaScript - YouTube](https://www.youtube.com/watch?v=_bzqF05xsC4)
 * 📖 [Get Started With Analyzing Runtime Performance  |  Google Developers](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/)
 * 📖 [State of the Web | 2018_01_01](https://httparchive.org/reports/state-of-the-web?start=2018_01_01)
 * 📖 [Page Weight Doesn't Matter](https://www.speedshop.co/2015/11/05/page-weight-doesnt-matter.html)
---

## HTML

![html]

- [ ] **压缩 HTML:** ![medium] HTML代码压缩，将注释、空格和新行从生产文件中删除。

    *为什么：*
    > 删除所有不必要的空格、注释和中断行将减少HTML的大小，加快网站的页面加载时间，并显著减少用户的下载时间。

    *怎么做：*
    > 大多数框架都有插件用来压缩网页的体积。你可以使用一组可以自动完成工作的NPM模块。

    * 🛠 [HTML minifier | Minify Code](http://minifycode.com/html-minifier/)
    * 📖 [Experimenting with HTML minifier — Perfection Kills](http://perfectionkills.com/experimenting-with-html-minifier/#use_short_doctype)

- [ ] **删除不必要的注释：** ![low] 确保从您的网页中删除注释。

    *为什么：*
    > 注释对用户来说是没有用的，应该从生产环境文件中删除。可能需要保留注释的一种情况是：保留远端代码库（keep the origin for a library）。

    *怎么做：*
    > 大多数情况下，可以使用HTML minify插件删除注释。

 * 🛠 [remove-html-comments - npm](https://www.npmjs.com/package/remove-html-comments)

- [ ] **删除不必要的属性：** ![low] 像 `type="text/javascript"` or `type="text/css"` 这样的属性应该被移除。

    ```html
    <!-- Before HTML5 -->
    <script type="text/javascript">
        // Javascript code
    </script>

    <!-- Today -->
    <script>
        // Javascript code
    </script>
    ```

    *为什么*
    > 类型属性不是必需的，因为HTML5把text/css和text/javascript作为默认值。没用的代码应在网站或应用程序中删除，因为它们会使网页体积增大。

    *怎么做：*
    > ⁃ 确保所有`<link>`和`<script>`标记都没有任何type属性。

    * 📖 [The Script Tag | CSS-Tricks](https://css-tricks.com/the-script-tag/)
   
- [ ] **在JavaScript引用之前引用CSS标记：** ![high] 确保在使用JavaScript代码之前加载CSS。

    ```html
    <!-- 不推荐 -->
    <script src="jquery.js"></script>
    <script src="foo.js"></script>
    <link rel="stylesheet" href="foo.css"/>

    <!-- 推荐 -->
    <link rel="stylesheet" href="foo.css"/>
    <script src="jquery.js"></script>
    <script src="foo.js"></script>
    ```

    *为什么：*
    > 在引用JavaScript之前引用CSS可以实现更好地并行下载，从而加快浏览器的渲染速度。

    *怎么做：*
    > 确保`<head>`中的`<link>`和`<style>`始终位于`<script>`之前。

    * 📖 [合理安排styles和scripts来提高网页速度](https://varvy.com/pagespeed/style-script-order.html)

- [ ] **最小化iframe的数量：** ![high] 仅在没有任何其他技术可行性时才使用iframe。尽量避免使用iframe。

**[⬆ 返回顶部](#table-of-contents)**

## CSS

![css]

- [ ] **压缩:** ![high] 所有CSS文件都需要被压缩，从生产文件中删除注释，空格和空行。

    *为什么：*
    > 缩小CSS文件后，内容加载速度更快，并且将更少的数据发送到客户端，所以在生产中缩小CSS文件是非常重要，这对用户是有益的，就像任何企业想要降低带宽成本和降低资源。

    *怎么做：*
    > 使用工具在构建或部署之前自动压缩文件。

    * 🛠 [cssnano: 基于PostCSS生态系统的模块化压缩工具。](https://cssnano.co/)
    * 🛠 [@neutrinojs/style-minify - npm](https://www.npmjs.com/package/@neutrinojs/style-minify)

- [ ] **Concatenation:** ![medium] CSS文件合并（对于HTTP/2效果不是很大）。

    ```html

    <!-- 不推荐 -->
    <link rel="stylesheet" href="foo.css"/>
    <link rel="stylesheet" href="bar.css"/>

    <!-- 推荐 -->
    <link rel="stylesheet" href="foobar.css"/>
    ```

    *为什么：*
    > 如果你还在使用HTTP/1，那么你就需要合并你的文件。不过在使用HTTP/2的情况下不用这样（效果待测试）。

    *怎么做：*
    > 在构建或部署之前使用在线工具或者其他插件来合并文件。
    > 当然，要确保合并文件后项目可以正常运行。

    * 📖 [HTTP: 优化应用程序交付 - 高性能浏览器网络 (O'Reilly)](https://hpbn.co/optimizing-application-delivery/#optimizing-for-http2)
    * 📖 [HTTP/2时代的性能最佳实践](https://deliciousbrains.com/performance-best-practices-http2/)

- [ ] **非阻塞：** ![high] CSS文件需要非阻塞引入，以防止DOM花费更多时间才能渲染完成。

    ```html
    <link rel="preload" href="global.min.css" as="style" onload="this.rel='stylesheet'">
    <noscript><link rel="stylesheet" href="global.min.css"></noscript>
    ```

    *为什么：*
    > CSS文件可以阻止页面加载并延迟页面呈现。使用`preload`实际上可以在浏览器开始显示页面内容之前加载CSS文件。

    *怎么做：*
    > 需要添加`rel`属性并赋值`preload`，并在`<link>`元素上添加`as=“style”`。

    * 📖 [loadCSS by filament group](https://github.com/filamentgroup/loadCSS)
    * 📖 [使用loadCSS预加载CSS的示例](https://gist.github.com/thedaviddias/c24763b82b9991e53928e66a0bafc9bf)
    * 📖 [使用rel =“preload”预加载内容](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
    * 📖 [Preload: What Is It Good For? — Smashing Magazine](https://www.smashingmagazine.com/2016/02/preload-what-is-it-good-for/)

- [ ] **CSS类(class)的长度:** ![low] class的长度会对HTML和CSS文件产生（轻微）影响。

    *为什么：*
    > 甚至性能影响也是有争议的，项目的命名策略会对样式表的可维护性有重大影响。如果使用BEM，在某些情况下可能会写出比所需要的类名更长的字符。重要的是要明智的选择名字和命名空间。

    *怎么做：*
    > 可能有些人更关注类名的长度，但是网站按组件进行划分的话可以帮助减少类名的数量和长度。

    * 🛠 [long vs short class · jsPerf](https://jsperf.com/long-vs-short-class)

- [ ] **不用的CSS:** ![medium] 删除未使用的CSS选择器。

    *为什么：*
    > 删除未使用的CSS选择器可以减小文件的大小，提高资源的加载速度。

    *怎么做：*
    > ⚠️ 检查要使用的CSS框架是否已包含reset/normalize代码，可能不需要用到reset/normalize文件中的内容。

    * 🛠 [UnCSS Online](https://uncss-online.com/)
    * 🛠 [PurifyCSS](https://github.com/purifycss/purifycss)
    * 🛠 [PurgeCSS](https://github.com/FullHuman/purgecss)
    * 🛠 [Chrome DevTools Coverage](https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage)

* [ ] **关键CSS（Critical）:** ![high] 将页面渲染时必备的CSS通过```<style></style>```的方式内联到页面中（尽可能压缩后引用）。

    *为什么：*
    > 内联关键CSS有助于加速网页的呈现，减少对服务器的请求数量。

    *怎么做：*
    > 使用在线工具或使用Addy Osmani开发的插件生成关键CSS。

    * 📖 [理解关键CSS](https://www.smashingmagazine.com/2015/08/understanding-critical-css/)
    * 🛠 [Critical by Addy Osmani on GitHub](https://github.com/addyosmani/critical) automates this.
    * 📖 [Inlining critical CSS for better web performance | Go Make Things](https://gomakethings.com/inlining-critical-css-for-better-web-performance/)
     * 📖 [Critical Path CSS Generator - Prioritize above the fold content :: SiteLocity](https://www.sitelocity.com/critical-path-css-generator)

- [ ] **嵌入或内联CSS：** ![high] 避免在<body>中使用嵌入或内联CSS*（对HTTP/2无效）*

    *为什么：*
    > 因为将内容与设计分开是一种很好的做法。它还可以提高代码的可维护性并使站点可访问性更强。对于性能来说，它只是减少了HTML页面的文件大小和加载时间。

    *怎么做：*
    > 始终使用外部样式表或在<head>中嵌入CSS（并遵循其他CSS性能规则）。

    * 📖 [Observe CSS Best Practices: Avoid CSS Inline Styles](https://www.lifewire.com/avoid-inline-styles-for-css-3466846)

- [ ] **分析样式表的复杂性：** ![high] 分析样式表有助于发现有问题的、冗余和重复的CSS选择器。

    *为什么：*
    > 有时在CSS中会出现冗余或验证错误，分析CSS文件并删除这些复杂性的代码可以加速CSS文件的读取和加载（因为您的浏览器会更快地读取它们）

    *怎么做：*
    > CSS需要有编写规范，再通过CSS预处理器处理。下面列出的一些在线工具也可以帮助你分析和更正你的代码。
    
    * 🛠 [TestMyCSS | 优化和检查CSS性能](http://www.testmycss.com/)
    * 📖 [CSS 统计数据（stats）](https://cssstats.com/)
    * 🛠 [macbre/analyze-css: CSS选择器复杂性和性能分析](https://github.com/macbre/analyze-css)

**[⬆ 返回顶部](#table-of-contents)**

## 字体

![fonts]

* 📖 [A Book Apart, Webfont Handbook](https://abookapart.com/products/webfont-handbook)

- [ ] **Webfont格式：** ![medium] 在你的网站或者应用使用WOFF2格式字体。

    *为什么：*
    > 根据Google的说法，WOFF 2.0 Web字体压缩格式平均比WOFF 1.0高30％的增益。一个较好的做法是使用WOFF 2.0作为主要字体，WOFF 1.0和TTF格式字体作为备选。

    *怎么做：*
    > 在购买新字体之前应先检查提供商是否提供了WOFF2格式。如果使用的是免费字体，则可以始终使用Font Squirrel生成所需格式的字体。

    * 📖 [WOFF 2.0 – 了解有关下一代Web字体格式的更多信息，并将TTF转换为WOFF2](https://gist.github.com/sergejmueller/cf6b4f2133bcb3e2f64a)
    * 🛠 [创建你自己的@ font-face Kits » Font Squirrel](https://www.fontsquirrel.com/tools/webfont-generator)
    * 📖 [Using @font-face | CSS-Tricks](https://css-tricks.com/snippets/css/using-font-face/?ref=frontendchecklist)
    * 📖 [Can I use... WOFF2](https://caniuse.com/#feat=woff2)

- [ ] **使用`preconnect`可以更快地加载字体：** ![medium]

    ```html
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    ```

    *为什么：*
    > 当你浏览网站时，设备需要获取网站所在的位置以及需要连接的服务器。浏览器必须连接DNS服务器并等待查找完成后再获取资源（字体，CSS文件...），`prefetche`和`preconnect`允许浏览器在空闲时进行上面的操作，在真实请求时就不需要再花时间去做一系列动作。

    *怎么做：*
    > 在预取您的网络字体之前，请使用网页测试来检测网站.
    > 查找蓝绿色DNS查找并记下正在请求的主机（Look for teal colored DNS lookups and note the host that are being requested.）
    > 在<head>中添加预取的webfonts，添加上一步查找到的主机名。

    * 📖 [Faster Google Fonts with Preconnect - CDN Planet](https://www.cdnplanet.com/blog/faster-google-webfonts-preconnect/)
    * 📖 [Make Your Site Faster with Preconnect Hints | Viget](https://www.viget.com/articles/make-your-site-faster-with-preconnect-hints/)
    * 📖 [Ultimate Guide to Browser Hints: Preload, Prefetch, and Preconnect - MachMetrics Speed Blog](https://www.machmetrics.com/speed-blog/guide-to-browser-hints-preload-preconnect-prefetch/)
    * 📖 [A Comprehensive Guide to Font Loading Strategies—zachleat.com](https://www.zachleat.com/web/comprehensive-webfonts/#font-face)

- [ ] **Webfont大小：** ![medium] Webfont尺寸不超过300kb（包括所有变体）

 * 📖 [Font Bytes - Page Weight](https://httparchive.org/reports/page-weight#bytesFont)

**[⬆ 返回顶部](#table-of-contents)**

## 图片

![images]

 * 📖 [Image Bytes in 2018](https://httparchive.org/reports/page-weight#bytesImg)

* [ ] **图像优化:** ![high] 在保证压缩后的图片符合产品要求的情况下将图像进行优化。

    *为什么：*
    > 优化的图像在浏览器中加载速度更快，消耗的数据更少。

    *怎么做：*
    > 尽可能尝试使用CSS3效果（而不是用小图像替代）
    > 尽可能使用字体图片
    > 使用 SVG
    > 使用编译工具并指定85以下的级别压缩。

    * 📖 [Image Optimization | Web Fundamentals | Google Developers](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization)
    * 🛠 [TinyJPG – Compress JPEG images intelligently](https://tinyjpg.com/)
    * 🛠 [Kraken.io - Online Image Optimizer](https://kraken.io/web-interface)
    * 🛠 [Compressor.io - optimize and compress JPEG photos and PNG images](https://compressor.io/compress)
    * 🛠 [Cloudinary - Image Analysis Tool](https://webspeedtest.cloudinary.com/)


* [ ] **图像格式：** ![high] 适当选择图像格式。

    *为什么：*
    > 确保图片不会减慢网站速度
        
    *怎么做：*
    > 使用[Lighthouse](https://developers.google.com/web/tools/lighthouse/)识别哪些图像可以使用下一代图片格式（如JPEG 2000m JPEG XR或WebP）。
    > 比较不同的格式，有时使用PNG8比PNG16好，有时候不是。

    * 📖 [Serve Images in Next-Gen Formats  |  Tools for Web Developers  |  Google Developers](https://developers.google.com/web/tools/lighthouse/audits/webp)
    * 📖 [What Is the Right Image Format for Your Website? — SitePoint](https://www.sitepoint.com/what-is-the-right-image-format-for-your-website/)
     * 📖 [PNG8 - The Clear Winner — SitePoint](https://www.sitepoint.com/png8-the-clear-winner/)
     * 📖 [8-bit vs 16-bit - What Color Depth You Should Use And Why It Matters - DIY Photography](https://www.diyphotography.net/8-bit-vs-16-bit-color-depth-use-matters/)

- [ ] **使用矢量图像 VS 栅格/位图：** ![medium] 可以的话，推荐使用矢量图像而不是位图图像。

    *为什么：*
    > 矢量图像（SVG）往往比图像小，具有响应性和完美缩放功能。而且这些图像可以通过CSS进行动画和修改操作。

* [ ] **图像尺寸：** ![medium] 如果已知最终渲染图像大小，请在<img>上设置宽度和高度属性。

    *为什么：*
    > 如果设置了高度和宽度，则在加载页面时会保留图像所需的空间。如果没有这些属性，浏览器就不知道图像的大小，也无法为其保留适当的空间，导致页面布局在加载期间发生变化。

* [ ] **避免使用Base64图像：** ![medium] 你可以将微小图像转换为base64，但实际上并不是最佳实践。

    * 📖 [Base64 Encoding & Performance, Part 1 and 2 by Harry Roberts](https://csswizardry.com/2017/02/base64-encoding-and-performance/)
    * 📖 [A closer look at Base64 image performance – The Page Not Found Blog](http://www.andygup.net/a-closer-look-at-base64-image-performance/)
    * 📖 [When to base64 encode images (and when not to) | David Calhoun](https://www.davidbcalhoun.com/2011/when-to-base64-encode-images-and-when-not-to/)
   * 📖 [Base64 encoding images for faster pages | Performance and seo factors](https://varvy.com/pagespeed/base64-images.html)

* [ ] **懒加载：** ![medium] 图像懒加载（始终提供noscript作为后备方案）。

    *为什么：*
    > 它能改善当前页面的响应时间，避免加载一些用户可能不需要或不必要的图像。

    *怎么做：*
    > 使用[Lighthouse](https://developers.google.com/web/tools/lighthouse/)可以识别屏幕外的图像数量。
    > 使用懒加载图像的JavaScript插件。

    * 🛠 [verlok/lazyload: Github](https://github.com/verlok/lazyload)
    * 📖 [Lazy Loading Images and Video  |  Web Fundamentals  |  Google Developers](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)
    * 📖 [5 Brilliant Ways to Lazy Load Images For Faster Page Loads - Dynamic Drive Blog](http://blog.dynamicdrive.com/5-brilliant-ways-to-lazy-load-images-for-faster-page-loads/)

* [ ] **响应式图像：** ![medium] 确保提供接近设备显示尺寸的图像。

    *为什么：*
    > 小型设备不需要比视口大的图像。建议在不同尺寸上使用一个图像的多个版本。

    *怎么做：*
    > 为不同的设备设置不同大小的图像。
    > 使用srcset和picture为每个图像提供多种变体（variants）。

     * 📖 [Responsive images - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)

**[⬆ 返回顶部](#table-of-contents)**

## JavaScript

![javascript]

- [ ] **JS 压缩:** ![high] 所有JavaScript文件都要被压缩，生产环境中删除注释、空格和空行（在HTTP/2仍然有效果）。

    *为什么：*
    > 删除所有不必要的空格、注释和空行将减少JavaScript文件的大小，并加快网站的页面加载时间，提升用户体验。

    *怎么做：*
    > 建议使用下面的工具在构建或部署之前自动缩小文件。

    * 📖 [uglify-js - npm](https://www.npmjs.com/package/uglify-js)
    * 📖 [Short read: How is HTTP/2 different? Should we still minify and concatenate?](https://scaleyourcode.com/blog/article/28)

* [ ] **不内嵌JavaScript:** ![medium] *(仅对网站有效)* 避免在`body`中间嵌入多个JavaScript代码，将JavaScript代码重新集中到外部文件中，放在<head>或页面末尾（</body>之前）。

    *为什么：*
    > 将JavaScript嵌入代码直接放在`<body>`中可能会降低页面速度，因为它在构建DOM时会加载。最好的选择是使用`async` 或 `defer`的外部文件来避免阻塞DOM渲染。另一种选择是在<head>中放置一些脚本。大多数时候是需要在DOM进入主处理之前加载的分析代码或小脚本。

    *怎么做：*
    > 确保使用async或defer加载所有script文件，并准确地在<head>中加载代码。
    
     * 📖 [优化JavaScript并提高网站加载速度的11个技巧](https://www.upwork.com/hiring/development/11-tips-to-optimize-javascript-and-improve-website-loading-speeds/)

* [ ] **非阻塞JavaScript：** ![high] 使用defer属性或使用async来异步加载JavaScript文件。

    ```html
    <!-- Defer Attribute -->
    <script defer src="foo.js">

    <!-- Async Attribute -->
    <script async src="foo.js">
    ```

    *为什么：*
    > JavaScript阻止HTML文档的正常解析，因此当解析器到达`<script>`标记时（特别是在`<head>`内），它会停止解析并且执行脚本。如果您的脚本位于页面顶部，则强烈建议添加`async`和`defer`，但如果在`</body>`标记之前加载，没有太大影响。但是，使用这些属性来避免性能问题是一种很好的做法。

    *怎么做：*
    > 添加`async`（如果脚本不依赖于其他脚本）或`defer`（如果脚本依赖或依赖于异步脚本）作为script脚本标记的属性。
    > 如果有小脚本，可以在异步脚本上方使用内联脚本。

    * 📖 [Remove Render-Blocking JavaScript](https://developers.google.com/speed/docs/insights/BlockingJS)

* [ ] **优化和更新的JS库：** ![medium] 项目中使用的所有JavaScript库都是有用到的 (推荐使用原生JS的简单功能)并更新到最新版本

    *为什么：*
    > 大多数情况下，新版本都带有优化和安全性修复，所以应该使用最优化的代码来优化项目。确保不存在过时插件。

    *怎么做：*
    > 如果项目使用NPM管理依赖包，[npm-check](https://www.npmjs.com/package/npm-check)是一个非常有用的库来升级/更新你的库。

    * 📖 [You may not need jQuery](http://youmightnotneedjquery.com/)
    * 📖 [Vanilla JavaScript for building powerful web applications](https://plainjs.com/)

- [ ] **检查依赖项大小限制：** ![low] 确保使用最优的外部库，大多数情况下，可以使用更轻的库来实现相同的功能。

    *为什么：*
    > 你可能想使用npm中745 000个包中的一个，但你需要选择最适合项目需求的包。例如，MomentJS是一个很棒的库，但是你可能永远不会使用其中的很多方法，这就是为什么创建Day.js的原因。瞬间大小从16.4kB到2kB。


    *怎么做：*
    > 始终比较并选择最适合您需求的轻型库。您还可以使用[npm trends](http://www.npmtrends.com/)等工具来比较NPM包下载次数或[Bundlephobia](https://bundlephobia.com/)以了解依赖项的大小。
    
    * 🛠 [ai/size-limit: Prevent JS libraries bloat. If you accidentally add a massive dependency, Size Limit will throw an error.](https://github.com/ai/size-limit)
    * 📖 [webpack-bundle-analyzer - npm](https://www.npmjs.com/package/webpack-bundle-analyzer)
    * 📖 [Size Limit: Make the Web lighter — Martian Chronicles, Evil Martians’ team blog](https://evilmartians.com/chronicles/size-limit-make-the-web-lighter)

- [ ] **JavaScript 分析:** ![medium] 检查JavaScript文件（以及CSS）中的性能问题。

    *为什么：*
    > JavaScript复杂性可能会降低运行时性能。识别这些可能的问题对提供流畅的用户体验来说至关重要。

    *怎么做：*
    > 使用Chrome开发者工具中的时间轴工具来评估脚本事件，并找到可能需要花费太多时间的事件。

     * 📖 [Speed Up JavaScript Execution  |  Tools for Web Developers  |  Google Developers](https://developers.google.com/web/tools/chrome-devtools/rendering-tools/js-execution)
    * 📖 [JavaScript Profiling With The Chrome Developer Tools — Smashing Magazine](https://www.smashingmagazine.com/2012/06/javascript-profiling-chrome-developer-tools/)
    * 📖 [How to Record Heap Snapshots  |  Tools for Web Developers  |  Google Developers](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots)
    * 📖 [Chapter 22 - Profiling the Frontend - Blackfire](https://blackfire.io/docs/book/22-frontend-profiling)

**[⬆ 返回顶部](#table-of-contents)**

## Server

![server-side]

- [ ] **页面大小 < 1500 KB:** ![high] (理想情况 < 500 KB) 尽可能减少页面和资源的大小。

    *为什么：*
    > 理想情况下，应该尝试让页面大小<500 KB，但Web页面大小中位数大约为1500 KB（即使在移动设备上）。根据你的目标用户、连接速度、设备，尽可能减少页面大小以尽可能获得最佳用户体验非常重要。

    *怎么做：*
    > 前端性能清单中的所有规则将帮助你尽可能地减少资源和代码。

    * 📖 [Page Weight](https://httparchive.org/reports/page-weight#bytesTotal)
    * 🛠 [What Does My Site Cost?](https://whatdoesmysitecost.com/)

- [ ] **页面加载时间 < 3秒：** ![high] 尽可能减少页面加载时间，以便快速将内容传递给用户。

    *为什么：*
    > 网站或应用程序速度越快，反弹增加的可能性越小，换句话说，失去用户或未来客户的机会就越少。Google对该主题的充分研究证明了这一点。
    
    *怎么做：*
    >  使用[Page Speed Insight](https://developers.google.com/speed/pagespeed/insights/)或[WebPageTest](https://www.webpagetest.org/)等在线工具分析可能会降低速度的工具，并使用前端性能清单来缩短加载时间。

    * 🛠 [Compare your mobile site speed](https://www.thinkwithgoogle.com/feature/mobile/)
    * 🛠 [Test Your Mobile Website Speed and Performance - Think With Google](https://testmysite.thinkwithgoogle.com/?_ga=1.155316027.1489996091.1482187369)
    * 📖 [Average Page Load Times for 2018 - How does yours compare? - MachMetrics Speed Blog](https://www.machmetrics.com/speed-blog/average-page-load-times-websites-2018/)

- [ ] **TTFB < 1.3 seconds:** ![high] 尽可能减少浏览器在接收数据之前等待的时间。

    * 📖 [什么是DevTools中的TTFB，以及如何处理它](https://scaleyourcode.com/blog/article/27)
    * 📖 [Monitoring your servers with free tools is easy](https://scaleyourcode.com/blog/article/7)

* [ ] **Cookie 大小:** ![medium] 如果您使用cookie，请确保每个cookie不超过4096字节，并且一个域名下不超过20个cookie。

    *为什么：*
    > cookie存在于HTTP头中，在Web服务器和浏览器之间交换。保持cookie的大小尽可能低是非常重要的，以尽量减少对用户响应时间的影响。

    *怎么做：*
    > 消除不必要的cookie
    
    * 📖 [Cookie specification: RFC 6265](https://tools.ietf.org/html/rfc6265)
    * 📖 [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
    * 🛠 [Browser Cookie Limits](http://browsercookielimits.squawky.net/)
    * 📖 [Website Performance: Cookies Don't Taste So Good - Monitis Blog](http://www.monitis.com/blog/website-performance-cookies-dont-taste-so-good/)
    * 📖 [Google's Web Performance Best Practices #3: Minimize Request Overhead - GlobalDots Blog](https://www.globaldots.com/googles-web-performance-best-practices-3-minimize-request-overhead/)

- [ ] **最小化HTTP请求：** ![high] 始终确保所请求的每个文件对网站或应用程序至关重要，尽可能减少http请求。

- [ ] **使用CDN提供静态文件：** ![medium] 使用CDN可以更快地在全球范围内获取到你的静态文件。

 * 📖 [10 Tips to Optimize CDN Performance - CDN Planet](https://www.cdnplanet.com/blog/10-tips-optimize-cdn-performance/)
 * 📖 [HTTP Caching  |  Web Fundamentals  |  Google Developers](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching)

- [ ] **提供来自相同协议的文件：** ![high] 避免网站使用HTTPS同时使用HTTP来提供相同源地址的文件。

- [ ] **提供可访问的文件：** ![high] 避免请求无法访问的文件（404）。

- [ ] **正确设置HTTP缓存标头：** ![high] 合理设置HTTP缓存标头来减少http请求次数。

- [ ] **启用GZIP压缩** ![high]

 * 📖 [Check GZIP compression](https://checkgzipcompression.com/)

**[⬆ 返回顶部](#table-of-contents)**

---
## 性能与前端框架

### Vue

### React

 * 📖 [Optimizing Performance - React](https://reactjs.org/docs/optimizing-performance.html)
 * 📖 [React image manipulation | Cloudinary](https://cloudinary.com/documentation/react_image_manipulation)
 * 📖 [Debugging React performance with React 16 and Chrome Devtools.](https://building.calibreapp.com/debugging-react-performance-with-react-16-and-chrome-devtools-c90698a522ad)

---

## Translations

The Front-End Performance Checklist wants to also be available in other languages! Don't hesitate to submit your contribution!

## Contributing

**Open an issue or a pull request to suggest changes or additions.**

## Support
如果有什么问题和疑问，请通过以下途径联系:

* [Chat on Gitter](https://gitter.im/Front-End-Checklist/Lobby?utm_source=share-link&utm_medium=link&utm_campaign=share-link)
* [Facebook](https://www.facebook.com/frontendchecklist/)
* [Twitter](https://twitter.com/thedaviddias)

## Author

**Build with ❤️ by [David Dias](https://github.com/thedaviddias) at [@influitive](https://influitive.com/) 🇨🇦**

## Contributors

感谢各位参与本项目的人员所作出的贡献。 [[Contribute]](.github/CONTRIBUTING.md).

## License

[MIT](LICENCE.md)

All icons are provided by [Icons8](https://icons8.com/)

**[⬆ 返回顶部](#table-of-contents)**

[logo]: images/logo-front-end-performance-checklist.jpg
[html]: images/html.png
[css]: images/css.png
[fonts]: images/fonts.png
[images]: images/images.png
[javascript]: images/javascript.png
[server-side]: images/server-side.png

[low]: https://front-end-checklist.now.sh/low.svg
[medium]: https://front-end-checklist.now.sh/medium.svg
[high]: https://front-end-checklist.now.sh/high.svg


