---
layout: post
title: گذروازه‌های امن
category: [امنیت]
tags: [امنیت, ریاضیات, گذرواژه]
date: 2017-05-25 14:18:00 +0330
published: true
permalink: secure-passwords
summary: شاید وقتی برای اولین بار به برنامه نویسی بازی‌های کامپیوتری فکر کنیم احتمالا مهم‌ترین سوال برامون اینکه کامپیوتر به چه طریق همه اشیا رو در محل درستشون قرار می‌دهد؟ یا اشیا چگونه توسط کامپیوتر جابجا می‌شن؟ برای پاسخ به این سوالات ابتدا باید به سراغ تعریف نقطه و نحوه قرارگیری اشیا در فضاهای دو بعدی و سه بعدی برویم، دستگاه‌های مختصاتی را بررسی کنیم و سپس به سراغ تعریف خط و بردار بپردازیم. در این پست ضمن بررسی موارد یاد شده، به سراغ بررسی کابردهای خطوط هم خواهیم رفت و سیستم line-line collision detection را هم با هم بررسی خواهیم کرد.
excerpt_separator: <!--more--> 
uuid: 7fb6f37f-8800-45dc-a3cb-a9f814aedf48
comments: true
series:
description: شاید وقتی برای اولین بار به برنامه نویسی بازی‌های کامپیوتری فکر کنیم احتمالا مهم‌ترین سوال برامون اینکه کامپیوتر به چه طریق همه اشیا رو در محل درستشون قرار می‌دهد؟ یا اشیا چگونه توسط کامپیوتر جابجا می‌شن؟ برای پاسخ به این سوالات ابتدا باید با تعریف نقطه و خط آشنا بشیم.
---
چند وقت پیش، مثل هر روز صبح بعد از نشستن پشت میز کارم و قبل از شروع کار، به سراغ چک کردن e-mailهایی رفتم که از شب گذشته تا صبح برایم ارسال شده بودند؛ در این بین هم یک e-mail از بخش IT Administration شرکت دریافت کرده بودم.
این e-mail که با عنوان "دستور العمل انتخاب گذرواژه‌های امن" ارسال شده بود، قصد داشت تا به کارمندان سازمان نحوه انتخاب گذرواژه‌هایی که در برابر حملات Brute Force امنیتی بالایی دارند، را آموزش بدهد.

با توجه به اینکه هر از چند گاهی، در مورد نحوه ساخت گذرواژه‌های امن، مورد سوال قرار می‌گیرم و از آنجایی که نسبت به شیوه و چگونگی انجام کارها، غالبا روش‌های خاصی دارم، قصد داشتم تا با اشتراک گذاشتن مواردی که در e-mail یاد شده، عنوان شده بودند و ذکر نظرم نسبت به هر کدوم از اونها و در پایان با ارائه یک تکنیک که کمک شایانی به امن‌ شدن گذرواژه‌های ساده می‌کند، نظراتم رو با شما هم به اشتراک گذاشته باشم.


<span class="number-box">۱</span><span class="font-color-white">متن اصلی:</span> گذرواژه باید حداقل دوازده کاراکتر داشته باشد.

<span class="font-color-white">نظر من:</span> هر چند که امنیت گذرواژه‌ها تا حد زیادی به نوع حمله‌ای که قصد نفوذ به سیستم را دارد، هم وابسته است. اما باور رایج غلطی وجود دارد که یک گذرواژه کوتاه ولی حاوی کاراکترهای تصادفی را امن‌تر از گذرواژه‌ای با طول زیاد، ولی حاوی کلمات ساده و معنا داری که به خاطر سپاری آنها راحت هستند، می‌داند که این مطلب به کل اشتباه است، برای مثال، گذرواژه &quot;goandtypeyourscriptanddriktea&quot; از گذرواژه &quot;*G&>0$!3&quot; امن‌تر است! این موضوع ناشی از آنتروپی و ارتباط آن با طول رشته‌هاست که در ادامه به آن خواهیم پرداخت.


<span class="number-box">۲</span><span class="font-color-white">متن اصلی:</span> گذرواژه بهتر است ترکیبی از اعداد، علائم، حروف بزرگ و حروف کوچک باشد.

