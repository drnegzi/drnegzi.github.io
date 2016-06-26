---
layout: post
title: ساخت یک سایت با استفاده از GitHub Pages و Jekyll
category: [Jekyll, GitHub Pages, GitHub, آموزشی]
tags: [آموزشی]
date: 2016-03-09 04:30:00 +0330
published: true
comments: true
series:
summary: این پست با هدف آموزش کوتاه و مختصر چگونگی ساخت یک سایت شخصی با استفاده از GitHub Pages و Jekyll نوشته شده است. قصد داریم این بیت با GitHub Pages و نحوه استفاده از Jekyll بر روی آن آشنا بشیم و سایت خودمون رو با استفاده از این دو ابزار از صفر آماده کنیم.
description: مطلب آموزشی برای آشنایی با GitHub Pages و Jekyll و نحوه کارکرد این دو ابزار به همراه آموزش ساخت یک سایت شخصی با استفاده از آنها.
uuid: 552f84a1-ed51-4af3-b3f3-64ee5fc84256
excerpt_separator: <!--more--> 
---
این پست با هدف آموزش کوتاه و مختصر چگونگی ساخت یک سایت شخصی با استفاده از [GitHub Pages](https://pages.github.com) و [Jekyll](http://jekyll.com) نوشته شده است.

برای شروع این مطلب من فرض رو بر این گذاشتم که خواننده علاوه بر آشنایی با version control و نحوه کارکرد Git و GitHub، بلکه آشنایی مقدماتی با HTML و CSS هم دارد. ضمن اینکه در این مطلب در بخش‌هایی از [Markdwon](https://daringfireball.net/projects/markdown/) هم استفاده خواهم کرد.

در ضمن از اونجایی که قصد دارم این پست ساده و کوتاه باشه، سعی کردم تا تمامی مراحل رو از طریق رابط کاربری وب GitHub انجام بدم و سراغ CLI نخواهم رفت.
اما به طور حتم، در آینده در یک سری پست، درباره نحوه کار با Jekyll و حتی GitHub از طریق CLI، به همراه پیاده سازی بعضی از ویژگی‌های جالب با Jekyll خواهم نوشت.

اگر براتون جالب بود که چرا Jekyll و من چرا تصمیم به ساخت سایت شخصیم به این شکل افتادم، می‌تونید [این یادداشت](https://theskn.github.io/:posts/yes-we-jekyll.html) رو بخونید.


<div class='post-inline-title'>GitHub Pages چیست؟</div>
GitHub Pages صفحات وبی هستند که توسط GitHub میزبانی می‌شوند. همه کاربران GitHub می‌توانند به صورت رایگان یک صفحه شخصی  بسازند، ضمن اینکه GitHub Pages این قابلیت را به شما می‌دهد تا برای هر پروژه‌‌اتون روی GitHub هم یک صفحه وب بسازید. نحوه کار کردن و ساختن این صفحات مانند کارکردن با خود GitHubه، با این تفاوت که repository مربوط به صفحه‌ای که قصد ایجاد آن را دارید، باید طبق فرمت مشخصی نامگذاری شده باشه و شامل حداقل یک فایل HTML یا Markdown باشد تا بتوانید این فایل را مثل سایت‌های دیگه از طریق مرورگرهاتون ببینید.

GitHub Pages در کنار این قابلیت‌ها دارای یک [موتور تولید وب سایت static](http://www.staticgen.com/) به نام Jekyllه که به زودی با اون هم آشنا می‌شیم.


<div class="post-inline-title">شروع کار با GitHub Pages</div>
<span class="font-color-white">- </span> شما در ابتدا نیاز به یک حساب کاربری در GitHub دارید، در صورتی که قبلا در GitHub ثبت نام کردید، به حساب کاربریتون وارد بشید و در غیر این صورت یک حساب کاربری جدید برای خودتون بسازید و پس از ورود به GitHub به آدرس [https://github.com/new](https://github.com/new) برید یا دکمه مربوط به ساخت repository جدید رو بزنید.

<span class="font-color-white">- </span>نام repository جدیدتون رو <span class="highlight-text">username.github.io</span> بذارید و به خاطر داشته باشید که به جای قسمت <span class="highlight-text">username</span> باید نام کاربری خودتون در GitHub رو جایگزین کنید.
ضمنا repository جدیدتون باید public - عمومی - باشه و در صورتی که گزینه ساخت فایل <span class="highlight-text">README</span> توسط GitHub در هنگام ایجاد repository فعال باشه، مشکلی وجود ندارد.

و در انتها repository جدیدتون رو بسازید.

<span class="font-color-white">- </span>حالا باید یک فایل <span class="highlight-text">index.html</span> داخل repository بسازیم.

برای این کار رو گزینه مربوط به اضافه کردن فایل جدید بزنید و اسم فایل جدید رو <span class="highlight-text">index.html</span> قرار بدید.

<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2016-03-27/theskn-blog-post-jekyll-github-pages-001.png"/>

حالا تو ویرایگشر متنی GitHub کد زیر رو قرار بدید. فراموش نکنید که اطلاعات مربوط به خودتون رو داخل کد جایگزین کنید.
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain; html-script: true">
&lt;!DOCTYPE html>
&lt;html>
  &lt;head>
    &lt;title>Kianoosh Naghavi&lt;/title>
    <!-- link to main stylesheet -->
	<link rel="stylesheet" type="text/css" href="/css/main.css">
  &lt;/head>
  &lt;body>
    &lt;nav>
      &lt;ul>
        &lt;li>&lt;a href="/">Home&lt;/a>&lt;/li>
        &lt;li>&lt;a href="/blog">Blog&lt;/a>&lt;/li>
      &lt;/ul>
    &lt;/nav>
    &lt;div class="container">
      &lt;div class="main">
        &lt;h1>Hi!&lt;/h1>
        &lt;p>This is Kianoosh!&lt;/p>
      &lt;/div>&lt;!-- /.main -->
    &lt;/div>&lt;!-- /.container -->
    &lt;footer>
      &lt;ul>
        &lt;li>&lt;a href="mailto:example@gmail.com">email&lt;/a>&lt;/li>
        &lt;!-- /using mailto is bad, very very bad - only fools and noobs use it -->
        &lt;li>&lt;a href="https://github.com/theskn">github.com/theskn&lt;/a>&lt;/li>
      &lt;/ul>
    &lt;/footer>
  &lt;/body>
&lt;/html>
</pre>
</div>

<span class="font-color-white">- </span>حالا از پایین صفحه روی <span class="highlight-text">Commit changes</span> بزنید.
شما در این قسمت می‌توانید توضیحاتی در مورد تغییراتی که داخل فایل در حال ویرایش انجام داده‌اید بنویسید.

خب، حالا با موفقیت اولین سایت خودتون رو با GitHub Pages ساختید. برای دیدن سایتتون به آدرس <span class="highlight-text">https://username.github.io</span> مراجعه کنید. گاهی اوقات ساخته شدن و در دسترس قرار گرفتن سایت تازه ساخته شده با GitHub Pages بین ۵ تا ۱۰ دقیقه زمان می‌برد، ولی در غالب موارد، همزمان با Commit کردن فایل <span class="highlight-text">index.html</span> برای اولین بار، سایت شما آماده است.

<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2016-03-27/theskn-blog-post-jekyll-github-pages-002.png"/>

<span class="font-color-white">- </span>خب حالا بهتره که یه ذره سر و شکلی به صفحه سایتمون بدیم.

برای این کار دوباره به صفحه اول repository خودتون برگردید و یک فایل جدید به اسم <span class="highlight-text">css/main.css</span> ایجاد کنید.

من در حالت کلی، همیشه سعی می‌کنم تا در حد ممکن ساختار پوشه و فایل بندی پروژه‌هام تفکیک شده و خوانا باشه و فایل‌هایی مثل فایل‌های مربوط به style sheet رو در مسیر <span class="highlight-text ltr-direction">assets/css/filename.css</span> قرار می‌دم.

در ضمن قسمت <span class="highlight-text">/css</span> در هنگام نام گذاری فایل جدید، باعث میشه تا GitHub به صورت اتوماتیک داخل repository شما subdirectory مربوط رو بسازه.

حالا کد زیر رو داخل فایل <span class="highglight-text">main.css</span> قرار بدید:
<div class="ltr-direction font-family-consolas">
<pre class="brush: css;">
body {
    margin: 60px auto;
    width: 70%;
}
nav ul, footer ul {
    font-family:'Consolas';
    padding: 0px;
    list-style: none;
    font-weight: bold;
}
nav ul li, footer ul li {
    display: inline;
    margin-right: 20px;
}
a {
    text-decoration: none;
    color: #999;
}
a:hover {
    text-decoration: underline;
}
h1 {
    font-size: 3em;
    font-family:'Consolas';
}
p {
    font-size: 1.5em;
    line-height: 1.4em;
    color: #333;
}
footer {
    border-top: 1px solid #d5d5d5;
    font-size: .8em;
}

ul.posts { 
    margin: 20px auto 40px; 
    font-size: 1.5em;
}

ul.posts li {
    list-style: none;
}
</pre>
</div>

فراموش نکنید که تغییرات انجام شده رو Commit کنید.

ما در مرحله قبلی و هنگام نوشتن کد مربوط به فایل <span class="highlight-text">index.html</span>، این فایل رو با فایل <span class="highlight-text">main.css</span> مرتبط کردیم. برای چگونگی این اتفاق به خط ششم کد فایل <span class="highlight-text">index.html</span> مراجعه کنید.

خب، حالا دوباره به آدرس <span class="highlight-text">https://username.github.io</span> سر بزنید.

<div class="post-inline-title">Jekyll چیست؟</div>
Jekyll یک سیستم مدیریت و تولید سایت‌های ایستا<a id="footnote-ref-001" class="foot-note-reference" href="#footnote-001">[۱]</a>ی قدرتمند است.
استفاده از Jekyll و یا سایر سیستم‌های مشابه کار را برای ایجاد و مدیریت سایت‌هایی مانند دورانی که صفحات وب از به صورت ایستا ساخته می‌شدند و محتوای آنها در پایگاه داده ذخیره نمی‌شد، آسان می‌کند.

این شیوه شاید بهترین حالت ممکن برای ایجاد سایت‌های زیبا و ساده که دارای ساختار پیچیده‌ای نیستند باشد.

از آنجایی که موتور Jekyll برای استفاده به همراه GitHub Pages بر روی GitHub موجود است، باز هم با رعایت کردن ساختار مشخصی در نامگذاری‌ فایل‌ها و پوشه‌هامون، می‌تونیم شرایط استفاده از این قابلیت رو ایجاد کنیم. تحت این شرایط، هر بار که فایل جدیدی را به repository خودمون commit کنیم، Jekyll یک بار از ابتدا تمام صفحات HTML را دوباره تولید می‌کند و محتوای سایت در صورت تغییر به روز رسانی می‌شود.

به نظر من بهترین حالت برای کار کردن با Jekyll نصب اون روی کامپیوتر شخصی خودتونه، به این ترتیب که قبل از commit کردن تغییرات جدید به repository، بتونید سایت خودتون رو به صورت local روی کامپیوتر شخصی خودتون مشاهده کنید، مزیت بزرگ این کار، جلوگیری از افزایش تعداد reversionها و شلوغ، کثیف و نامرتبط شدن repository کاربران است.

اما همانطور که در ابتدا اشاره کردم، برای سرعت دادن در مرور کلیت بحث، این بار تنها از طریق رابط کاربری وب GitHub سایتمون رو راه اندازی می‌کنیم.

مزیت بزرگ Jekyll و سایر سیستم‌های مشابه برای کاری که قصد انجام آن را داریم، در این است که این سیستم‌ها می‌توانند صفحات وب ما را با استفاده از قالب‌هایی که برای اون‌ها نوشتیم تولید کنند؛ به زبان ساده‌تر یعنی برای داشتن &quot;فهرست کناری صفحات سایت&quot; لازم نیست تا کد این قسمت را در همه صفحات تکرار کنیم، ما یک بار در فایلی جداگانه که به آن قالب، Template یا Layout می‌گوییم، کد این فهرست را می‌نویسیم و از حالا به بعد هر جا که نیاز به استفاده از این فهرست داشتیم، تنها از فراخوانی این قالب استفاده می‌کنیم. تولید این قالب و بارگذاری کد نوشته شده در بین فایل‌های دیگر بر عهده موتوری مانند Jekyll است. حالا تصور کنید که &quot;فهرست صفحات سایت&quot; قرار بود تا در هر صفحه جدید در محلی متفاوت قرار بگیرد و یا تغییراتی دیگر داشته باشد، قطعا روشن است که با استفاده از یک موتور تولید سایت ایستا مانند Jekyll چقدر می‌توان در زمان صرفه جویی کرد و جلوی دوباره و چندباره کاری‌ها را گرفت.

<div class="post-inline-title">استفاده از Jekyll در GitHub</div>
همانطوری که گفتم برای فعال کردن امکان استفاده از Jekyll بر روی سایتمان باید ساختار مشخصی را در نحوه نامگذاری فایل‌ها و پوشه‌هامون رعایت کنیم. <a href="http://jekyllrb.com/docs/structure/">ساختار Jekyll</a> را مرحله به مرحله به سایتمون اضافه می‌کنیم و در مورد اون صحبت خواهیم کرد.

<span class="font-color-white">- </span>در اولین قدم در شاخه اصلی repository سایت یک فایل به اسم <span class="highlight-text">gitignore.</span> می‌سازیم و داخل این فایل به GitHub دستور می‌دهیم تا از اضافه کردن پوشه <span class="highlight-text">site_</span> به داخل repository جلوگیری کند؛ این پوشه هر بار بعد از هر commit که Jekyll اقدام به تولید مجدد سایت می‌کند، به صورت اتوماتیک توسط Jekyll در پروژه ساخته می‌شود و  به همین دلیلی نیازی نیست تا این پوشه شامل شرایط version control باشد.

این کد را از طریق ویرایگشر متنی GitHub در فایل <span class="highlight-text">gitignore.</span> وارد کنید:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain;">
_site/
</pre>
</div>

<span class="font-color-white">- </span>حالا داخل شاخه اصلی repository یک فایل جدید به نام <span class="highlight-text">config.yml_</span> ایجاد می‌کنیم که شامل اطلاعاتی است که از آنها برای کنترل و تنظیمات Jekyll استفاده می‌شود.
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain;">
# Site settings
title: "Just another test website"
name: "Kianoosh Naghavi"
author: Kianoosh Naghavi

# Build settings
markdown: kramdown
encoding: utf-8
timezone: Asia/Tehran
</pre>
</div>

در اینجا ما به Jekyll اطلاعاتی در مورد عنوان سایت، نام سایت و نویسنده سایت به همراه نسخه Markdown مورد استفاده، encoding مورد استفاده و منطقه زمانی خودمان داده‌ایم.

این مقادیر را با مقادیر دلخواه خودتان تعویض کنید.

<span class="font-color-white">- </span>حالا یک پوشه به نام <span class="highlight-text">layout_</span> بسازید و در داخل آن فایلی جدید به نام <span class="highlight-text">default.html</span> ایجاد کنید.

این فایل قالب اصلی ما خواهد بود که حاوی عناصر تکرار شونده مانند tagهای <span class="highlight-text">&lt;head></span> و <span class="highlight-text">&lt;footer></span> خواهد بود. با استفاده از این قالب دیگر لازم نیست تا در هنگام ساخت هر صفحه جدید کدهای مربوط به این قسمت‌ها را دوباره بنویسیم. ضمن اینکه خطاگیری، نگهداری و تغییر در این قسمت‌ها بسیار ساده و آسان شده و در صورت نیاز به تغییر، ما تنها یک بار فایل <span class="highlight-text">default.html</span> را ویرایش خواهیم کرد و این تغییر در تمامی صفحات سایت اعمال خواهد شد.

پس در اولین قدم کدهای مربوط به فایل <span class="highlight-text">index.html</span> را به داخل فایل <span class="highlight-text">default.html</span> منتقل می‌کنیم و در نهایت باید فایلمان به شکل زیر باشد:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain; html-script: true">
&lt;!DOCTYPE html>
&lt;html>
  &lt;head>
    &lt;title>&lbrace;&lbrace; page.title }}&lt;/title>
    <!-- link to main stylesheet -->
	<link rel="stylesheet" type="text/css" href="/css/main.css">
  &lt;/head>
  &lt;body>
    &lt;nav>
      &lt;ul>
        &lt;li>&lt;a href="/">Home&lt;/a>&lt;/li>
        &lt;li>&lt;a href="/blog">Blog&lt;/a>&lt;/li>
      &lt;/ul>
    &lt;/nav>
    &lt;div class="container">
      &lt;div class="main">
        &lt;h1>Hi!&lt;/h1>
        &lt;p>
        
      		&lbrace;&lbrace; content }}
      		
      	&lt;/p>
      &lt;/div>&lt;!-- /.main -->
    &lt;/div>&lt;!-- /.container -->
    &lt;footer>
      &lt;ul>
        &lt;li>&lt;a href="mailto:example@gmail.com">email&lt;/a>&lt;/li>
        &lt;!-- /using mailto is bad, very very bad - only fools and noobs use it -->
        &lt;li>&lt;a href="https://github.com/theskn">github.com/theskn&lt;/a>&lt;/li>
      &lt;/ul>
    &lt;/footer>
  &lt;/body>
&lt;/html>
</pre>
</div>

لازم به ذکر است که tagهای <span class="highlight-text"><code>&lbrace;&lbrace; page.title &rbrace;&rbrace;</code></span> و <span class="highlight-text"><code>&lbrace;&lbrace; content &rbrace;&rbrace;</code></span> همان tagهایی هستند که قرار است ما از طریق آنها، مطالب و محتوای مورد نظرمان را به قالبمان طزریق کنیم. Jekyll این دست از tagها را <span class="highlight-text">liquid tags</span> یا tagهای شناور می‌نامد.

<span class="font-color-white">- </span>خب حالا وقت آن رسیده تا <span class="highlight-text">index.html</span> را برای استفاده از قالبی که ساختیم آماده کنیم. برای این کار قطعه زیر را با کل محتوای فایل جایگزین کنید:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain; html-script: true">
---
layout: default
title: Kianoosh Naghavi, inject
---
<div class="main">
	<h1>This is Kianoosh Naghavi!</h1>
	<p>and this is content injection using jekyll!</p>
</div><!-- /.main -->
</pre>
</div>

در این قطعه plain text بالای صفحه در Jekyll به نام Front-matter شناخته می‌شود. هر فایلی که در سایت دارای ساختاری مشابه در ابتدای خود باشد، توسط Jekyll پردازش خواهد شد.

هر باری که ما یک فایل HTML جدید ایجاد کنیم و در آن مقدار <span class="highlight-text">layout: default</span> را برای Jekyll مشخص کرده باشیم، Jekyll قالب <span class="highlight-text">layouts/defaul.html_</span> را برداشته و با جاگذاری مقدار <span class="highlight-text"><code>&lbrace;&lbrace; content &rbrace;&rbrace;</code></span> با متن وارد شده در پایین قسمت Front-matter یک فایل HTML جدید برای ما تولید می‌کند.

حالا دوباره سایتتان را چک کنید!


<div class="post-inline-title">راه اندازی بلاگ</div>
ساختن یک بلاگ با Jekyll هم همانطور که در گذشته دیدیم کار پیچیده و سختی نیست و فقط قواعد و ساختار خاصی دارد که در صورت پیروی از اون‌ها، به راحتی می‌تونیم بلاگ خودمون رو بسازیم.

در ادامه این قسمت به سایتمون یه پست جدید و صفحاتی برای لیست کردن پست‌هامون اضافه می‌کنیم، ضمن اینکه نحوه ساختن permalinkهای سفارشی رو هم با هم بررسی می‌کنیم.

<span class="font-color-white">- </span>در اولین قدم برای پست‌هامون یک قالب جدید می‌سازیم. برای این کار فایل جدیدی با نام <span class="highlight-text">blog.html</span> در داخل پوشه <span class="highlight-text">layouts_</span> می‌سازیم.

فایل جدید ما باید حاوی قطعه زیر باشد:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain; html-script: true">
---
layout: default
---
<h1>&lbrace;&lbrace; page.title }}</h1>
<p class="meta">&lbrace;&lbrace; page.date | date_to_string }}</p>

