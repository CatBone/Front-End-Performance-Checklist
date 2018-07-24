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
 * 📖 [Pagespeed - The tool and optimization guide](https://varvy.com/pagespeed/)
 * 📖 [Make the Web Faster | Google Developers](https://developers.google.com/speed/)
 * 📖 [Sitespeed.io - Welcome to the wonderful world of Web Performance](https://www.sitespeed.io/)

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
    > 删除所有不必要的空格、注释和中断行将减少HTML的大小，加快网站的页面加载时间，并显着减轻用户的下载时间。

    *怎么做：*
    > 大多数框架都有插件来促进网页的缩小。你可以使用一组可以自动完成工作的NPM模块。

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
    > ⁃ 确保所有<link>和<script>标记都没有任何type属性。

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
    > 在引用JavaScript之前引用CSS可以实现更好的并行下载，从而加快浏览器的渲染速度。

    *怎么做：*
    > 确保<head>中的<link>和<style>始终位于<script>之前。

    * 📖 [合理安排styles和scripts来提高网页速度](https://varvy.com/pagespeed/style-script-order.html)

- [ ] **最小化iframe的数量：** ![high] 仅在没有任何其他技术可能性时才使用iframe。尽量避免使用iframe。

**[⬆ 返回顶部](#table-of-contents)**

## CSS

![css]

- [ ] **压缩:** ![high] 所有CSS文件都需要被压缩，从生产文件中删除注释，空格和空行。

    *为什么：*
    > 缩小CSS文件时，内容加载速度更快，并且将更少的数据发送到客户端，所以在生产中缩小CSS文件是非常重要，这对用户是有益的就像任何企业想要降低带宽成本和降低资源。

    *怎么做：*
    > 使用工具在构建或部署之前自动压缩文件。

    * 🛠 [cssnano: 基于PostCSS生态系统的模块化压缩工具。](https://cssnano.co/)
    * 🛠 [@neutrinojs/style-minify - npm](https://www.npmjs.com/package/@neutrinojs/style-minify)

- [ ] **Concatenation:** ![medium] CCSS文件合并（对于HTTP/2效果不是很大）。

    ```html

    <!-- 不推荐 -->
    <script src="foo.css"></script>
    <script src="ajax.css"></script>

    <!-- 推荐 -->
    <script src="combined.css"></script>
    ```

    *为什么：*
    > 如果你还在使用HTTP/1就可能需要合并文件，如果服务器使用是HTTP/2效果还有待检测。

    *怎么做：*
    > 在构建或部署之前使用在线工具或者其他插件来合并文件。当然要在确保合并文件不会破坏项目正常运行。

    * 📖 [HTTP: 优化应用程序交付 - 高性能浏览器网络 (O'Reilly)](https://hpbn.co/optimizing-application-delivery/#optimizing-for-http2)
    * 📖 [HTTP/2时代的性能最佳实践](https://deliciousbrains.com/performance-best-practices-http2/)

- [ ] **非阻塞：** ![high] CSS文件需要是非阻塞引入，以防止DOM花时间加载。

    ```html
    <link rel="preload" href="global.min.css" as="style" onload="this.rel='stylesheet'">
    <noscript><link rel="stylesheet" href="global.min.css"></noscript>
    ```

    *为什么：*
    > CSS文件可以阻止页面加载并延迟页面呈现。使用`preload`实际上可以在浏览器开始显示页面内容之前加载CSS文件。

    *怎么做：*
    > 需要添加`rel`属性并赋值`preload`，并在`<link>`元素上添加`as =“style”`。

    * 📖 [loadCSS by filament group](https://github.com/filamentgroup/loadCSS)
    * 📖 [使用loadCSS预加载CSS的示例](https://gist.github.com/thedaviddias/c24763b82b9991e53928e66a0bafc9bf)
    * 📖 [使用rel =“preload”预加载内容](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
    * 📖 [Preload: What Is It Good For? — Smashing Magazine](https://www.smashingmagazine.com/2016/02/preload-what-is-it-good-for/)

- [ ] **CSS类(class)的长度:** ![low] class的长度会对HTML和CSS文件产生（轻微）影响。

    *为即使是性能影响也是有争议的，对项目的命名策略做出决定会对样式表的可维护性产生重大影响。如果使用BEM，在某些情况下可能会遇到比所需字符多的类。明智地选择名字和命名空间总是很重要的。

    *怎么做：*
    > 组件化有助于减少类的数量（和声明）以及类的长度。

    * 🛠 [long vs short class · jsPerf](https://jsperf.com/long-vs-short-class)

- [ ] **不用的CSS:** ![medium] 删除未使用的CSS选择器。

    *为什么：*
    > 删除未使用的CSS选择器可以减小文件的大小，加快资源的加载速度。

    *怎么做：*
    > ⁃ ⚠️ Always check if the framework CSS you want to use don't already has a reset / normalize code included. Sometimes you may not need everything that is inside your reset / normalize file.

    * 🛠 [UnCSS Online](https://uncss-online.com/)
    * 🛠 [PurifyCSS](https://github.com/purifycss/purifycss)
    * 🛠 [PurgeCSS](https://github.com/FullHuman/purgecss)
    * 🛠 [Chrome DevTools Coverage](https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage)

* [ ] **CSS Critical:** ![high] The CSS critical (or "above the fold") collects all the CSS used to render the visible portion of the page. It is embedded before your principal CSS call and between `<style></style>` in a single line (minified if possible).

    *为什么：*
    > Inlining critical CSS help to speed up the rendering of the web pages reducing the number of requests to the server.

    *怎么做：*
    > ⁃ Generate the CSS critical with online tools or using a plugin like the one that Addy Osmani developed.

    * 📖 [Understanding Critical CSS](https://www.smashingmagazine.com/2015/08/understanding-critical-css/)
    * 🛠 [Critical by Addy Osmani on GitHub](https://github.com/addyosmani/critical) automates this.
    * 📖 [Inlining critical CSS for better web performance | Go Make Things](https://gomakethings.com/inlining-critical-css-for-better-web-performance/)
     * 📖 [Critical Path CSS Generator - Prioritize above the fold content :: SiteLocity](https://www.sitelocity.com/critical-path-css-generator)

- [ ] **Embedded or inline CSS:** ![high] Avoid using embed or inline CSS inside your `<body>` *(Not valid for HTTP/2)*

    *为什么：*
    > One of the first reason it's because it's a good practice to **separate content from design**. It also help you have a more maintainable code and keep your site accessible. But regarding performance, it's simply because it decrease the file-size of your HTML pages and the load time.

    *怎么做：*
    > ⁃ Always use external stylesheets or embed CSS in your `<head>` (and follow the others CSS performance rules)

    * 📖 [Observe CSS Best Practices: Avoid CSS Inline Styles](https://www.lifewire.com/avoid-inline-styles-for-css-3466846)

- [ ] **Analyse stylesheets complexity:** ![high] Analyzing your stylesheets can help you to flag issues, redundancies and duplicate CSS selectors.

    *为什么：*
    > Sometimes you may have redundancies or validation errors in your CSS, analysing your CSS files and removed these complexities can help you to speed up your CSS files (because your browser will read them faster)

    *怎么做：*
    > ⁃ Your CSS should be organized, using a CSS preprocessor can help you with that. Some online tools listed above can also help you analysing and correct your code.

    * 🛠 [TestMyCSS | Optimize and Check CSS Performance](http://www.testmycss.com/)
    * 📖 [CSS Stats](https://cssstats.com/)
    * 🛠 [macbre/analyze-css: CSS selectors complexity and performance analyzer](https://github.com/macbre/analyze-css)

**[⬆ 返回顶部](#table-of-contents)**

## 字体

![fonts]

* 📖 [A Book Apart, Webfont Handbook](https://abookapart.com/products/webfont-handbook)

- [ ] **Webfont formats:** ![medium] You are using WOFF2 on your web project or application.

    *为什么：*
    > According to Google, the WOFF 2.0 Web Font compression format offers 30% average gain over WOFF 1.0. It's then good to use WOFF 2.0, WOFF 1.0 as a fallback and TTF.

    *怎么做：*
    > ⁃ Check before buying your new font that the provider gives you the WOFF2 format. If you are using a free font, you can always use Font Squirrel to generate all the formats you need.

    * 📖 [WOFF 2.0 – Learn more about the next generation Web Font Format and convert TTF to WOFF2](https://gist.github.com/sergejmueller/cf6b4f2133bcb3e2f64a)
    * 🛠 [Create Your Own @font-face Kits » Font Squirrel](https://www.fontsquirrel.com/tools/webfont-generator)
    * 📖 [Using @font-face | CSS-Tricks](https://css-tricks.com/snippets/css/using-font-face/?ref=frontendchecklist)
    * 📖 [Can I use... WOFF2](https://caniuse.com/#feat=woff2)

- [ ] **Use `preconnect` to load your fonts faster:** ![medium]

    ```html
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    ```

    *为什么：*
    > When you arrived on a website, your device needs to find out where you site live and which server it needs to connect with. Your browser had to contact a DNS server and wait for the lookup complete before fetching the ressource (fonts, CSS files...). Prefetches and preconnects allow the browser

    *怎么做：*
    > ⁃ Before prefetching your webfonts, use webpagetest to evaluate your website.
    ⁃ Look for teal colored DNS lookups and note the host that are being requested.
    ⁃ Prefetch your webfonts in your `<head>` and add eventually these hostnames that you should prefetch too.

    * 📖 [Faster Google Fonts with Preconnect - CDN Planet](https://www.cdnplanet.com/blog/faster-google-webfonts-preconnect/)
    * 📖 [Make Your Site Faster with Preconnect Hints | Viget](https://www.viget.com/articles/make-your-site-faster-with-preconnect-hints/)
    * 📖 [Ultimate Guide to Browser Hints: Preload, Prefetch, and Preconnect - MachMetrics Speed Blog](https://www.machmetrics.com/speed-blog/guide-to-browser-hints-preload-preconnect-prefetch/)
    * 📖 [A Comprehensive Guide to Font Loading Strategies—zachleat.com](https://www.zachleat.com/web/comprehensive-webfonts/#font-face)

- [ ] **Webfont size:** ![medium] Webfont sizes don't exceed 300kb (all variants included)

 * 📖 [Font Bytes - Page Weight](https://httparchive.org/reports/page-weight#bytesFont)

**[⬆ 返回顶部](#table-of-contents)**

## 图片

![images]

 * 📖 [Image Bytes in 2018](https://httparchive.org/reports/page-weight#bytesImg)

* [ ] **Images optimization:** ![high] Your images are optimized, compressed without direct impact to the end user.

    *为什么：*
    > Optimized images load faster in your browser and consume less data.

    *怎么做：*
    > ⁃ Try using CSS3 effects when it's possible (instead of a small image)
    ⁃ When it's possible, use fonts instead of text encoded in your images
    ⁃ Use SVG
    ⁃ Use a tool and specify a level compression under 85.

    * 📖 [Image Optimization | Web Fundamentals | Google Developers](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization)
    * 🛠 [TinyJPG – Compress JPEG images intelligently](https://tinyjpg.com/)


* [ ] **Images format:** ![high] Choose your image format appropriately.

    *为什么：*
    > To ensure that your images don't slow your website, choose the format that will

    *怎么做：*
    > ⁃ Use [Lighthouse](https://developers.google.com/web/tools/lighthouse/) to identify which images can eventually use **next-gen formats** (like JPEG 2000m JPEG XR or WebP)
    ⁃ Compare different formats, sometimes using PNG8 is better than PNG16, sometimes it's not.

    * 📖 [Serve Images in Next-Gen Formats  |  Tools for Web Developers  |  Google Developers](https://developers.google.com/web/tools/lighthouse/audits/webp)
    * 📖 [What Is the Right Image Format for Your Website? — SitePoint](https://www.sitepoint.com/what-is-the-right-image-format-for-your-website/)
     * 📖 [PNG8 - The Clear Winner — SitePoint](https://www.sitepoint.com/png8-the-clear-winner/)
     * 📖 [8-bit vs 16-bit - What Color Depth You Should Use And Why It Matters - DIY Photography](https://www.diyphotography.net/8-bit-vs-16-bit-color-depth-use-matters/)

- [ ] **Use vector image vs raster/bitmap:** ![medium] Prefer using vector image rather than bitmap images (when possible).

    *为什么：*
    > Vector images (SVG) tend to be smaller than images and SVG's are responsive and scale perfectly. These images can be animated and modified by CSS.

* [ ] **Images dimensions:** ![medium] Set `width` and `height` attributes on `<img>` if the final rendered image size is known.

    *为什么：*
    > If height and width are set, the space required for the image is reserved when the page is loaded. However, without these attributes, the browser does not know the size of the image, and cannot reserve the appropriate space to it. The effect will be that the page layout will change during loading (while the images load).

* [ ] **Avoid using Base64 images:** ![medium] You could eventually convert tiny images to base64 but it's actually not the best practice.

    * 📖 [Base64 Encoding & Performance, Part 1 and 2 by Harry Roberts](https://csswizardry.com/2017/02/base64-encoding-and-performance/)
    * 📖 [A closer look at Base64 image performance – The Page Not Found Blog](http://www.andygup.net/a-closer-look-at-base64-image-performance/)
    * 📖 [When to base64 encode images (and when not to) | David Calhoun](https://www.davidbcalhoun.com/2011/when-to-base64-encode-images-and-when-not-to/)
   * 📖 [Base64 encoding images for faster pages | Performance and seo factors](https://varvy.com/pagespeed/base64-images.html)

* [ ] **Lazy loading:** ![medium] Images are lazyloaded (A noscript fallback is always provided).

    *为什么：*
    > It will improve the response time of the current page and then avoid loading unnecessary images that the user may not need.

    *怎么做：*
    > ⁃ Use [Lighthouse](https://developers.google.com/web/tools/lighthouse/) to identify how many **images are offscreen**.
    ⁃ Use a JavaScript plugin like to lazyload your images.

    * 🛠 [verlok/lazyload: Github](https://github.com/verlok/lazyload)
    * 📖 [Lazy Loading Images and Video  |  Web Fundamentals  |  Google Developers](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)
    * 📖 [5 Brilliant Ways to Lazy Load Images For Faster Page Loads - Dynamic Drive Blog](http://blog.dynamicdrive.com/5-brilliant-ways-to-lazy-load-images-for-faster-page-loads/)

* [ ] **Responsive images:** ![medium] Ensure to serve images that are close to your display size.

    *为什么：*
    > Small devices don't need images bigger than their viewport. It's recommended to have multiple versions of one image on different sizes.

    *怎么做：*
    > ⁃ Create different image sizes for the devices you want to target.
    ⁃ Use `srcset` and `picture` to deliver multiple variants of each image.

     * 📖 [Responsive images - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)

**[⬆ 返回顶部](#table-of-contents)**

## JavaScript

![javascript]

- [ ] **JS Minification:** ![high] All JavaScript files are minified, comments, white spaces and new lines are removed from production files *(still valid if using HTTP/2)*.

    *为什么：*
    > Removing all unnecessary spaces, comments and break will reduce the size of your JavaScript files and speed up your site's page load times and obviously lighten the download for your user.

    *怎么做：*
    > ⁃ Use the tools suggested below to minify your files automatically before or during your build or your deployment.

    * 📖 [uglify-js - npm](https://www.npmjs.com/package/uglify-js)
    * 📖 [Short read: How is HTTP/2 different? Should we still minify and concatenate?](https://scaleyourcode.com/blog/article/28)

* [ ] **No JavaScript inside:** ![medium] *(Only valid for website)* Avoid having multiple JavaScript codes embed in the middle of your body. Regroupe your JavaScript code inside external files or eventually in the `<head>` or at the end of your page (before `</body>`).

    *为什么：*
    > Placing JavaScript embedded code directly in your `<body>` can slow down your page because it loads while the DOM is being built. The best option is to use external files with `async` or `defer` to avoid blocking the DOM. Another option is to place some scripts inside your `<head>`. Most of the time analytics code or small script that need to load before the DOM gets to main processing.

    *怎么做：*
    > ⁃ Ensure that all your files are loaded using `async` or `defer` and decide wisely the code that you will need to inject in your `<head>`.

     * 📖 [11 Tips to Optimize JavaScript and Improve Website Loading Speeds](https://www.upwork.com/hiring/development/11-tips-to-optimize-javascript-and-improve-website-loading-speeds/)

* [ ] **Non-blocking JavaScript:** ![high] JavaScript files are loaded asynchronously using `async` or deferred using `defer` attribute.

    ```html
    <!-- Defer Attribute -->
    <script defer src="foo.js">

    <!-- Async Attribute -->
    <script async src="foo.js">
    ```

    *为什么：*
    > JavaScript blocks the normal parsing of the HTML document, so when the parser reaches a `<script>` tag (particularly is inside the `<head>`), it stops to fech and run it. Adding `async` or `defer` are highly recommended if your scripts are placed in the top of your page but less valuable if just before your `</body>` tag. But it's a good practice to always use these attributes to avoid any performance issue.

    *怎么做：*
    > ⁃ Add `async` (if the script don't rely on other scripts) or `defer` (if the script relies upon or relied upon by an async script) as an attribute to your script tag.
    ⁃ If your have small scripts, maybe use inline script place above async scripts.

    * 📖 [Remove Render-Blocking JavaScript](https://developers.google.com/speed/docs/insights/BlockingJS)

* [ ] **Optimized and updated JS libraries:** ![medium] All JavaScript libraries used in your project are necessary (prefer Vanilla Javascript for simple functionalities), updated to their latest version and don't overwhelm your JavaScript with unnecessary methods.

    *为什么：*
    > Most of the time, new versions come with optimization and security fix. You should use the most optimized code to speed up your project and ensure that you'll not slow down your website or app without outdated plugin.

    *怎么做：*
    > ⁃ If your project use NPM packages, [npm-check](https://www.npmjs.com/package/npm-check) is a pretty interesting library to upgrade / update your librairies.

    * 📖 [You may not need jQuery](http://youmightnotneedjquery.com/)
    * 📖 [Vanilla JavaScript for building powerful web applications](https://plainjs.com/)

- [ ] **Check dependencies size limit:** ![low] Ensure to use wisely external librairies, most of the time, you can use a lighter library for a same functionnality.

    *为什么：*
    > You may be tempted to use one of the 745 000 packages you can find on [npm](https://www.npmjs.com/), but you need to choose the best package for your needs. For example, MomentJS is an awesome library but with a lot of methods you may never use, that's why Day.js was created. It's just 2kB vs 16.4kB gz for Moment.

    *怎么做：*
    > ⁃ Always compare and choose the best and lighter library for your needs. You can also use tools like [npm trends](http://www.npmtrends.com/) to compare NPM package downloads counts or [Bundlephobia](https://bundlephobia.com/) to know the size of your dependencies.

    * 🛠 [ai/size-limit: Prevent JS libraries bloat. If you accidentally add a massive dependency, Size Limit will throw an error.](https://github.com/ai/size-limit)
    * 📖 [webpack-bundle-analyzer - npm](https://www.npmjs.com/package/webpack-bundle-analyzer)
    * 📖 [Size Limit: Make the Web lighter — Martian Chronicles, Evil Martians’ team blog](https://evilmartians.com/chronicles/size-limit-make-the-web-lighter)

- [ ] **JavaScript Profiling:** ![medium] Check for performance problems in your JavaScript files (and CSS too).

    *为什么：*
    > JavaScript complexity can slow down runtime performance. Identifing these possible issues are essential to offer the smoothest user experience.

    *怎么做：*
    > ⁃ Use the Timeline tool in the Chrome Developer Tool to evaluate scripts events and found the one that may take too much time.

     * 📖 [Speed Up JavaScript Execution  |  Tools for Web Developers  |  Google Developers](https://developers.google.com/web/tools/chrome-devtools/rendering-tools/js-execution)
    * 📖 [JavaScript Profiling With The Chrome Developer Tools — Smashing Magazine](https://www.smashingmagazine.com/2012/06/javascript-profiling-chrome-developer-tools/)
    * 📖 [How to Record Heap Snapshots  |  Tools for Web Developers  |  Google Developers](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots)
    * 📖 [Chapter 22 - Profiling the Frontend - Blackfire](https://blackfire.io/docs/book/22-frontend-profiling)

**[⬆ 返回顶部](#table-of-contents)**

## Server

![server-side]

- [ ] **Webpage size < 1500 KB:** ![high] (but ideally < 500 KB) Reduce the size of your page + resources as much as you can.

    *为什么：*
    > Ideally you should try to target < 500 KB but the state of web shows that the median of Kilobytes is around 1500 KB (even on mobile). Depending your target users, connexion, devices, it's important to reduce as much as possible your total Kilobytes to have the best user experience possible.

    *怎么做：*
    > ⁃ All the rules inside the Front-End Performance Checklist will help you to reduce as much as possible your resources and your code.

    * 📖 [Page Weight](https://httparchive.org/reports/page-weight#bytesTotal)
    * 🛠 [What Does My Site Cost?](https://whatdoesmysitecost.com/)

- [ ] **Page load times < 3 seconds:** ![high] Reduce as much as possible your page load times to quickly deliver your content to your users.

    *为什么：*
    > Faster your website or app is, less you have probability of bounce increases, in other terms you have less chances to lose your user or future client. Enough researches on the subject prove that point.
    
    *怎么做：*
    >  ⁃ Use online tools like [Page Speed Insight](https://developers.google.com/speed/pagespeed/insights/) or [WebPageTest](https://www.webpagetest.org/) to analyze what could be slowing you down and use the Front-End Performance Checklist to improve your load times.

    * 🛠 [Compare your mobile site speed](https://www.thinkwithgoogle.com/feature/mobile/)
    * 🛠 [Test Your Mobile Website Speed and Performance - Think With Google](https://testmysite.thinkwithgoogle.com/?_ga=1.155316027.1489996091.1482187369)
    * 📖 [Average Page Load Times for 2018 - How does yours compare? - MachMetrics Speed Blog](https://www.machmetrics.com/speed-blog/average-page-load-times-websites-2018/)

- [ ] **Time To First Byte < 1.3 seconds:** ![high] Reduce as much as you can the time your browser waits before receiving data.

    * 📖 [What is Waiting (TTFB) in DevTools, and what to do about it](https://scaleyourcode.com/blog/article/27)
    * 📖 [Monitoring your servers with free tools is easy](https://scaleyourcode.com/blog/article/7)

* [ ] **Cookie size:** ![medium] If you are using cookies be sure each cookie doesn't exceed 4096 bytes and your domain name doesn't have more than 20 cookies.

    *为什么：*
    > cookies is exchanged in the HTTP headers between web servers and browsers. It's important to keep the size of cookies as low as possible to minimize the impact on the user's response time.

    *怎么做：*
    > ⁃ Eliminate unnecessary cookies

    * 📖 [Cookie specification: RFC 6265](https://tools.ietf.org/html/rfc6265)
    * 📖 [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
    * 🛠 [Browser Cookie Limits](http://browsercookielimits.squawky.net/)
    * 📖 [Website Performance: Cookies Don't Taste So Good - Monitis Blog](http://www.monitis.com/blog/website-performance-cookies-dont-taste-so-good/)
    * 📖 [Google's Web Performance Best Practices #3: Minimize Request Overhead - GlobalDots Blog](https://www.globaldots.com/googles-web-performance-best-practices-3-minimize-request-overhead/)

- [ ] **Minimizing HTTP requests:** ![high] Always ensure that every file requested are essential for you website or application.

- [ ] **Use a CDN to deliver your assets:** ![medium] Use a CDN to deliver faster your content over the world.

 * 📖 [10 Tips to Optimize CDN Performance - CDN Planet](https://www.cdnplanet.com/blog/10-tips-optimize-cdn-performance/)
 * 📖 [HTTP Caching  |  Web Fundamentals  |  Google Developers](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching)

- [ ] **Serve files from the same protocol:** ![high] Avoid having your website using HTTPS and serve files coming from source using HTTP.

- [ ] **Serve reachable files:** ![high] Avoid requesting unreachable files (404).

- [ ] **Set HTTP cache headers properly:** ![high] Set HTTP headers to avoid expensive number of roundtrips between your browser and the server.

- [ ] **GZIP compression is enable:** ![high]

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
