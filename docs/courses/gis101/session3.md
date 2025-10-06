---
title: جلسه ۳ - تهیه نقشه از طریق نمایش داده‌ها ۱
---
# نشان دادن داده‌ها در GIS

+ درست کردن یک نقشه
ArcGIS / Insert / New Map / New Map
+ افزودن داده
Map / Add Data / Data / "Add Your Data" (PAYGAH ETELAAT MAKANI TEHRAN.gdb)
+ دیدن لایه‌ها
Contents / Drawing Order / Example: 107_Rah
انواع لایه‌ها: polyline, polygon, point
+ مشاهده اطلاعات هر لایه
Contents / Drawing Order / "Layer" / Right Click / Attribute Table
+ جداسازی اطلاعات لایه‌ها با نمادها
Contents / Drawing Order / "Layer" / Right Click / Symbology
انواع نمادها (Symbology): Colors, Symbol
*انتخاب نوع جداسازی:
Contents / Drawing Order / "Layer" / Right Click / Symbology / Primary Symbology
+ انواع جداسازی با رنگ: Unique Value, Graduate Color
* بعد از انتخاب نوع جداسازی باید Field هم با توجه به هدف و ستون‌های موجود در Attribute Table (جدول اطلاعات) انتخاب بشه.
Unique Value: جداسازی با ارزش‌های منحصر به فردی که در ستون‌های جدول اطلاعات لایه می‌بینیم. وقتی از این گزینه استفاده می‌کنیم که ارزش‌های ما غیرعددی و گسسته با تعداد محدود باشه. مثل: مسکونی، تجاری، نظامی
Graduate Color: ارزش‌هارو به تعداد مشخص تقسیم‌بندی می‌کنه و به هر کلاس یک رنگ در طیف رنگی اختصاص میده. مناسب برای ارزش‌های کمی مثل: 32.22357678, 34.931238, 31.1324454
* برای Graduate Color می‌تونیم Method هم انتخاب کنیم که بیشتر آنها مربوط به آمار ترم‌های بعد هستش. متدها شیوه‌ی تقسیم‌بندی ارزش‌ها و تشکیل کلاس‌ها رو مشخص می‌کنن.
متد Equal Interval (ساده‌ترین): تقسیم‌بندی محدوده ارزش‌ها به کلاس‌هایی با اندازه مساوی.
+ دیدن اطلاعات هر ستون در Attribute Table: اطلاعاتی همچون min, max, ...
Attribute Table / "Column" / Right Click (on the column header) / Statistics 
+جداسازی با نماد: Graduate Symbol (درست کردن یک طیف خطی/شکلی، مناسب برا ی لایه‌های خطی/polyline)
