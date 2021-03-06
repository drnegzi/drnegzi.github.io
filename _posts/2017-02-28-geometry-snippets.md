---
layout: post
title: مسائلی در هندسه
category: [آموزشی]
tags: [آموزشی, ریاضیات, برنامه نویسی]
date: 2017-02-27 23:18:00 +0330
published: true
permalink: geometry-snippets
summary: شاید وقتی برای اولین بار به برنامه نویسی بازی‌های کامپیوتری فکر کنیم احتمالا مهم‌ترین سوال برامون اینکه کامپیوتر به چه طریق همه اشیا رو در محل درستشون قرار می‌دهد؟ یا اشیا چگونه توسط کامپیوتر جابجا می‌شن؟ برای پاسخ به این سوالات ابتدا باید به سراغ تعریف نقطه و نحوه قرارگیری اشیا در فضاهای دو بعدی و سه بعدی برویم، دستگاه‌های مختصاتی را بررسی کنیم و سپس به سراغ تعریف خط و بردار بپردازیم. در این پست ضمن بررسی موارد یاد شده، به سراغ بررسی کابردهای خطوط هم خواهیم رفت و سیستم line-line collision detection را هم با هم بررسی خواهیم کرد.
excerpt_separator: <!--more--> 
uuid: 7fb6f37f-8800-45dc-a3cb-a9f814aedf48
comments: true
series: "برنامه نویسی، مقدمات ریاضی و فیزیک"
description: شاید وقتی برای اولین بار به برنامه نویسی بازی‌های کامپیوتری فکر کنیم احتمالا مهم‌ترین سوال برامون اینکه کامپیوتر به چه طریق همه اشیا رو در محل درستشون قرار می‌دهد؟ یا اشیا چگونه توسط کامپیوتر جابجا می‌شن؟ برای پاسخ به این سوالات ابتدا باید با تعریف نقطه و خط آشنا بشیم.
---
این مطلب دومین قسمت آموزشی از سری &quot;برنامه نویسی، مقدمات ریاضی و فیزیک&quot; خواهد بود، در [قسمت قبلی](  http://blog.kianooshnaghavi.com/:posts/points-and-lines.html) به عنوان اولین قدم، به بررسی نقاط، خطوط و معادلات خط‌ها پرداختیم، پیاده سازی آنها در کد را دیدیم و نمونه‌ای از کاربرد معادلات خطوط و یا حالت دو خط نسبت به یکدیگر در بازی‌های کامپیوتری را بررسی کردیم.

در این قسمت قصد داریم تا با هم مسائل و قضایا و یا اشکالی مانند دایره و کره را بررسی کنیم که در ادامه این مجموعه برای ما پرکاربرد خواهند بود. در انتها هم سعی خواهیم کرد تا یک مثال کاربردی را با مطالب این بخش، بررسی کنیم.

<div class="post-inline-title">فاصله دو نقطه</div>
به زمانی فکر کنیم که قصد داریم تا فاصله دو کاراکتر از یکدیگر را بررسی کنیم یا یک AI را در نظر بگیریم که قبل از حمله کردن، منتظر است تا بازیکن در فاصله خاصی از وی قرار داشته باشد. فارغ از مساله‌ای که با آن روبروییم، مهم‌ترین چیز کارآمد بودن و سریع بودن شیوه‌ایست که با استفاده از آن قصد داریم تا فاصله بین دو نقطه را محاسبه کنیم. راحت‌ترین روش برای انجام این کار، قضیه فیثاغورث است.

<p><blackquote class="alert">
قضیه فیثاغورث:<br>
$a^2 + b^2 = c^2$<br>
که در آن a و b اضلاغ قائم مثلث و c وتر <a id="footnote-ref-001" style="font-style: normal;" class="foot-note-reference" href="#footnote-001">[۱]</a> هستند.
</blackquote></p>

صورت تصویری قضیه فیثاغورث به شکل زیر است:
<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2017-02-27/ch002-right-triangle.png"/>
دقت داشته باشید که این قضیه تنها برای <span class="font-color-white">مثلث قائم الزاویه</span> صادق است.


صورت عکس قضیه فیثاغورت

اگر a و b و c طول اضلاع یک مثلث باشند به طوریه که شرط $a^2 + b^2 = c^2$ برقرار باشد، آنگاه آن مثلث قائم الزاویه است و دارای وتری به طول c است.

کاربردهای مثلث قائم الزاویه را بعدا و هنگاه بررسی عملیات برداری بررسی خواهیم کرد، اما فعلا به استفاده از خواص مثلث‌های قائم الزاویه برای پیدا کردن فاصله بین دو نقطه، بسنده می‌کنیم.

فرض کنید که دو نقطه <bdi class="ltr-direction">$P_1(X_1, Y_1)$</bdi> و <bdi class="ltr-direction">$P_2(X_2, Y_2)$</bdi> دو نقطه مانند شکل زیر باشند:
<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2017-02-27/ch002-the-pythaforean-example.png"/>
کاملا واضح است که می‌توانیم با رسم خطی که از $P_1P_2$ می‌گذرد و در نظر گرفتن آن به عنوان وتر، یک مثلث قائم الزاویه رسم کنیم، راس سوم این مثلث هم نقطه‌ای مانند <bdi class="ltr-direction">$T(X_2, Y_1)$</bdi> است. همان طور که واضح است، ضلع $P_1T$ دارای طول $(X_2 - X_1)$  و ضلع $P_2T$ دارای طول $(Y_2 - Y_1)$ است. حال با استفاده از قضیه فیثاغورث داریم:


<bdi class="ltr-direction">
<span>     
$(P_1P_2)^2 = (P_1T)^2 + (P_2T)^2$
<br> 
$= (X_2 - X_1)^2 + (Y_2 - Y_1)^2$
</span>
</bdi>

با بازنویسی رابطه بالا، به فرمول <span class="highlight-text">محاسبه فاصله دو نقطه در فضای دو بعدی</span> می‌رسیم:

<bdi class="ltr-direction">
<span>
$P_1P_2 = √{(X_2 - X_1)^2 + (Y_2 - Y_1)^2}$
<br>
$P_1P_2 = ((X_2 - X_1)^2 + (Y_2 - Y_1)^2)^(1/2)$
</span>
</bdi>

که دو نقطه <bdi class="ltr-direction">$P_1(X_1, Y_1)$</bdi> و <bdi class="ltr-direction">$P_2(X_2, Y_2)$</bdi> روی خط واقع شده‌اند.

حال وقت آن رسیده که به صورت نمونه، پیاده سازیی از مطلب بالا ارائه دهیم:
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
// input: P1 - an array of 2 floats representing point 1
//        P2 - an array of 2 floats representing point 2
// output: the distance between the two given points

float Distance2D(float *P1, float *P2)
{
     return (float)sqrt(pow(P2[0] – P1[0], 2) + 
                        pow(P2[1] – P1[1], 2);
}
</pre>
</div>
در نظر داشته باشید که تابع <bdi class="ltr-direction">pow(x, 2)</bdi> در عین کاربرد فراوان، تابعی کند محسوب می‌شود، به طوریکه با ضرب کردن عددی که قصد به توان رساندن آن را داریم، به تعداد دفعات لازم، در خودش، ما را سریع‌تر به جواب می‌رساند. هر چند که اگر از یکی از compilerهای شرکت Microsoft استفاده می‌کنید، می‌توانید با استفاده از #pragma intrinsic به میزان قابل توجهی، سرعت اجرای اکثر توابع سرفایل &#60;
cmath&#62; را افزایش دهید.

استفاده از این دستور، این امکان را فراهم می‌آورد اکثر فراخوانی توابع ریاضی، ترجیحا به جای قرار گیری در function stack، مستقیما به math coprocessor فرستاده شوند، که این مساله باعث افزایش سرعت چشمگیری در اجرای این دست از توابع می‌شود.

اجازه بدهید که فرمول مطرح شده را با قضیه فیثاغورث ترکیب کنیم و مثال زیر را با هم بررسی کنیم:
فرض کنید مثلثی داریم که سه نقطه <bdi class="ltr-direction">$A(20, 50)$</bdi> و <bdi class="ltr-direction">$B(100, 90)$</bdi> و <bdi class="ltr-direction">$C(70, 150)$</bdi> رئوس آن هستند، می‌خواهیم بدانیم که آیا این مثلث قائم الزاویه است یا خیر؟
طبق قضیه فیثاغورث می‌دانیم که یک مثلث در صورتی قائم الزاویه است که داشته باشیم: $a^2 + b^2 = c^2$ پس ابتدا باید طول اضلاع مثلث داده شده را بیابیم.

برای AB داریم:

<bdi class="ltr-direction">
<span>
$√{(100 - 20)^2 + (90 - 50)^2} = AB$
<br>
$= √{8000}$
</span>
</bdi>

و برای BC داریم:

<bdi class="ltr-direction">
<span>
$√{(70 - 100)^2 + (150 - 90)^2} = BC$
<br>
$= √{4500}$
</span>
</bdi>

و برای CA داریم:

<bdi class="ltr-direction">
<span>
$√{(70 - 20)^2 + (150 - 50)^2} = BC$
<br>
$= √{12500}$
</span>
</bdi>

و حالا با جاگذاری طول اضلاح به دست آمده در قضیه فیثاغورث داریم:

<bdi class="ltr-direction">
<span>
$(√{800})^2 + (√{4500})^2 = (√{12500})^2$
<br>
$12500 = 12500$
</span>
</bdi>

پس مثلت در نظر گرفته شده قائم الزاویه است.

رابطه موجود بین فاصله دو نقطه، تنها مربوط به فضای دو بعدی نیست و می‌توان آن را به فضاهای با ابعاد بیشتر هم تعمیم داد. با این اوصاف برای فضای سه بعدی و با اضافه شدن z داریم:

<bdi class="ltr-direction">
<span>
$P_1P_2 = √{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (z_2 - z_1)^2}$
</span>
</bdi>

در نظر داشته باشید که نقاط <bdi class="ltr-direction">$P_1(x_1, y_1, z_1)$</bdi> و <bdi class="ltr-direction">$P_2(x_2, y_2, z_2)$</bdi> روی یک خط قرار دارند.

رابطه پرکاربرد دیگر، رابطه تعیین نقطه وسط است. در مواقعی که نیاز داشتیم تا نقطه میانی بین دو نقطه مثل <bdi class="ltr-direction">$P_1(x_1, y_1)$</bdi> و <bdi class="ltr-direction">$P_2(x_2, y_2)$</bdi> را بدست آوریم، تنها کافیست که از فرمول زیر استفاده کنیم:

<bdi class="ltr-direction">
<span>
$M{({x_1 + x_2}/2, {y_1 + y_2}/2)}$
</span>
</bdi>
 
اجازه دهید تا پیاده‌سازی این فرمول را با هم بررسی کنیم:
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
// input: P1 - an array of 2 floats representing point 1
//        P2 - an array of 2 floats representing point 2
// output: the midpoint between the two given points

float *Find2dMidPoint(float *P1, float *P2)
{
     float *temp = new float[2];
     
     temp[0] = (P1[0] + P2[0]) / 2.0f;
     temp[1] = (P1[1] + P2[1]) / 2.0f;
     
     return temp;
}
</pre>
</div>
همانطوری که می‌بینید برای تخصیص حافظه کافی به متغیر temp از کلیدواژه new استفاده کردیم. همیشه باید به خاطر داشته باشیم تا بعد از به پایان رسیدن کارمان با متغیرهایی که از این طریق به آنها حافظه اختصاص داده شده است، حافظه مربوط به آنها را با استفاده از کلیدواژه delete پاکسازی کنیم.

دقیقا همانند رابطه فاصله بین دو نقطه، رابطه پیدا کردن نقطه میانی را هم می‌توان به فضاهایی با ابعاد بیشتر تعمیم داد، پیاده سازی این حالت را با هم بررسی می‌کنیم:
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
// input: P1 - an array of 3 floats representing point 1
//        P2 - an array of 3 floats representing point 2
// output: the midpoint between the two given points

float *Find3dMidPoint(float *P1, float *P2)
{
     float *temp = new float[3];
     
     temp[0] = (P1[0] + P2[0]) / 2.0f;
     temp[1] = (P1[1] + P2[1]) / 2.0f;
     temp[2] = (P1[2] + P2[2]) / 2.0f;
     
     return temp;
}
</pre>
</div>

<div class="post-inline-title">سهمی‌ها</div>
آیا تا به حال به مسیر حرکت یک توپ بسکتبال بعد از پرتاب شدن دقت کردید؟ آیا این توپ روی یک مسیر صاف حرکت می‌کند؟ خیر، مسیر حرکت این توپ بیشتر به صورت منحنی و قوس‌دار به نظر می‌رسد. در واقع حرکت تمام پرتابه‌ها روی مسیری به شکل سهمی اتفاق می‌افتد.

چهار نوع از انواع مختلف سهمی‌ها به این شکل هستند:
<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2017-02-27/ch002-four-types-of-porabolas.png"/>
برای تعیین معادله یک سهمی، از دو پارامتر استفاده می‌کنیم، پارامتر اول راس <a id="footnote-ref-001" style="font-style: normal;" class="foot-note-reference" href="#footnote-001">[۲]</a> سهمی است و پارامتر دوم محور تقارن <a id="footnote-ref-001" style="font-style: normal;" class="foot-note-reference" href="#footnote-001">[۳]</a> سهمی که از نقطه راس سهمی گذر می‌کند  باعث تقارن دو طرف سهمی با یکدیگر می‌شود. دو فرم کلی برای سهمی‌ها که دارای محور تقارن عموی یا افقی باشند، به شکل زیر بیان می‌شود:

<p><blackquote class="alert">
معادله یک سهمی با راس و محور تقارن عمودی<br>
$y = a(x - h)^2 + k$<br>
که <bdi class="ltr-direction">$(h, k)$</bdi> در آن راس سهمی و محور تقارن هم برابر با <bdi class="ltr-direction">$x= h$</bdi> است.
</blackquote></p>

<p><blackquote class="alert">
معادله یک سهمی با راس و محور تقارن افقی<br>
$x = a(y - k)^2 + h$<br>
که <bdi class="ltr-direction">$(h, k)$</bdi> در آن راس سهمی و محور تقارن هم برابر با <bdi class="ltr-direction">$y= k$</bdi> است.
</blackquote></p>

هنگام نوشتن معادلات سهمی‌ها باید در نظر داشته باشیم که مقدار ثابت a مشخص کننده جهت باز شدن و پهنای عرض بین دو شاخه سهمی است. برای مثال اگر a یک میزان مثبت باشد، سهمیی با محور تقارن عمودی به سمت بالا و سهمیی با محور تقارن افقی به سمت راست باز می‎شود و به همین صورت اگر a مقداری منفی باشد، این جهت‌ها عکس می‌شوند. همچنین هر چه a به صفر نزدیک‌تر باشد، باعث پهنای بیشتر عرض سهمی در می‌شود و هرچه میزان <bdi class="ltr-direction">$|a|$</bdi> از صفر دورتر باشد، پهنای عرض فاصله بین دو شاخه سهمی کمتر می‌شود. این اطلاعات می‌توانند ما را برای تخمین و پیش‌بینی روی رفتار یک سهمی کمک کنند.

<div class="post-inline-title">دایره‌ها و کرات</div>
یکی از معادلات پرکاربرد دیگری که نیاز به آشنایی با آن داریم، معادله یک دایره است. بررسی مسیر حرکت یک شی دور یک محور ثابت، یا محیط کردن یک دایره به دور یک شی دیگر و استفاده از این دایره برای تشخصیص برخورد دو شی با یکدیگر، نمونه‌ای از مواقعی است در آنها نیاز به شناخت و کار کردن با معادله یک دایره داریم.

با در نظر گرفتن یک دایره بر روی یک صفحه، کاملا مشخص است که یک دایره مجموعه نقاطی است که بر روی یک صفحه در فاصله‌ای ثابت از یک نقطه واقع شده‌اند. نقطه یاد شده، مرکز دایره و فاصله مورد نظر از این نقطه، شعاع دایره نامیده می‌شود.

با در نظر گفتن دو پارامتر بالا، کدام یک از معادله‌هایی که سابق براین بررسی کردیم، می‌تواند به ما فاصله یک نقطه روی دایره از مرکز آن را بدهد؟ بله، قضیه فیثاغورث. پس در واقع می‌توان معادله هر دایره‌ای را تنها با دانستن مرکز و شعاع آن، نوشت. در ضمن شباهت معادله یک دایره با قضیه فیثاغورث را هم در نظر داشته باشید.
 
 اجازه بدهید تا نحوه ذخیره سازی یک دایره در کد را با هم بررسی کنیم:
 <div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
struct Circle
{
     float Center[2];
     float Radius;
}

struct Sphere
{
     float Center[3];
     float Radius;
}
</pre>
</div>

<p><blackquote class="alert">
معادله یک دایره:<br>
<bdi class="ltr-direction">$(x - h)^2 + (y - k)^2 = r^2$</bdi><br>
که در آن <bdi class="ltr-direction">$(h, k)$</bdi> مرکز دایره و r شعاع دایره است.
</blackquote></p>

<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2017-02-27/ch002-right-triangle.png"/>
دایره مشخص شده در شکل بالا، دارای مرکز <bdi class="ltr-direction">$(-2, 2)$</bdi> و شعاع 3 است. با توجه به مطالب بیان شده، می‌توان معادله این دایره را به شکل زیر نوشت:

<bdi class="ltr-direction">$(x + 2)^2 + (y - 2)^2 = 9
     
     


<div class="foot-note-header">پا نویس:</div>
<span id="footnote-001" class="foot-note"><a href="#footnote-ref-001">[۱]:</a> Hypotenuse</span><br>
<span id="footnote-001" class="foot-note"><a href="#footnote-ref-001">[۲]:</a> Vertex</span><br>
<span id="footnote-001" class="foot-note"><a href="#footnote-ref-001">[۳]:</a> Axis of symmetry</span><br>
