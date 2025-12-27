---
title: تحلیل مطلوبیت
---
# آشنایی با elevation

راه‌های مختلفی برای بدست آوردن elevation داریم.

برای پهنه‌ای مانند تهران، ما خودمان برداشت نمی‌کنیم و از داده‌های ارتفاعی استفاده می‌کنیم.

منبع داده: سازمان نقشه‌برداری

فایل‌هایی که به ما می‌دهد دو نوع هستند

p:عوارض انسان‌ساخت

h: عوارض طبیعی

دو نوع h داریم

h: ۱- نقاط ارتفاعی

h: ۲- خطوط هم‌تراز یا contour

contour: در کانتور همه‌ی نقاطی که روی یک خط هستند، یک ارتفاع دارند

برای اینکه بفهمیم موضع ما چاله است یا تپه: از عدد روی خطوط متوجه می‌شویم.

اگر از بیرون به داخل افزایش مقدار داشته باشیم: با تپه مواجه هستیم.

از خطوط هم‌تراز می‌توانیم شیب را هم دریابیم.

داده‌های وکتوری برای تحلیل سطح بدرد نمی‌خورند.

لایه elevation را باید استفاده کنیم و همچنین این لایه به صورت raster می‌باشد.

برای بدست آوردن لایه الویشن راه‌های مختلفی وجود دارد:

مثال: سایت open topography؛ از این سایت می‌توانیم لایه الویشن را دانلود کنیم.

open topography/ data/ find data map/ محدوده مورد نظرمان را پیدا می‌کنیم / select a region/ مستطیل را حول محدوده مورد می‌کشیم/ فایل SRTM 15+ را دانلود می‌کنیم/ data output format: Geo tiff/ در visualization تغییری ایجاد نمی‌کنیم/ email را وارد کرده و submit را می‌زنیم.

فایل را وارد arcgis pro می‌کنیم. می‌بینیم که کیفیت لایه پایین است. برای حل این مشکل باید فایل رستری را به نقطه و سپس از نقطه تبدیل به فایل رستر کنیم.

1) analysis/ toolboxes/ conversion/ from raster/ raster to point/ input raster: لایه SRTM/ field: value

2) analysis/ toolboxes/ spatial analyst tools/ interoplation/ IDW/ input point feature: فایل نقطه‌ای/ Z value field: grid_code/ بدون تغییر دیگر run می‌کنیم

واحد اندازه‌گیری در این سیستم مختصاتی که داریم، درجه می‌باشد؛ اما ما با متر کار می‌کنیم!

نقشه‌ها در اینترنت معمولا برحسب درجه می‌باشند.

کد جهانی سیستم مختصاتی بر حسب درجه: ۴۳۲۶ درجه

کد جهانی سیستم مختصاتی بر حسب متر برای تهران و محدوده مرکزی ایران: ۳۲۶۳۹ متر

برای تغییر سیستم مختصاتی از درجه به متر: 

analysis/ toolboxes/ projections and transformations/ raster/ project raster/ input raster: idw_raster T/ output coordinate system: کره کنار این بخش را انتخاب کرده و از قسمت جست‌وجو کد جهانی برحسب متر یعنی ۳۲۶۳۹ را سرچ می‌کنیم و WGS 1984 UTM zone 39N را انتخاب کرده و بدون تغییر دیگری run می‌کنیم.

خیلی از ابزاری که با آنها کار می‌کنیم، زیر مجموعه spatial analyst هستند.

مهم‌ترین تحلیل که از تحلیل‌های سطح بدست می‌آوریم، شیب می‌باشد: 

spatial analyst/ surface/ slope/ input raster: idw raster projectraster/ output measurment: percent rise/ z factor: 1

z factor: روی ۱ می‌گذاریم چون ارتفاع و فاصله ما بر حسب متر و با یکای برابر هستند.

شیب صفر درصد: صفر درجه

شیب ۱۰۰ درصد: ۴۵ درجه

شیب بی‌نهایت: ۹۰ درجه

معمولا در شهرسازی، شیب را برحسب درصد می‌گذاریم.

در اینجا می‌بینیم که بطور مثال بیشترین شیب، کمتر یا مساوی ۱۰۰۰ درصد می‌باشد.

علاوه بر درصد شیب، جهت شیب نیز برای ما اهمیت دارد.

برای تحلیل جهت شیب:

surface/ aspect/ input raster: idw raster projectraster/ بدون تغییر دیگری run را می‌زنیم.

در جهت شیب، با درجه جغرافیایی سروکار داریم:

