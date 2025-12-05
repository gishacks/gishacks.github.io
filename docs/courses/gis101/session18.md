---
title: جلسه 18
---
# استخراج، نمایش و میان‌یابی ارتفاع از سطح دریا در ArcGIS
سایت `open topography` را سرچ می‌کنیم.
Opentopography > Data > Find Data Map  
VPN روشن باشد  
تهران را پیدا می‌کنیم.  
بالا سمت چپ > Select a Region  
انتخاب محدوده با موس  
پایین صفحه ثبت درخواست:

DEM > SRTM 15  
Get SRTM 15  
فرمت فایل: GeoTIFF  
وارد کردن Email  
More Options > انتخاب عنوان پروژه  
Submit  

پس از آماده شدن فایل آن را دانلود می‌کنیم.  
Add Data در GIS  

برای مشاهده ارتفاع:
کلیک روی هر نقطه → نمایش ارتفاع از سطح دریا  
- روی لایه رایت‌کلیک کرده و سیمبولوژی را انتخاب می‌کنیم.
Symbology > Shaded Relief  

بهبود کیفیت:
Raster Layer > Resampling Type  
انتخاب Cubic  

- نقشه پایه اضافه می‌کنیم.

دقت این مدل محدود است و کل محدوده یکپارچه در نظر گرفته می‌شود.

استفاده از داده دقیق نقاط ارتفاعی:
Add Data> Tehran 25000 > pnt > spot-height-4  
همان spot-height-4 کافی است  
دقت بسیار بالاتر از SRTM  

میان‌یابی:
Geoprocessing  
Spatial Analyst Tools > Interpolation > IDW  
Input: spot-height-4  
Run   

روش جایگزین:
تبدیل رستر به نقطه:
Conversion Tools > From Raster > Raster to Point  
Input Raster: فایل SRTM  
Field: Value  
Run  
- تعداد زیادی نقطه ایجاد می‌شود.

ترکیب لایه‌ها:
Union:
Analysis Tools > Overlay > Union  

Merge:
Data Management Tools > General > Merge  
شرط: لایه‌ها باید هم‌جنس باشند (مثلا نقطه با پولیگون نمی‌شود.)  
باید فیلد مشترک داشته باشیم (مثلا height)  
