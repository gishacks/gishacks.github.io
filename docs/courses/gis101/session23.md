---
title: 23 جلسه  
---
## تحلیل شبکه (Network Analysis)

### مفاهیم پایه
- اندازه‌گیری سطح پوشش خدمات نیازمند بررسی دسترسی است.
- راه‌ها یکی از موضوعات اصلی تحلیل شبکه هستند.
- شبکه‌ها می‌توانند شامل:
  - راه‌ها
  - آب
  - گاز
  - و سایر زیرساخت‌ها باشند.
- متداول‌ترین نوع تحلیل شبکه: **Route (مسیریابی)**

---

## تحلیل شبکه راه‌ها با OpenRouteService
**سایت:** `maps.openrouteservice.org`

### مراحل:
1. کلیک روی آیکون سه‌خط → **Find Place**
2. تنظیم **Mode** روی `Car`
3. انتخاب گزینه **Reach**
4. با استفاده از نقشه کنار Find Place، محدوده موردنظر را مشخص می‌کنیم.
5. در پنل سمت چپ (Parameters):
   - `Range = 5`
   - `Interval = 1`  
    یعنی هر یک کیلومتر تا شعاع ۵ کیلومتر
6. این تحلیل، تحلیل دسترسی است (فاصله بر اساس مسیرها).

### تفاوت دسترسی و نزدیکی:
- **نزدیکی (Proximity):**
  - شکل منظم
  - مستقل از معابر
- **دسترسی (Accessibility):**
  - شکل نامنظم
  - وابسته به شبکه معابر

### خروجی:
- دانلود خروجی با فرمت **GeoJSON**

---

## تحلیل شبکه در GIS

### داده‌های موردنیاز
- لایه راه‌ها (به صورت خط)
- فایل حمل‌ونقل ← شبکه معابر

---

### تبدیل GeoJSON
مسیر ابزار:
Toolbox > Conversion Tools > JSON > JSON To Feature
 *این ابزار باگ دارد، پس فعلا با آن کاری نداریم.*

---

## ساخت Network Dataset

### چرا Network Dataset؟
- GIS راه‌ها را فقط خط می‌بیند.
- برای تحلیل شبکه باید به GIS بفهمانیم این خطوط **معبر** هستند.

---

### مراحل ساخت Network Dataset

1. **پنل Catalog (سمت راست)**
2. بخش **Databases**
3. Right Click روی **Geodatabase**
4. New → **Feature Dataset**
   - نام: `Network`
   - سیستم مختصات: `EPSG:32639`
5. Run

---

### اضافه کردن شبکه معابر
1. Right Click روی `Network`
2. Import → **Feature Class**
3. Input: شبکه معابر
4. Run

---

### ساخت Network Dataset
1. Right Click روی `Network`
2. New → **Network Dataset**
3. نام: `tehran_nd`
4. Source Feature Class:
   - تیک شبکه معابر را می‌زنیم.
5. Elevation Field:
   - `None`
6. Finish  
- یک باکس دور تهران در نقشه ایجاد می‌شود.

---

## تنظیمات Network Dataset

1. Right Click روی `tehran_nd`
2. Properties
3. بخش **Travel Attributes**
4. منوی سه‌خط → New
   - Name: `drive`
   - Type: `Driving`
5. OK
6. Right Click روی `tehran_nd` → **Build**

- حالا Network Dataset آماده است.

---

## تحلیل سطح پوشش خدمات (Service Area)
- پرکاربردترین تحلیل شبکه در شهرسازی

### مراحل:
1. اضافه کردن لایه **بیمارستان‌ها**
2. تب **Analysis**
3. Workflows → **Network Analysis**
4. انتخاب **Service Area**
5. اضافه شدن تب `Service Area Layer`

---

### تنظیمات Service Area
- Import Facilities
  - Input Location: بیمارستان‌ها
- Cutoff:
  - تعیین فاصله (مثلاً مشابه OpenRouteService)
- Mode:
  - `Drive`
- جهت مبدا و مقصد:
  - مهم به دلیل معابر یک‌طرفه و دوطرفه
- Overlap:
  - `Dissolve`  
  - هم‌پوشانی‌ها در هم حل می‌شوند و خروجی تمیزتر می‌شود
- Run

---


  - برای بیمارستان‌ها بافر ۱۰۰۰ متری می‌گیریم.
- خروجی تحلیل شبکه موقتی است:
  - از لایه پلیگن خروجی می‌گیریم (Export Feature)
- برای هر پروژه Dataset جدید نمی‌سازیم، مثلا از این Dataset تهران بعدا هم استفاده می‌کنیم.
  - Network Dataset تهران برای پروژه‌های بعدی هم قابل استفاده است.
