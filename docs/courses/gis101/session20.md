---
title: جلسه  19

---

# ساخت مدل Model Builder برای تمام فرایند جلسه قبل

## 1) **اضافه‌کردن ابزار Conversion Tool**
- تصویر Export‌شده از سایت را به عنوان **Input** قرار می‌دهیم.

---

## 2) **استفاده از ابزار Topo to Raster**
- Feature Layer: خروجی مرحله قبل  
- Type: **Point Elevation**  
- Field: **grid-code**  
- سپس **Auto Layout** برای مرتب‌سازی مدل.

---

## 3) **Project Raster**
- Input: خروجی Topo to Raster  
- Output Coordinate System: **32639**

---

## 4) **Slope**
- Input: خروجی Project Raster  
- Output Measurement: **Percent**

---

## 5) **Aspect**
- Input: خروجی مرحله ۲  
  (همان رستر ارتفاعی که سیستم مختصاتی‌اش را تغییر دادیم)

---

## 6) **Contour**
- Input: خروجی Topo to Raster  
- Contour Interval: **10**

---

## 7) **Hillshade**
- Input: خروجی Topo to Raster  

> سپس **Run** و **Add to Display** می‌کنیم.

---

#  تنظیم پارامترها در Model Builder 

###  تبدیل هر ابزار به پارامتر (برای ورودی کاربر)
- روی اولین بیضی دابل‌کلیک کرده و نوشته را پاک می‌کنیم.  
- راست‌کلیک → **Parameter**  
- مدل را سیو می‌کنیم و می‌بندیم.

### بازکردن مدل در Catalog
- Right Click → **Edit**

###  تعریف Variable برای ابزار Topo to Raster
- راست‌کلیک روی ابزار  
- **Create Variable → From Parameter → Primary Type of Input Data**

> هر ورودی که می‌خواهیم کاربر تعیین کند را باید به عنوان «پارامتر» به آن بدهیم.

###  خروجی‌های مهم را نیز پارامتر می‌کنیم:
- Output Slope  
- Output Aspect  
- Output Contour  
- (روی آن‌ها راست‌کلیک → Parameter)

###  حذف نوع‌های پارامتری اضافی
- Type را از حالت Parameter درمی‌آوریم  
- یک‌بار **Delete**  
- **Save** و دوباره Run

### ✔️ پاک‌کردن مسیر ثابت ورودی‌ها
- در Catalog → Edit  
- روی آخرین ابزارها دابل‌کلیک  
- مسیر Output را پاک می‌کنیم  
- Save

---

#  Rename کردن پارامترها

در Model Builder:
- روی Input اول → **Rename**  
- آخرین خروجی‌ها نیز:
  - **Output_Aspect**
  - **Output_Slope**
  - **Output_Contour**

###  Rename خود مدل:
- SurfaceAnalyst → Right Click → **Properties**  
- Name & Label بدون فاصله مثل:  
  **SurfaceAnalystModel**

---

#  انواع تحلیل‌ها (Surface / Distance)

## 1) **تحلیل‌های سطح (Surface)**
- شیب (Slope)  
- جهت شیب (Aspect)  
- کانتور  
- Hillshade  
- Elevation

---

# 2) **تحلیل‌های فاصله (Distance Analysis)**

### فاصله دو نوع دارد:

##  **Proximity = نزدیکی**
- مثال:  
  - گسل  
  - فرودگاه  
  - رودخانه  
  - دریا  
- بحث «فاصله مستقیم» و «حریم»

##  **Accessibility = دسترسی**
- مثال:  
  - بیمارستان  
  - مرکز محله  
  - ایستگاه مترو  
  - فرودگاه  
- *کلیدواژه*: **راه‌ها**  
  - در دسترسی از شبکه معابر استفاده می‌کنیم  
  

---



#  (فاصله اقلیدوسی)

مسیر:  
**Spatial Analyst → Distance → Legacy → Euclidean Distance**

### ورودی (Input Source):
- لایه **گسل**

---

#  تفاوت با Buffer
- در Buffer فقط می‌پرسد: *تا چه فاصله‌ای؟* → خروجی ۰/۱  
  - داخل حریم = ۱  
  - خارج = ۰

- در Euclidean Distance:
  - برای **تمام سلول‌ها** فاصله دقیق محاسبه می‌شود.  
  - مانند نقشه حرارتی فاصله.

---

#  تنظیمات مهم در Raster Distance
دو چیز همیشه باید مشخص کنیم:

### 1) **Extent (محدوده کار)**
- در Environment  
- Processing Extent →  
  گزینه سوم: **مناطق شهرداری**  
  → فقط محدوده شهر تحلیل می‌شود.

### 2) **Cell Size (اندازه سلول)**
- هرچه کوچک‌تر → دقت بیشتر  
- ولی حجم فایل بزرگ‌تر  
- پیشنهاد برای تهران: **۱۰۰ متر**

---

#  Symbology رستری
- اصولاً تغییر نمی‌دهیم  
- در Symbology → **Classify**  
- تعداد دسته‌ها و Range قابل تنظیم است.

---

# تحلیل فاصله فرودگاه
- لایه فرودگاه را اضافه می‌کنیم  
- همین Euclidean Distance را روی آن اجرا می‌کنیم

---