<div class="post">
  &lbrace;&lbrace; content }}
</div>
</pre>
</div>

توجه داشته باشید که خود قالب پست‌هایمان در حال استفاده از قالب <span class="highlight-text">default</span> به عنوان قالب اصلی است و ما با استفاده از قسمت <span class="highlight-text"><code>&lbrace;&lbrace; content &rbrace;&rbrace;</code></span> آن tagهای شناور جدیدی به قالب اصلی طزریق می‌کنیم.

<span class="font-color-white">- </span>حالا تو مسیر اصلی repository یک پوشه جدید با نام <span class="highlight-text">posts_</span> می‌سازیم. این پوشه محل ذخیره سازی و نگهداری پست‌هایی است که در بلاگ منتشر شده‌اند. نکته مهم درباره این پست‌ها ساختار نامگذاری آنهاست، نام هر پست باید از قاعده <span class="highlight-text">YYYY-MM-DD-title-of-the-blog-post.md</span> پیروی کند. نام هر فایل در ادامه تبدیل به permalink مربوط به آن پست می‌شود، برای مثال فایلی با نام <span class="highlight-text">2016-03-31-frst-blog-post.md</span> ایجاد کنید:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain;">
---
layout: post
title: "Firs blog post"
date: 2016-03-31 01:50:00 +0330
---
and this is our first blog post.
typical Hello world?
0_0
</pre>
</div>

