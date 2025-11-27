---
title: جلسه 16 
---
 
- هر **تحلیل مطلوبیتی** شامل مجموعه‌ای از **معیارها**ست.


---

## کار با Model Builder در GIS 
`Analysis > Model Builder`

### اضافه کردن ابزار Buffer  
- ابزار **Buffer** را می‌کشیم و در Model Builder رها می‌کنیم.  
- روی آن دوبار کلیک می‌کنیم.
- در قسمت **Input:** لایه‌ی `gosal` را می‌گذاریم.   
  - مستطیل = دستور  
  - بیضی = ورودی/خروجی  
- زمانی که تنظیمات درست باشد، ابزار رنگ می‌گیرد.  
- اگر رنگ نگرفت:  
  - لایه‌ی `gosal` را در نقشه اصلی باز می‌کنیم و دوباره امتحان می‌کنیم.  

### اضافه کردن ابزار Identity  
- ابزار **Identity** را اضافه می‌کنیم (مثل Buffer).  
  - **Identity feature:** `mahallat`  
  - **Input:** `gosal`
- از تب **Diagram > Auto Layout** چیدمان را مرتب می‌کنیم.   
- برای اجرا:  
  - روی مستطیل هر ابزار **Right Click > Run**  
- نشانه‌ی اجرا شدن: روی ابزار **سایه** می‌افتد.  
- ترتیب اجرا:  
  1. Buffer  
  2. Identity  
- در آخر روی خروجی **Add to Display** می‌زنیم تا به نقشه اضافه شود.

### اهمیت Model Builder   
چون در پروژه‌های پیچیده ممکن است فراموش کنیم:  
- مثلاً ۱۰۰ مرحله بعد یادمان نماند که ورودی Buffer چه بوده.  
- Model Builder تمام مراحل را ثبت می‌کند.

### ذخیره‌سازی  
- بعد از ذخیره، در پنل Toolboxes  
  - یک **Toolbox** به نام پروژه ساخته می‌شود  
  - مدل داخل همان Toolbox قرار می‌گیرد.

---

## مثال: Spatial Join برای بیمارستان‌ها

### ساخت مدل جدید  
- لایه‌ها:  
  - Input: `bimarestan`  
  - Target: `mahallat`  

### مراحل:

#### ۱) افزودن فیلد جدید  
`Geoprocessing > Add Field`  
- Input: `mahallat`  
- Field name: `hospitals`

#### ۲) Spatial Join  
- Target: `mahallat_2`  
- Run

#### ۳) Calculate Field  
- Input: `mahallat_spatial`  
- Field: `hospital`  
- Value: `Join Count`  
- Run

#### ۴) Remove Join  
- Layer name: `mahallat_spa_2`

- جدول `attribute` را باز می‌کنیم.
- مقدار فیلد `hospital` قابل مشاهده است.
- باید اکسپورت می‌کردیم چون در `spatial join` لایه جدید ساخته می‌شود.
- جدول `attribute` برای `mahallat spatial join` را باز می‌کنیم.