<span class="font-color-white">نظر من:</span> این مورد کاملا درست است. می‌دانیم که ما در زبان انگلیسی، ۲۶ حرف کوچک و ۲۶ حرف بزرگ داریم. علاوه بر اینها ۱۰ عدد و ده‌ها علائم نگارشی مانند ؟، !، $، # و ... را هم در نظر بگیرید - ۳۲ علامت نگارشی بر روی صفحه کلید استاندارد انگلیسی. حال فرض کنید قصد انتخاب گذرواژه‌ای تنها با استفاده از ۶ عدد را دارید، برای این انتخاب، یک میلیون امکان وجود دارد! اگر دایره کاراکترهای مجاز، در گذرواژه شش کاراکتریمان را به ترکیب اعداد و حروف کوچک انگلیسی گسترش دهیم، تعداد انتخاب‌هایمان بالغ بر ۳۰۰ میلیون خواهد بود و حال اگر حروف بزرگ هم به این دایره وارد شوند، تعداد انتخاب‌هایمان به ۲ بیلیون می‌رسد و اضافه کردن علائم نگارشی، این مقدار را به بالغ از صدها بیلیون می‌رساند!

ترکیب توصیه شماره ۱ و ۲ این متن، ما را به بالغ بر $10^23$ گزینه ممکن می‌رساند!

<span class="number-box">۳</span><span class="font-color-white">متن اصلی:</span> یک کلمه معنادار یا ترکیبی از چند کلمه معنادار نباشد.

<span class="font-color-white">نظر من:</span> به باور این مساله یکی از مهم‌ترین موارد برای رعایت امنیت گذرواژه انتخابیمان است، ولی در ادامه این مطلب، توضیحی خواهم داد که چگونه می‌توان از کلمات معنادار و یا حتی کلماتی که باور به وجود آنها در حمله‌هایی با استفاده از Dictionary، Password Data bases و cracking list داریم، استفاده کنیم و باز هم گذرواژه امنی داشته باشیم.

متن:

۴- از کاراکترای جایگزینی که واضح هستند د آن استفاده نشده باشد.

نظر من:

در متن به این نکته اشاره شده بود که با توجه به تشابه ظاهری کاراکترهایی مانند 0 (عدد صفر) و O (حرف الفبای انگلیسی)، از جایگزینی این کاراکترها به جای یکدیگر بپرهیزید، چرا که هکر قطعا تمام کاراکترهای جایگزین ممکن برای کلمه "house" مانند "h0use" را امتحان خواهد کرد. این موضوع هم به فاقد ایراد است و این امر در صورتی که هکر به کلمه‌ای در گذرواژه شما مشکوک باشد، کاملا محتمل است.

در ادامه متن هم به یکی از مواردی اشاره شده بود که من غالبا این روش رو به افرادی که حافظه تصویری ضعیف‌تری دارند یا امکان به خاطر سپردن گذرواژه‌های تصادفی برایشان سخت  است، توصیه می‌کنم.

در این روش، ما جمله بسیار ساده "I have bought my first coputer when I was 13 for 300\$" را در نظر می‌گیریم و سپس با استفاده از حروف اول این کلمات، به گذرواژه "Ihbmfcwiw13f300\$" می‌رسیم. یک گذرواژه 16 کاراکتری که به هیچ وجه نامناسب به نظر نمی‌رسد و به خاطر سپردن آن هم بسیار ساده است.

در ادامه شایان ذکر است که به اینکه اشاره کنم که در این مطلب گذرواژه‌ای مانند "[]1c!F^H#A)LMTRQ" به دلیل اینکه به صورت تصادفی تولید شده است، گذرواژه‌ای بسیار امن تلقی شده است.

اما، مساله اصلی اینجاست که هر دو گذرواژه‌ای که در این مطلب توصیه شده‌اند، یعنی "Ihbmfcwiw13f300\$" و "1[]c!F^H#A)LMTRQ" از حروف کوچک و بزرگ انگلیسی، ارقام و علائم تشکیل شده‌اند، در صورتی که فضای حالت این دو گذرواژه در یک حمله Brute Force را مورد بررسی قرار دهیم، هر دو گذرواژه دارای عمق $26 + 26 + 10 + 32 = 94$ در فضای جستجو ما هستند، و هر دو گذرواژه دارای طول 16 کاراکتر هستند.
کاملا واضح است که اندازه فضای حالت ما (شامل همه گذرواژه‌های ممکن ساخته شده با این عمق و اندازه) برابر با 44،480،886،725،444،405،642،219،209،517،120 و یا به عبارتی $4.45 × 10^31$ است.

پس، در سناریو یک حمله آنلاین که در طی آن بوانیم در هر ثانیه یک صد هزار حدس را مورد بررسی قرار دهیم، 14.14 میلیون تریلیون قرن زمان لازم داریم تا تمام ترکیب‌های ممکن را بررسی کنیم.

برای ادامه دادن موضوع، بد نیست که شما هم در جریان باشید که من روش‌هایی که با بررسی یک گذرواژه خاص اعلام می‌کنند که میزان روزهای مورد نیاز برای شکسته شدن یک گذرواژه خاص را اعلام می‌کنند را، معتبر و دقیق نمی‌دونم و بررسی آنتروپی، عمق و طول فضای حالت و امتیازدهی به گذراژه انتخابی بر اساس یک سیستم مبتنی بر تخصیص وزن برای هر یک از پارامترها و حالات اتفاق افتاده در گذرواژه را مطمئن‌تر می‌دانم.