حتما دقت داشته باشید که در قسمت <span class="highlight-text">date</span> زمان را با فرمتی که در اینجا وارد کرده‌ام، وارد کنید. در نسخه‌های قدیمی‌تر موتور Jekyll تنها وارد کردن سال، ماه و روز کافی بود، اما در حال حاضر باید این اطلاعات به صورت کامل و به همراه، ساعت، دقیقه، ثانیه و منطقه زمانی با ساختار UTC offset وارد شود، یعنی به شکل <span class="highlight-text">YYYY-MM-DD HH:MM:SS +/-TTTT</span>.

پسوند <span class="highlight-text">md.</span> پسوند مربوط به فایل‌های Markdown است، syntax به کار گرفته شده در این فایل‌ها توسط Jekyll تبدیل به HTML می‌شود. Markdown یک زبان &quot;نشانه گذاری&quot; است و ساختار آن شبیه plain text است. هدف از استفاده از Markdown سهولت بخشیدن به امر نوشتن است به طوری که بتوانیم به سرعت محتوای HTML خود را تولید کنیم. در صورت تمایل میتوانید [Markdown cheatsheet](http://packetlife.net/media/library/16/Markdown.pdf) را نگاهی بیاندازید.

<span class="font-color-white">- </span>حالا قصد داریم تا صفحه‌ای جهت لیست کردن و نمایش تمامی پست‌های سایتمون درست کنیم. برای این کار یک پوشه جدید با نام <span class="highlight-text">blog</span> می‌سازیم و در داخل آن فایل جدیدی با نام <span class="highlight-text">index.html</span> ایجاد می‌کنیم. ما از این شیوه تنها به دلیل جدا بودن صفحات سایتمان و ذخیره کردن هر کدام از آنها در پوشه مخصوص به خود استفاده می‌کنیم در غیر این صورت و در صورت تمایل می‌توانیم فایل <span class="highlight-text">blog.html</span> را در مسیر اصلی repository هم ایجاد کنیم. شایان ذکر است که این دو رویکرد تفاوت کوچکی در نحوه ایجاد URL برای دسترسی به صفحه مورد نظر دارند. برای مثال در رویکرد اول آدرس صفحه مورد نظر ما، در اینجا <span class="highlight-text">blog</span> به شکل <span class="highlight-text">http://example.com/blog</span> است و در رویکرد دوم برای دسترسی به صفحه مورد نظر، باید آدرس <span class="highlight-text">http://example.com/blog.html</span> را وارد کنیم.

ما فرض را بر انجام همان رویکرد نخست می‌گیریم، پس فایل <span class="highlight-text">index.html</span> ایجاد شده باید دارای محتوای زیر باشد:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain; html-script: true">
---
layout: default
title: Blog archive
---
	<h1>&lbrace;&lbrace; page.title }}</h1>
	<ul class="posts">

	  &lbrace;% for post in site.posts %}
	    <li><span>&lbrace;&lbrace; post.date | date_to_string }}</span> » 
	    <a href="&lbrace;&lbrace; post.url }}" 
	    title="&lbrace;&lbrace; post.title }}">{{ post.title }}</a></li>
	  &lbrace;% endfor %}
	</ul>
