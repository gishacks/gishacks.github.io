---
title: جلسه ۱۲ - ساخت نقشه آنلاین
---
# جلسه12
ادامه بحث analysis tools
# ابزار overlay
در این مجموعه با ابزار erase می‌خواهیم حریم گسل را از لایه طرح تفصیلی یرداریم و به نوعی پاک کنیم:
![توضیح تصویر](https://i.postimg.cc/VsqxZ5rc/Screenshot-402.png)
در ادامه می‌خواهیم بفهمیم حریم گسل چه پهنه‌ها و چه سطحی از پهنه‌ها را دربرمی‌گیرد:
با استفاده از ابزار intersect و باز کردن attribute table این لایه و کلیل راست روی لیبل و summarize کردن فیلد را روی shape_area و statistic type را روی sum و case field را روی codeiv_ label قرار می‌دهیم.
![توضیح تصویر](https://i.postimg.cc/DwMH4XDv/Screenshot-403.png)
# identity
هر لایه را روی لایه دیگر غالب می‌زند به عنوان مثال خطوط بافر روی لایه زونینگ باقی می‌ماند
تمرین: می‌خواهیم بدانیم چند درصد از محلاتمان روی گسل قرار دارد
نحوه: روی لایه محلال identity می‌زنیم input آن محلات و output اش بافر گسل است.
از attribute table آن خروجی گرفته و در اکسل وارد می‌کنیم، با استفاده از pivot در قسمت rows آیدی محله و در columns فاصله بافر و در values هم shape area را وارد می‌کنیم و در اتظیمات value آن را روی sum قرار می‌هیم از آنجایی که درصد می‌خواهیم روی سر ستون grand total کلیک راست می‌کنیم و در قسمت value field setting روی % of row total قرار می‌هیم:
![توضیح تصویر](https://i.postimg.cc/zfHMCfZg/Screenshot-404.png)
