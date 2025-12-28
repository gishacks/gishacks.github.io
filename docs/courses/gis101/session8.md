#  جلسه ۸: Join و گزارش‌گیری پیشرفته

## ۱. Join – اضافه کردن جداول
این جلسه درباره اضافه کردن اطلاعات است. دو حالت برای اجرای Join وجود دارد:  
- بر اساس فضای انتخابی و موقعیت (Location)  
- بر اساس اطلاعات و فیلدهای مشترک

**مثال عملی:**  
از جدول حریم گسل خروجی بگیریم و به CSV ذخیره / در Excel درج / **Insert** > **Pivot** / خلاصه‌سازی جدول / خروجی بر اساس ستون‌های مورد نیاز / قرار دادن در صفحه دیگر.

## ۲. تحویل درصد در Excel Pivot
بر روی ردیف دیگر اطلاعات اضافه / فرمت **SUM** / **Layout and Print** > درصد از کل / اعمال تغییرات / جدول به صورت درصدی.

## ۳. پیاده‌سازی درصد در GIS
بدون تغییر اعداد، جدول را در GIS اضافه / ستون جدید (Float) / **Calculate** برای درصد / روی **جدول ادغام شده محلات + حریم گسل** کلیک / **Join** بر اساس ID محلات / **Symbology** > **Unique Values** / طیف رنگی (قرمز-زرد) برای نمایش درصد کاربری‌های روی/در حریم گسل و میزان خطر برای ساکنان.

---

## ۴. ابزار Select By Attribute

### معرفی
انتخاب قطعات و داده‌های خاص براساس داده‌های جدول.

### Selection Type
اگر A = دسته ۱ و B = دسته ۲:  
- **New selection**: A  
- **Add to current selection**: A ∪ B  
- **Remove from current selection**: A − B  
- **Select subset from current selection**: A ∩ B

### نحوه انتخاب
**Where**: فیلد مورد نظر / **وسط**: عملیات (is equal to, is greater than, contains text...) / **راست**: مقدار / **Apply** و **OK**.

برای ترکیب چند شرط: **Add Clause** / **AND** (اشتراک) / **OR** (اجتماع).

### مثال
کاربری‌های مسکونی زیر ۲۰۰ متر:  
- LandUse is equal to 'Residential' **AND** Shape_Area is less than 200

### نمایش داده‌های منتخب
**روش ۱:** خروجی گرفتن از لایه.  
**روش ۲:** **Definition Query** – راست‌کلیک لایه / **Properties** / **Definition Query** / تعریف شرط انتخاب / فعال/غیرفعال با تیک.

---

## ۵. ابزار Select By Location

انتخاب نقاط/عوارض براساس موقعیت نسبت به عنصر دیگر.

**Relationship گزینه‌ها:**  
- **Intersect**: تقاطع  
- **Contains**: کاملاً داخل محدوده  
- **Within**: کاملاً داخل محدوده  
- **Have their center in**: مرکز داخل محدوده

---

## ۶. پروژه عملی: گسل‌های منطقه ۱ تهران

**هدف:** گزارش و نقشه نمایانگر کاربری‌های روی/در فاصله ۱۵۰ متری گسل.

### دو دسته:
**A:** قطعات دقیقاً روی گسل  
- Select By Location / Intersect / Distance: 0

**B:** قطعات در فاصله ۱۵۰ متری (نه روی گسل)  
- Select By Location / Intersect / Distance: 150  
- سپس: Select By Location / Intersect / Distance: 0 / Selection Type: **Remove from current selection**

### مراحل کدگذاری:
- فیلد جدید: **gosal**  
- برای A: **Calculate Field** = 1  
- برای B: **Calculate Field** = 2  
- **Symbology** > **Unique Values** / رنگ اختصاص برای A و B

### خروجی و گزارش:
خروجی جدول به CSV / در Excel باز / **Pivot Table** / تعداد و نوع قطعات در دسته A/B / گزارش کامل.

---

## ۷. گزارش (Report)

**مسیر:** **Insert** > **New Report**

**صفحه ۱:** انتخاب تمپلیت:  
- **Attribute**: گزارش توصیفی  
- **By Grouping**: دسته‌بندی  
- **Basic Summary**: خلاصه  
- **Page Per Feature**: هر عارضه در صفحه جداگانه

**صفحه ۲:** انتخاب جدول.  
**صفحه ۳:** انتخاب فیلدهای گزارش.  
**Finish** و سفارشی‌سازی / **Preview** برای مشاهده نهایی.

---

## ۸. Presentation

**مسیر:** **Insert** > **New Presentation**

### ساخت اسلاید:
![pic1](https://github.com/user-attachments/assets/8b6ddff4-7a5b-4dfd-855d-91e688f9fd01)

در **نوار چپ** گزینه **Insert Page** / اسلاید جدید از نقشه.

### زوم و اسلاید دوم:
پنل نقشه / زوم روی محله / برگشت به **Presentation** / اسلاید دوم منعکس زوم شده.

![pic2](https://github.com/user-attachments/assets/a302bc06-bc4e-4d7a-b03c-5ca204da5599)

### اضافه کردن Report:
**Insert** > **New Report** (روی لایه) / **Data Source** انتخاب / **Next** > **Sorting & Summary Stats** / **Next** > **Grouping Per Feature** (هر عارضه در صفحه جداگانه).

![pic3](https://github.com/user-attachments/assets/2f6a166d-c207-4efd-ab7e-6d3be5fa1ec9)
![pic4](https://github.com/user-attachments/assets/545fea7f-d04a-4cba-b832-d2ed7a26869c)
![pic5](https://github.com/user-attachments/assets/26cd49f3-61ea-4715-b34e-a946f80b9300)

### Transition:
**Transition** > **Fly** برای حرکت بین اسلاید‌ها.

![pic6](https://github.com/user-attachments/assets/a1e5289b-c8f5-43a9-9e90-d0ff488187c0)

### پخش:
**Presentation** > **Full Screen** / پخش ارائه.

![pic7](https://github.com/user-attachments/assets/9ef46319-821d-4744-a8f2-f96d0226f629)

---

## ۹. خروجی جدول به Excel

**جدول:** **Export Table** / نام فایل (دستی: `table.csv`) / ذخیره.  
باز کردن جدول نهایی در Excel.
