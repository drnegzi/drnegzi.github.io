---
layout: post
title: مشاهده فایل‌های تصویری با Photo Viewer در Windows 10
category: [عمومی]
tags: [عمومی, Windows 10 tweak]
date: 2016-03-30 18:49:00 +0330
published: true
permalink: /post/associate-files-with-photo-viewer-in-windows-10
comments: true
series:
summary: یکی از مواردی که در اولین تجربه من در کار کردن با Windows 10 عجیب بود، اجبار Microsoft به استفاده از Photos به جای Windows Photo Viewer برای مشاهده فایل‌های تصویری بود. در این پست قصد دارم تا راه حلی برای این مشکل و ایجاد امکان تنظیم کردن Windows Photo Viewer به عنوان نمایش دهنده پیش فرض فایل‌های تصویری ارائه کنم.
description: یکی از مواردی که در اولین تجربه من در کار کردن با Windows 10 عجیب بود، اجبار Microsoft به استفاده از Photos به جای Windows Photo Viewer برای مشاهده فایل‌های تصویری بود. در این پست قصد دارم تا راه حلی برای این مشکل و ایجاد امکان تنظیم کردن Windows Photo Viewer به عنوان نمایش دهنده پیش فرض فایل‌های تصویری ارائه کنم.
uuid: 573888f1-af85-471f-901b-68dad10ed9bb
excerpt_separator: <!--more--> 
---
اولین چیزی که پس از نصب Microsoft Windows 10 کاربرها رو اذیت میکنه، اصرار عجیب Microsoft برای مجبور کردن کاربرها به استفاده از برنامه‌هایی است که خود Microsoft به صورت پیش فرض در نظر گرفته.

یکی از این موارد که در اولین تجربه من در کار کردن با Windows 10 خیلی عجیب بود، اجبار Microsoft به استفاده از <span class="highlight-text">Photos</span> به عنوان نمایش‌ دهنده پیش فرض فایل‌های تصویری بود؛ برنامه Metroی جدیدی که در Windows 10 جایگزین برنامه قدیمی و خوب <span class="highlight-text">Winodws Photo Viewer</span> این سیستم عامل شده.

در Windows 10 امکان جایگزین کردن <span class="highlight-text">Photos</span> با برنامه‌های دیگر به عنوان نمایش دهنده پیش فرض فایل‌های تصویری وجود دارد، اما در صورتی که مثل من قصد داشته باشید تا از <span class="highlight-text">Windows Photo Viewer</span> برای این کار استفاده کنید، ظاهرا راه حلی وجود ندارد.

متاسفانه در اولین تلاش برای انجام این تغییر در برنامه پیش فرض نمایش فایل‌های تصویری در Windows 10 به نتیجه‌ای نمی‌رسیم، نه می‌توان <span class="highlight-text">Windows Photo Viewer</span> را در لیست نرم افزارهایی که در گزینه تنظیمات <span class="highlight-text">Open with</span> مربوط به فایل‌های تصویری موجود هستند، پیدا کرد و نه می‌توان از طریق <span class="highlight-text">Control Panel</span> به نتیجه‌ای رسید. در <span class="highlight-text">Control Panel</span> تنها به ما این اجازه داده می‌شود تا فایل‌های <span class="highlight-text">TIFF</span> را با <span class="highlight-text">Windows Photo Viewer</span> مشاهده کنیم.

اما مقایسه <span class="highlight-text">Registry</span> سیستم عامل Windows 10 با Windows 8.1 و تفاوت مقادیر مسیر <span class="highlight-text">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations</span> در دو سیستم عامل، باعث شد تا تصمیم بگیرم به صورت دستی، مقادیر موجود در Windows 8.1 رو در Windows 10 هم ایجاد کنم.

و این کار دقیقا راه حل مشکلی بود که برای تنظیم کردن <span class="highlight-text">Windows Photo Viewer</span> به عنوان برنامه پیش فرض مشاهده فایل‌های تصویری در Windows 10 داریم!

من برای راحت کردن فرآیند اضافه کردن مقادیری که در Windows 10 در مسیر یاد شده موجود نیستند، یک فایل <span class="highlight-text">batch</span> درست کردم، که همه فرمت‌هایی که امکان نمایششان با <span class="highlight-text">Windows Photo Viewer</span> وجود دارد رو به مسیر یاد شده در <span class="highlight-text">Registry</span> اضافه می‌کنه، شما می‌تونید این فایل رو از [اینجا](https://github.com/theskn/adding-windows-photo-viewer-values-to-registery-batch/archive/master.zip
) دانلود کنید و با اجرای اون مقادیر یاد شده به صورت اتوماتیک به <span class="highlight-text">Registry</span> شما اضافه می‌شه.

بعد از تغییر مقادیر <span class="highlight-text">Registry</span> باید به برنامه <span class="highlight-text">Setting</span> بریم و از قسمت <span class="highlight-text">Default apps</span> روی گزینه <span class="highlight-text">Set defaults by app</span> بزنیم.

حالا می‌تونیم به راحتی فرمت‌هایی که دوست داریم اون‌ها رو با <span class="highlight-text">Windows Photo Viewer</span> مشاهده کنیم تنظیم کنیم.