صفر در درجه جغرافیایی: ۹۰ درجه در جدول مختصات و شمال را نشان می‌دهد

همچنین جدول مختصات درجه جغرافیایی، ساعتگرد می‌چرخد و درجه افزایش می‌یابد.

اگر لایه الویشن را داریم و می‌خواهیم لایه contour بسازیم که خطوط هم‌تراز را به ما بدهد:

surface/ contour/ input raster: idw raster projectraster/ contour interval: فاصله خطوط هم‌تراز

همچنین می‌توانیم یک‌بار یک کانتور با اینتروال ۱۰ با نوار خاکستری و ضخامت ۰.۲ بسازیم؛ بعد دوباره یک کانتور دیگر بسازیم با اینتروال ۵۰ و رنگ سیاه و ضخامت ۲ که نقشه‌ای خواناتر داشته باشیم.

برای اینکه نقشه ۲ بعدی ما،‌۳ بعدی شود و سایه‌ها دیده شود:

surface/ hillshade

azimuth: زاویه تابش در طول شبانه‌روز

altitude: زاویه تابش خورشید در طول سال(تابستان و زمستان)

در نیمکره شمالی، azimuth بین ۹۰ تا ۲۷۰ درجه جغرافیایی است.

شرق: ۹۰ درجه جغرافیایی

غرب: ۲۷۰ درجه جغرافیایی

زاویه تابش خورشید در زمستان: کم

زاویه تابش خورشید در تابستان: زیاد

اگر بخواهیم سایه را تحلیل کنیم، باید برویم سراغ عکس‌هایی که در زمستان گرفته شده‌اند.

سایه کمتر: تابستان ظهر

خورشید در نیمکره شمالی بین ۹۰ تا ۲۷۰ درجه جغرافیایی حرکت می‌کند.

در نیمکره شمالی در صبح زاویه جغرافیایی خورشید، بین ۹۰ تا حدود ۱۲۰ است.

زاویه تابش خورشید در تابستان و زمستان از جدول مختصات دکارتی تبعیت می‌کند.


# فرآیند توپولوژی در modelbuilder

analysis/ modelbuilder

فرآیندهای پیشین تا این لحظه را با مدل بیلدر انجام می‌دهیم؛ بطور پیوسته چنان که خروجی مرحله الف، ورودی مرحله ب باشد.

\**بجای فرآیند IDW می‌توانیم از topo to raster استفاده کنیم.**

برای اینکه این مدل، تبدیل به یک ابزار شود:

روی ورودی (آبی ‌رنگ) کلیک‌راست می‌کنیم و نام ورودی را پاک می‌کنیم و سپس enter را می‌زنیم؛ حالا می‌بینیم که مدل غیر فعال می‌شود؛ حالا روی ورودی راست‌کلیک می‌کنیم و parameter را می‌زنیم و save می‌کنیم.

حالا در toolboxes می‌بینیم که در مثلا my project 17 مدل ما ذخیره شده است.

روی مدل‌مان راست‌کلیک می‌کنیم و edit را می‌زنیم.

نام خروجی‌ها را مانند ورودی پاک می‌کنیم.

روی خروجی (های) نهایی راست‌کلیک می‌کنیم و parameters را می‌زنیم و save می‌کنیم.

روی ورودی کلیک‌راست می‌کنیم و rename را می‌زنیم و input DEM layer را می‌زنیم؛ جهت مرتب شدن و زیبا شدن کار.

حالا نام مدل را هم تغییر می‌دهیم به surface analyst.

دو نوع فاصله داریم: نزدیکی (proximity) دسترسی (accesibility)

نزدیکی معمولا به حریم مربوط است؛ و دسترسی معمولا به راه‌ها مرتبط است.

در تحلیل نزدیکی، فرمت raster برای ما مناسب‌تر است.

**## پروژه مناسب برای بررسی فاصله از گسل در محیط رَستری**

یک پروژه جدید باز می‌کنیم و لایه‌های گسل و مناطق شهرداری را باز می‌کنیم

**### آشنایی با ابزار distance**

analysis/ toolboxes/ spatial analyst/ distance/ legacy/ euclidian distance

در تمرین‌های رستری باید ۲ چیز را معین کرد: ۱- محدوده کار   ۲- اندازه سلول‌ها (cell size)

حالا:

input raster or feature source data: gosal

output cell size: 100 چون دقت بیشتری نسبت به عدد پیشنهادی خود نرم‌افزار دارد

run

حالا می‌بینیم که لایه‌ای ساخته شده که در محدوده لایه ورودی‌مان یعنی گسل می‌باشد. برای اینکه محدوده ما در حوزه تهران باشد:

