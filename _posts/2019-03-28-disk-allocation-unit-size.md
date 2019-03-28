---
layout: post
title: Disk allocation unit size چیست؟
category: [عمومی]
tags: [Hard disk]
date: 2019-02-16 22:57:00 +0100
published: true
permalink: disk-allocation-unit-size
summary: همه ما هر روز مسئول حل مسائلی حیاتی و مهم در سازمان‌هایی هستیم که در آنها مشغول به فعالیتیم. اما چگونه می‌توان مسائل بزرگ و پیچیده را به اجزایی کوچک‌تر شکست و اهمیت اجزایی که برای رسیدن به موفقیت باید حل شوند را سنجید؟ چگونه می‌توان مسائل را به ساده‌ترین شکل ممکن بیان کرد و به در نهایت به دستور العمل لازم برای رسیدن به موفقیت رسید؟
excerpt_separator: <!--more--> 
uuid: a5d2c075-1f7a-4106-a694-6de0f81166ea
comments: true
series: 
description: بررسی چگونگی ارائه مدل‌ها و راه حل‌های ارائه راهکارهای خلاق و نوآورانه در شرکت‌ها و سازمان‌های بزرگ، به جهت ساده سازی مسائل بزرگ و پیچیده‌ای که هر روز با آنها مواجه می‌شویم.
---
خیلی از افراد در محیط Windows به هنگام format کردن driveهای مختلف، وظیفه مدیریت کردن ویژگی‌های partitionهاشون رو بر عهده سیستم عامل رها می‌کنن. این کار به خودی خود دچار مشکلی نیست، ولی بعضی مواقعی هم وجود دارند که تنظیم این ویژگی‌ها به صورت دستی، برای ما مفیدتر از تنظیمات پیش‌فرض سیستم عامل باشن. در این پست قصد دارم تا در مورد یکی از ویژگی‌های قابل تنظیم در هنگام format کردن driveهایمان، یعنی <span class="highlight-text">allocation unit</span>، و هدف و نحوه بهره‌مند شدن از این ویژگی بنویسم.

قطعا همه کاربران Windows dialogue زیر رو، که موقع format کردن یک drive به نمایش درمیاد رو به خاطر دارند. با هم نگاهی اجمالی به قسمت‌های مختلف این پنجره بیاندازیم:

<img class="post-image image-responsive" src="https://theskn.github.io/assets/img/2019-03-28/format-dialogue.png"/>

<span class="font-color-white">Capacity: </span>مشخص کننده میزان ظرفیت کل partitionیست که قصد format کردن آن را داریم.

<span class="font-color-white">Volume lablel: </span>از طریق این ویژگی می‌توانیم برای driveمان یک اسم دلخواد انتخاب کنیم.

<span class="font-color-white">File system: </span>از طریق این گزینه می‌توانیم [file system](https://docs.microsoft.com/en-us/windows/desktop/fileio/file-systems) مورد نظرمان را انتخاب کنیم، در Windows 10 به جز برخی از نسخه‌های Enterprise، حق انتخاب ما محدود به [NTFS](https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview) و یا REFS است؛ هر چند که برای partitionهای کوچک، FAT و [FAT32](https://support.microsoft.com/en-au/help/154997/description-of-the-fat32-file-system) هم به این انتخاب‌ها اضافه می‌شوند.

<span class="font-color-white">Perform a quick format: </span>به صورت عادی، دستور format ابتدا drive را به جهت پیدا کردن [bad sector](https://www.howtogeek.com/173463/bad-sectors-explained-why-hard-drives-get-bad-sectors-and-what-you-can-do-about-it/)های احتمالی مورد بررسی قرار می‌دهد. این گزینه باعث می‌شود تا format بدون اجرای این تست، اجرا شود.

<span class="font-color-white">Enable file and folder compression: </span>باعث می‌شود تا در این partition، تمام fileها به صورت فشرده ذخیره شوند. معمولا به دلیل سربار بالای اجرای این ویژگی، از آن استفاده نمی‌شود. همانطور که در تصویر هم می‌بینیم، این ویژگی در نسخه Windows دستگاه من، از طریق format dialogue قابل دسترسی نیست.

<span class="font-color-white">Allocation unit size: </span>به نظر من جالب‌ترین ویژگی این dialogue، همین گزینه است. گزینه‌ای که مقادیر مرموز زیادی بین 4096 تا 2048K را ارائه می‌دهد، ولی ما معمولا آن را به صورت defaul رها می‌کنیم. این مقادیر در واقع مشخص کننده کوچکترین فضایی هستند که می‌تواند به یک file اختصاص یابد. یک partition به واحدهای کوچکتری تقسیم می‌شود.هنگامی که fileها روی یک partition ذخیره می‌شوند، به بخش‌های کوچکتری تقسیم می‌شوند که هر بخش در واقع، داخل یکی از این واحدها قرار می‌گیرد.

پس یک partition با مقدار allocation unit برابر 4096، به بخش‌های کوچکتر که هر کدام 4096 byte هستند، تقسیم می‌شود. برای مثال، یک file با حجم 1MB = 1024K روی partition مفروض، به 250 بخش، تقسیم می‌شود و یا اگر allocation unit ما برابر با 64K باشد، به 16 بخش تقسیم می‌شود. این تفاوت به این معنی است که دستگاه الکترومکانیکی ما به هنگام نوشتن و خواندن این file نزدیک به ۱۶٪ کار کمتری انجام می‌دهد.