از مطالب بالا بگذریم و سراغ بررسی مورد زیر برویم، به راستی نظرتون در مورد امنیت دو گذرواژه "C4t.............." و "PrXyc.N(n4k77#L!eVdAfp9" چیست؟

کدام یکی از این دو گذرواژه قوی‌تر، امن‌تر و برای شکستن، سخت‌تر هستند؟ کاملا مشخصه که با یک سوال انحرافی سر و کار داریم!

ولی برخلاف اینکه به خاطر سپاری گذرواژه اول به شکل غیر قابل مقایسه‌ای ساده‌تر از گذرواژه دوم است، گذرواژه اول قوی‌تر است!

در واقع، اضافه داشتن یک کاراکتر و ساخته شدن این گذرواژه از ترکیب حروف کوچک و بزرگ انگلیسی به همراه اعداد و علائم نگارشی، باعث می‌شود تا حدس زدن این گذرواژه در یک حمله، نسبت به گذرواژه غیر قابل به خاطر سپاری دوم، 95 بار نیازمند زمان بیشتری باشد.

قطعا اگر مقداری ریاضی یا دانش کمی در زمینه امنیت داشته باشید، با موضوع "آنتروپی" یا میزان تصادفی و غیرقابل پیش‌بینی بودن داده آشنایید. پس حتما سوال اصلی برای شما اینجاست که با توجه به تفاوت فاحش میزان آنتروپی دو گذرواژه و آنتروپی کم گذرواژه اول، چرا این گذرواژه امن‌تر از مورد دوم است!؟

همه افراد بر این باورند یا حداقل اینگونه یاد گرفته‌اند که قدرت و امنیت بالای گذرواژه‌ها ناشی از "آنتروپی بالا" آنهاست، اما وقتی که تنها تکنیک موجود در سناریو حمله ما، حدس زدن گذرواژه‌های محتمل باشد، این منطق چندان خردمندانه به نظر نمی‌رسد.

در ضمن، تمامی مطالب مربوط به dictionaryها، password data baseها و cracking listها رو فراموش کنید!

قطعا عبارت C4t در تمام dictionaryها پیدا می‌شود ولی کسی که قصد حمله به شما را دارد، نسبت به اینکه گذرواژه شما چگونه به نظر می‌رسد هیچ اطلاعاتی ندارن! پس خیلی زود باید از پیدا کردن گذرواژه شما صرف نظر کند و سراغ هدف بعدی برود یا باید تا جایی که به جواب درست برسد، اقدام به حدس زدن تمام ترکیب‌های ممکن کند، چرا که به جز برابری گذرواژه حدس زده شده با گذرواژه اصلی، هیچ راهی برای وی وجود ندارد تا بداند که آیا عبارت C4t در گذرواژه ما وجود دارد یا خیر!

سخن آخر من، و اصلی‌ترین توصیه من برای ساخت گذرواژه‌های امن که حتی به ما این امکان را می‌دهد تا در گذرواژه‌هایمان از کلمات معنادار هم استفاده کنیم، تکنیکی است به نام Padding.

لزومی نیست که یک گذرواژه برای امن بودن، حتما طول زیادی داشته باشد، بلکه یک گذرواژه با طول کوتاه که امکان به خاطر سپاری آن هم وجود دارد، در صورتی که با تکنیک padding درآمیخته شود، می‌تواند برای ما گذرواژه‌ای "بسیار قوی" تولید کند.

بعد نیست این را هم بدانیم که این تکنیک، قادر است تا تمام کلمات موجود در یک dictionary را شکست دهد، برای مثال گذرواژه ساده "Password" را در نظر بگیرید که چهارمین گذرواژه پرکاربرد دنیاست، با تغییر این گذرواژه به "Password."، گذرواژه‌ای ساخته‌ایم که در هیچ dictionary موجود نیست.

در پایان بهتر است این نکته را در نظر داشته باشید که نمونه‌های ارائه شده از تکنیک padding، صرفا جنبه مثال را داشتند و بهتر است برای اعمال padding در گذرواژه‌هایمان تنها از "." استفاده نکنیم، چرا که در این صورت ترکیب مختلف نقاط، به دایره جستجوی حمله کنندگان اضافه خواهد شد. 

هر فردی باید روش شخصی padding خودش را ابداع کند.

می‌توانیم padding را در ابتدا، میانه و انتهای گذرواژه‌هایمان اضافه کنیم.

مطمئن باشید که تولید همچین گذروازه‌ای که به اندازه کافی بلند است و امکان به خاطر سپاری آن هم ساده است، بسیار امن و قوی است.