environments/ processing extent/ extent of a layer/ manateghe shahrdari/ run

حالا اگر لایه‌ها را خاموش کنیم و لایه eucdist را روشن کنیم، روی هر نقطه که کلیک کنیم، عددی که به ما می‌دهد، نشان‌دهنده فاصله آن مکان از نزدیک‌ترین گسل می‌باشد.

سیمبولوژی لایه‌های رستری با لایه‌های وکتوری متفاوت است.

اگر روی لایه رستری کلیک‌راست کنیم می‌بینیم که حالات مختلفی وجود دارد:

stretch: نشان‌دهنده طیف

classify: بر اساس دسته‌بندی‌ها (مثلا فاصله از گسل)

و انواع دیگر...

همین کارها را می‌توان برای فاصله از فرودگاه و ... انجام داد.
![توضیح تصویر](https://www.dropbox.com/scl/fi/vmwp1af4hw816zgo3pw7g/WhatsApp-Image-2025-12-20-at-07.20.14.jpeg?rlkey=uq2ouol0sndkeempphjwv4i6i&st=65tdy92i&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/3f8y6oxtepwkagxksprtb/WhatsApp-Image-2025-12-20-at-07.20.16.jpeg?rlkey=inri1pvy8fj18ugrizatx0vrw&st=snbc7mhm&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/h9anwaxlcrnmf702mqcnh/WhatsApp-Image-2025-12-20-at-07.20.17-2.jpeg?rlkey=a3c17wq4wjdtsuio226s55lbz&st=2l4p6g9e&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/rnunc0xofk753wwn70yfv/WhatsApp-Image-2025-12-20-at-07.20.17.jpeg?rlkey=l686xtujq0x4sg1ci0y4740xv&st=j58lmiwz&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/53mbxl4ckrd6xsvq8slsp/WhatsApp-Image-2025-12-20-at-07.20.27.jpeg?rlkey=db3sgbw9prmj0jog0qz1lada1&st=qlh708zo&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/v6hyz7qdhj9kv9y44y3lb/WhatsApp-Image-2025-12-20-at-07.20.32.jpeg?rlkey=nrntdgq7869sjvjxxolv35bq3&st=cqyumpzh&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/bh4qp1ccv1woddiu3111s/WhatsApp-Image-2025-12-20-at-07.20.33-2.jpeg?rlkey=70xtbvkrh8car2tszcxwx3v11&st=ekdb5zlc&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/u3zjtyfyrc3odsgmgly4s/WhatsApp-Image-2025-12-20-at-07.20.33-3.jpeg?rlkey=wdtjmwaf5i8g9rrhd6qcit2dp&st=zz3xxqwj&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/o3jyjgh617g5iak4nzskg/WhatsApp-Image-2025-12-20-at-07.20.33-4.jpeg?rlkey=utakrs9winpt2qup6ddjfbhj3&st=ed11de3p&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/goy2uxfxgaaqt5qx9cnmm/WhatsApp-Image-2025-12-20-at-07.20.33-5.jpeg?rlkey=j5lqjk7gtv8v48xq65c5br1rj&st=h1060c3a&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/rufz99efwge9j8m3skkc9/WhatsApp-Image-2025-12-20-at-07.20.33-7.jpeg?rlkey=kvezis5ei79gss3xqmbojcskg&st=0pm6pb64&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/rufz99efwge9j8m3skkc9/WhatsApp-Image-2025-12-20-at-07.20.33-7.jpeg?rlkey=kvezis5ei79gss3xqmbojcskg&st=zjtd57ha&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/438l2e87crcy57uw4n1lo/WhatsApp-Image-2025-12-20-at-07.20.33-8.jpeg?rlkey=nhb2gl3akncs5dktl1m3lzhdy&st=18b0lz21&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/ei1bvec0e77l7ezxok0zb/WhatsApp-Image-2025-12-20-at-07.20.33-9.jpeg?rlkey=6st5snrdlvxztd88dueomtbhc&st=8qe49cb6&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/9qs6blpjwzd98mi27ot1w/WhatsApp-Image-2025-12-20-at-07.20.33-10.jpeg?rlkey=vrvmtvp7rvzs6ohcz0aahnb1e&st=49rpb922&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/zfwe5xrpx38ltxy6wdltl/WhatsApp-Image-2025-12-20-at-07.20.33.jpeg?rlkey=a86b0y73z4c30u9cbyi3395iw&st=e39fscu9&dl=0)
