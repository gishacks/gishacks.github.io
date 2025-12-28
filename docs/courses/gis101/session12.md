---
title: جلسه ۱۲ - ساخت نقشه آنلاین
--- 
> چه جمعیتی در حریم گسل قرار دارد؟

---

## ایجاد حریم (Buffer)
مثل جلسه قبل، برای **گسل** یک **Buffer با فاصله‌ی ۱۵۰ متر** ایجاد می‌کنیم.
## بررسی زونینگ
- از قسمت طرح توسعه، زونینگ طرح تفصیلی را باز می‌کنیم.
- برای داشتن لایه زونینگ بدون گسل از ابزار **Erase** استفاده می‌کنیم. 
**تنظیمات ابزار Erase:**
- **Input Feature:** zoning  
- **Erase Feature:** gosal_buffer  
- تیک بافر و زونینگ را از قسمت **contents** برمیداریم. 
---

## بررسی پهنه‌های در حریم گسل 
> از چه پهنه‌هایی و چه سطحی از پهنه‌ها در حریم گسل قرار دارند؟

باید اشتراک (Intersection) بین **زونینگ اصلی** و **بافر گسل** را بگیریم.
- در ابزار `Erase` ترتیب نوشتن اهمیت داشت اما در `Intersect` فرقی ندارد چون اشتراک می‌گیریم.
### ابزار Intersect
چون هدف، یافتن اشتراک است:
- یکی از لایه‌ها: **گسل بافر (gosal_buffer)**  
- دیگری: **زونینگ اصلی (zoning)**  

---

## گزارش‌گیری از نتایج
1. روی **جدول لایه‌ی Intersect** راست‌کلیک می‌کنیم.  
2. گزینه‌ی **Summarize** را انتخاب می‌کنیم.  
3. تنظیمات:
   - **Field 1:** label  
   - **Field 2:** shape_area → Sum  


---

## ابزار Identity 
- برخلاف Erase، هیچ چیزی حذف نمی‌شود، فقط مرزها روی هم بریده می‌شوند.
- - **Input Feature:** zoning  
- **Identity Feature:** gosal_buffer  

می‌خوایم بفهمیم:
> چند درصد از مساحت محلات در محدوده‌ی گسل قرار دارد؟

### مراحل:
1. لایه‌ی **محلات (mahalat)** را اضافه می‌کنیم.  
2. ابزار **Identity** را اجرا می‌کنیم:
   - **Input Feature:** mahalat  
   - **Identity Feature:** gosal_buffer  
3. جدول‌های **محلات Identity** و **گسل بافر** را باز می‌کنیم.
   - آن‍هایی که در بافر برایشان `Distance` صفر نیست، واقع در گسلند.
### رنگ گذاشتن بر اساس **Buffer Distance**
 1. روی لایه **محلات Identity** کلیک راست می‌کنیم.
 2. در قسمت **Symbology**، گزینه **Unique Value** را انتخاب می‌کنیم.
 3. در فیلد اول `Buff_Dist` قرار می‌دهیم. 
---

## خروجی گرفتن
1. در قسمت `Table` روی **Export Table** کلیک می‌کنیم.
2. در قسمت `Output` در پنجره باز شده محل ذخیره شدن را انتخاب کرده و فرمت را روی csv می‌گذاریم.
3. در اکسل از `pivot` استفاده می‌کنیم:
   - در قسمت `rows` باید `mah-id` و برای ستون‌ها `buff_dist` را قرار دهیم.
   - Values: Shape area
   - Value field setting: sum
   - Show values as= % of row total
   - اگر فرمت اعداد تکست بود باید آن را تغییر داده و به عنوان عدد معرفی کنیم.
دوباره در این جلسه با arctoolbox و proximity کار خواهیم کرد. سوال: چه جمعیتی در گسل قرار دارد؟ 
در toolbox روی buffer کلیک می کنیم و inpu![pic 3](https://github.com/user-attachments/assets/a8406c4e-f45b-401f-a306-741631861035)
t=gosal/ distance=150/run را می![حهز 1](https://github.com/user-attachments/assets/58bac02a-1c66-4da7-8609-2370[Uploadin314fa524![pic 2](https://github.com/user-attachments/assets/a775eb90-6170-4038-8742-7cfac90be386)
)
 زنیم حالا دوباره در toolbox overlay را انتخاب می کنیم. از طریق add data گسل،زونینگ کپ(طرح تفصیل) را وارد می کنیم سپس erase را باز می کنیم. input=zoning erase feature=gosal buffer/ run ![pic 4](https://github.com/user-attachments/assets/a166ce09-f505-420f-8da5-125b12584915)
 بعد تیک لایه ی زونینگ و بافر را ور میداریم![pic 5](https://github.com/user-attachments/assets/3954e6a0-cba0-4018-82d5-dd3102524984)
.در toolbox روی intersect کلیک می کنیم و یکی را روی gosal buffer می گذاریم و دیگری را روی زونینگ می گذاریم.![pic 6](https://github.com/user-attachments/assets/7268c7ac-2857-4f00-9f0c-fc81a059df07)
 حال جدول intersect را باز می کنیم و روی label راست کلیک می کنیم و گزینه ی summarize را انتخاب می کنیمو field1=label/field2= shape area-sum را می زنیم ![pic 7](https://github.com/user-attachments/assets/2d8ce847-a547-4fab-b8e3-0cb853453323)
و پنجره را می بندیم. حال identity را باز می کنیم (تمام این ها در بخش toolbox ها هستند) دوباره input=zoning/output=gosal buffer برای فهمیدن identity می خواهیم بفهمیم درصد مساحت محلات توی گسل است. از فولدر مدیریت فضا محلات را اضافه می کنیم ![pic9](https://github.com/user-attachments/assets/78354034-6802-4314-9b03-8a691a86e604![pic 10](https://github.com/user-attachments/assets/4f0557dc-f14a-48dd-ada5-8cfa8e630fe1)
)
و دوباره در toolbox گزینه ی identity را انتخب می کنیم. input=mahallat/identity=gosal/run را می زنیم.![pic11](https://github.com/user-attachments/assets/98f90840-3e8b-40e0-843a-6bbbf982a6d6)
 حالا سه جدول mahallat identity/gosal/mahallat را باز می کنیم ![pic12](https://github.com/user-attachments/assets/6b5324ab-780a-43cf-9eb4-e0e0838d9e95)
و در جدول mahallat identity buffer distance اونهایی که 0 نیست یعنی روی گسل است. روی محلات identity راست کلیک می کنیم و سیمبولوژی را باز می کنیم و تغییر رنگ می دهیم( unique values)![pic 13](https://github.com/user-attachments/assets/c49b27e3-4ceb-4129-93ae-b0f98e9413c4)
 از ستون buffer distanc اکسپورت می گیریم و جدول را با فرمت csv سیو می کنیم![pic14](https://github.com/user-attachments/assets/51dd8581-a4f3-4bcb-90c8-7fed8af138ae)
 و سپس آن را در اکسل باز می کنیم. حال در اکسل روی pivot table کلیک می کنیم. mah id را در rows وارد می کنیم. buff distance را در columns وارد می کنیم و در values sum of shape area را وارد می کنیم حال در field settings پنجره ای باز می شود در تب اول sum را رناختب می کنیم و در تب دوم shoe values as percent of total rows انتخاب کرده و اوکی را می زنیم اینگونه یم جدول با اطلاات مفید و خلاصه از جمعیت برای ما ایجاد می شود![pic 16](https://github.com/user-attachments/assets/2edbab40-c16a-490f-a199-34630107ffad)
.
