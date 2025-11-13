---
title: جلسه ۹ تحلیل فضایی
---
#آشنایی با ابزار buffer

ابزار بافر برای تعیین محدوده‌هایی مانند گسل یا بیمارستان، بکار می‌رود به طوری که می‌توان با استفاده از آن تعیین کرد که محدوده مثلا ۱۵۰ متری اطراف گسل را نشان دهد.
برای ثبت اطلاعات بافرها روی جدول گسل‌ها، باید یک فیلد جدید اضافه کنیم:
add field/ name: buffer/ data type: long/ save

طریقه استفاده از ابزار بافر:
analysis/geoprocessing/ toolboxes/ proximity/ buffer
input: لایه گسل‌ها
distance: مثلا ۱۵۰ متر
dissolve type: 
no disslove; هر گسل حریم جداگانه‌ای دارد و نقاط تقاطع را می‌توان دید
dissolve all output; ترکیب حریم‌ها و یکی شدن حریم‌های مشترک
dissolve features using; فقط حریم‌هایی که ویژگی‌های مشترک دارند با هم ترکیب می‌شوند

حال اگر بخواهیم که چند فاصله را یک جا داشته باشیم از ابزار multiple ring buffer استفاده می‌کنیم و با توجه به آن distance ها را انتخاب می‌کنیم.
سپس می‌توانیم با استفاده از symbology و graduated color رنگ هر فاصله را تعیین کنیم.
![توضیح تصویر](https://www.dropbox.com/scl/fi/fcu3zuzz86eli1ce5s73a/IMG_0095.HEIC?rlkey=2s2b3wd5jpu1784beoc4skvjf&st=nan1abbn&dl=0)
# ابزار erase
بطور مثال برای حذف کردن نقاط گسل از روی نقشه از این ابزار استفاده می‌کنیم. 
analysis/geoprocessing/ toolboxes/ overlay/ erase
![توضیح تصویر](https://www.dropbox.com/scl/fi/yhlrfwpr6j7f3fhqil9yu/IMG_0096.HEIC?rlkey=3rhlcm7sfneh21eqch2gjlmf7&st=qdk3nbgt&dl=0)
# ابزار intersect
برای مشخص کردن گسل‌هایی که دقیقا داخل محدوده هستند و روی هم تطابق دارند بکار می‌رود
analysis/geoprocessing/ toolboxes/ overlay/ intersect
![توضیح تصویر](https://www.dropbox.com/scl/fi/flawf5vneyws6svw0c2ws/IMG_0097.HEIC?rlkey=j2btnjvwq16qr6oizcco56cod&st=uu5zzkhi&dl=0)

# ابزار identity
برای ثبت کردن محورهای گسل روی نقشه (حک کردن).
analysis/geoprocessing/ toolboxes/ overlay/ identity
![توضیح تصویر](https://www.dropbox.com/scl/fi/yd33t13qvn70z13d40cfe/IMG_0098.HEIC?rlkey=sn6qjfxq64i0x9yr2z95cqube&st=e3f3tu2d&dl=0)

# تعیین مساحت‌های هر نوع کاربری در لایه زونینگ
باز کردن لایه زونینگ/ بازکردن جدول attribute/ کلیک‌راست روی فیلد shape area/ انتخاب گزینه summerize/ نقشه ورودی یا input: نقشه محلات/ فیلد shape area را انتخاب می‌کنیم و statistic type را روی sum می‌گذاریم/ case field: codeiv_lable and distance.
سپس می‌توانیم ببینم مجموع مساحت هر نوع زون را ببینیم و دریابیم که در هر فاصه ۵۰، ۱۵۰، ۳۰۰ چند قطعه از هر زون وجود دارد.
در نهایت می‌توانیم با خروجی جدول به فرمت csv. و استفاده از ابزار pivot table آمار و داده‌های جدول را در اکسل تحلیل کنیم.
هدف از انجام این پروژه نهایی، اندازه‌گیری این است که در هر محله و یا زون چند درصد از خط گسل در آن وجود دارد.