</pre>
</div>

ما برای ساخت یک لیست غیر مرتب از تمام پست‌های منتشر شده در سایتمان از حلقه <span class="highlight-text">foreach</span> بر روی <span class="highlight-text">site.posts</span> استفاده می‌کنیم، یعنی برای تمام فایل‌های موجود در پوشه <span class="highlight-text">post</span>. در ادامه واضح است که برای هر پست موجود در این پوشه، مقادیر زمان، یعنی <span class="highlight-text">post.date</span> و عنوان، یعنی <span class="highlight-text">post.title</span> را در داخل یک لیست نامرتب فهرست می‌کنیم.

خب حالا بهتره تا نگاهی به https://username.github.io/blog بیاندازید.

<div class="post-inline-title">سفارشی سازی بلاگ</div>
یکی از قابلیت‌های خوب Jekyll، امکان مدیریت ساختار permalinks هاست، برای این کار به سراغ ویرایش فایل <span class="highlight-text">config.yml_</span> می‌رویم.

این خط را به فایل <span class="highlight-text">config.yml_</span> اضافه کنید:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain;">
#outputting
permalink: :posts/:title.html
</pre>
</div>

این تغییر باعث می‌شود تا از این به بعد بتوانید پست‌های خودتون رو در آدرسی مانند http://username.github.io/:posts/name-of-your-post.html ببینید.

