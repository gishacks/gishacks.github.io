# جلسه ۹: تحلیل فضایی و ModelBuilder

## ۱. انواع انتخاب (Selection) در تب Map
در تب **Map**، بخش **Select** سه نوع انتخاب اصلی دارد:  
- **Select**: انتخاب دستی محدوده با اشکال هندسی مختلف  
- **Select By Attributes**: انتخاب بر اساس ویژگی‌های توصیفی  
- **Select By Location**: انتخاب بر اساس موقعیت مکانی  

![select by attributes](https://i.postimg.cc/tC105DfV/Screenshot-370.png)

## ۲. Select By Attributes – جزئیات کامل

### Selection Type
![selection type](https://i.postimg.cc/bJK5Ff4r/Screenshot-371.png)  
اگر A = انتخاب قبلی و B = انتخاب جدید:  
- **New Selection**: B (انتخاب قبلی پاک می‌شود)  
- **Add to**: A ∪ B  
- **Remove**: A − B  
- **Select Subset**: A ∩ B  

### نوشتن Query
**عددی (Shape_Area):**  
![shape_Area](https://i.postimg.cc/XY7sLvXZ/Screenshot-372.png)  
**متنی (Label):**  
![label](https://i.postimg.cc/tTt68hMD/Screenshot-373.png)  

**ترکیب شرط‌ها:** **Add Clause** / **AND** (اشتراک) / **OR** (اجتماع)

## ۳. تمرین: محاسبه تراکم جمعیت و انتخاب بالای میانگین
**مراحل:**  
1. **Add Field**: نام `Density` / نوع **Float** / ذخیره  
2. **Calculate Field**: `population / (shape_area / 10000)`  
3. **Select By Attributes**: `Density` > **is above average**  

**نتیجه:**  
![نتیجه تراکم](https://i.postimg.cc/K8SZ3dzG/Screenshot-374.png)

## ۴. تمرین: گزارش کاربری‌های کمتر از ۲۰۰ متر
**Select By Attributes**: کاربری + Shape_Area < 200 / راست‌کلیک **Label** > **Summarize**

## ۵. دائمی کردن انتخاب‌ها
**Definition Query**: راست‌کلیک لایه > **Properties** > **Definition Query**  
**بهترین روش:** فیلد جدید + **Calculate Field** (1/2/...) به جای Export

## ۶. انواع داده‌ها (Field Types)
| نوع داده | توضیح |
|-----------|--------|
| **Integer** | عدد صحیح (120) |
| **Float/Double** | اعشاری (15.75) |
| **String/Text** | متنی ("مسکونی") |

**Null vs 0**: Null = محاسبه نشده / 0 = صفر قطعی

## ۷. ModelBuilder

### مراحل ساخت مدل:
1. **Conversion Tool** + تصویر Input  
2. **Topo to Raster** (Point-Elevation / grid-code)  
3. **Project Raster** (32639)  
4. **Slope** (Percent)  
5. **Aspect**  
6. **Contour** (Interval: 10)  
7. **Hillshade** (Azimuth/Altitude)  
8. **Run All** + **Add to Display** + پاک‌سازی مسیرهای پیش‌فرض

### تبدیل به پارامتر:
**Catalog** > مدل > **Edit** > **Create Variable** > **Make Parameter** (فقط خروجی‌های نهایی)

![pic1](https://github.com/user-attachments/assets/b8b91e55-9c12-4543-9eb9-779f01ad7e01)
![pic2](https://github.com/user-attachments/assets/fad03dbb-6e54-481d-9b52-a92d33b766c5)
![pic3](https://github.com/user-attachments/assets/e03e3821-f740-46f0-b6a9-cbfecfa2d98b)

## ۸. تحلیل فاصله (Proximity vs Accessibility)

**Proximity**: فاصله هندسی مستقیم  
**Accessibility**: مبتنی بر شبکه راه‌ها  

**ابزار:** **Spatial Analyst** > **Distance** > **Euclidean Distance**

### تنظیمات کلیدی:
**Environment Settings:**  
- **Processing Extent**: لایه مناطق شهرداری  
- **Cell Size**: 100 متر (دقت بیشتر = سلول کوچک‌تر)

**Input**: لایه گسل  
**خروجی**: رستر فاصله تا نزدیک‌ترین گسل

![pic4](https://github.com/user-attachments/assets/080203de-68dd-4958-8d41-649eb6981793)
![pic5](https://github.com/user-attachments/assets/1716350c-36db-4655-b5a6-2fcb88b6a43f)

## ۹. ساخت فیلد تراکم
**Add Field**: `تراکم` / **Double**  
**Calculate**: `population / shape_area / 10000`  

![pic6](https://github.com/user-attachments/assets/63b7c106-e48a-4a90-bb5c-3a948f22de6a)
![pic7](https://github.com/user-attachments/assets/2e178c52-c78a-4931-a46e-4fbe94bfd850)

## ۱۰. Summarize پیشرفته
**Label** > **Summarize** / **Maximum** / **OBJECTID** > **Count**

![pic10](https://github.com/user-attachments/assets/f4a80c63-e0a4-4de0-abbd-a09f6968cbbc)

## ۱۱. Definition Query عملی
راست‌کلیک لایه > **Properties** > **Definition Query** > `Shape_Area < 200`

![pic11](https://github.com/user-attachments/assets/4c82565f-01ca-4e98-b2b7-e6a8ad851185)

## ۱۲. Symbology رستر فاصله
- **Stretch**: نمایش پیوسته  
- **Classify**: ۵ دسته فاصله (قرمز=نزدیک، سبز=دور)

![pic8](https://github.com/user-attachments/assets/70eb9a95-513b-41ee-9a46-22318c116672)
![pic9](https://github.com/user-attachments/assets/bedfefcf-bb65-4a4e-be8b-2ff0bdd68bb7)
