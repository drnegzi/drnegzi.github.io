---
layout: post
title: int main vs. void main
category: [عمومی]
tags: [برنامه نویسی, cpp]
date: 2016-08-23 00:08:00 +0330
published: true
permalink: /posts/int-main-vs-void-main
summary: آیا از وجود رباتی در تلگرام که وظیفه دخیره و ثبت کردن پیام‌های رد و بدل شده در کانال‌ها و گروه‌ها را دارد باخبرید؟
excerpt_separator: <!--more--> 
uuid: d8b47e35-602d-48a8-94e2-428c4fcdd4e0
comments: true
series: 
description: ربات‌های زیادی در تلگرام زندگی می‌کند، اما آیا از وجود یک ربات که وظیفه ذخیره پیام‌های ارسال شده در گروه‌ها و کانال‌های تلگرامی را که در آنها عضو است، را دارد نیز باخبرید؟ آیا می‌دانستید این پیام‌ها روی یک سایت به نمایش در می‌آیند؟
---
حدود چند هفته پیش در محل کار، با یکی از همکاران این بحث پیش اومد که آیا در بدنه structها در ++C می‌توان به تعریف توابع نسیت پرداخت یا خیر. هر چند که همکارم با وجود ادعایی که درباره میزان آشنایی خودش با زبان‌های برنامه نویسی مختلف داره، از وجود همچین قابلیتی در ++C مطلع نبود، بلکه حتی وقتی که وی قصد داشت تا کدی برای اثبات این موضوع که نمی‌توان در ++C داخل structها تابع تعریف کرد، بنویسد، کد خود را بدون کاراکتری دخل و تصرف به شکل زیر آغاز کرد!
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
void main()
</pre>
</div>
واقعا دیگه حتی برام مقدور نیست که کوچکترین خیال پردازی یا تصوری در مورد میزان آشنایی این همکارم حتی با پیش پا افتاده‌ترین زبان‌های برنامه نویسی داشته باشم.
اما موضوع اساسیی که اینجا مطرح می‌شود و ممکنه برای خیلی‌های دیگه هم مورد سوال یا سردرگمی باشه، اینکه، کدوم یکی از برنامه‌های زیر درست هستند؟ اولی یا دومی؟
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
void main()
</pre>
</div>
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
void main()
</pre>
</div>
<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
#include <iostream>

int main()
{
   return 0;
}
</pre>
</div>
lksdlfjksdjfksdjf
lsjdfklsfjsaldf
lsjdfkjaskfjklasdf
lajsdlfsadkflsakf

و یا

<div class="ltr-direction font-family-consolas">
<pre class="brush: cpp">
#include <iostream>

void main(
{
   // No return statement...
}
</pre>
</div>