استفاده از ساختار زیر هم بسیار پرکاربرد است:
<div class="ltr-direction font-family-consolas">
<pre class="brush: plain;">
#outputting
permalink: /blog/:year/:month/:day/:title
</pre>
</div>

این ساختار باعث می‌شود تا پست‌هایتان را بتوانید در آدرسی مانند http://username.github.io/blog/YYYY/MM/DD/name-of-your-post.html مشاهده کنید.

<div class="post-inline-title">جمع بندی</div>
خب تا اینجا فکر کنم به مقدار خوبی با نحوه ایجاد یک سایت با استفاده از GitHub Pages و Jekyll آشنا شدیم، به عنوان تمرین بد نیست که خودتون تلاش کنید تا صفحات جدیدی مثل about یا cv برای سایتتون بسازید.

من در آینده سعی خواهم کردم تا یک سری مطالب درباره نحوه نصب GitHub و Jekyll بر روی رایانه‌های شخصی بنویسم و طرز استفاده از این دو برنامه از طریق CLI رو هم در اون‌ها بررسی کنیم و تعدادی از ویژگی‌های جالبی که با Jekyll می‌تونیم پیاده سازی کنیم رو با هم ببینیم.

منتظر نظرات و سوالاتتون هستم.

<div class="foot-note-header">پا نویس:</div>
<span id="footnote-001" class="foot-note"><a href="#footnote-ref-001">[۱]:</a> Static site generator </span>
