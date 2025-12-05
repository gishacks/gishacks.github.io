---
title: جلسه 17 - تحلیل مطلوبیت
موضوع: مکانیابی بیمارستان های جدید. مرحله ی 1:معیار ها/ -فاصله -فاصله تا پارک -فاصله تا بیمارستان -فاصله تا گسل -فاصله در شهرسازی مهم است. -سطح -خط تراز 1800(همه ی نقاط از سطح دریا) -شیب -جهت شیب -تراکم -جمعیتی - ساختمانی -تحلیل سطح -لایه ی elevation 
-DEM -توپوگرافی -پهنه ارتفاع بندی
داخل جی آی اس در geoprocessing روی مدل راست کلیک می کنیم و گزینه ی edit را می زنیم. داخل کاتالوگ گزینه ی project را انتخاب می کنیم و مدل را می زنیم.![1](https://github.com/user-attachments/assets/52a4e319-4c62-4ab3-9476-073c9fee2ca7)
(باید اون فایلی که در گروه فرستاده شد تهران 25000 را وارد پروژه کنیم)![5](https://github.com/user-attachments/assets/1b4ed72c-2ef9-457b-8ab4-a8752d7505b7)

حال می خواهیم ارتفاع از سطح دریا را نشان دهیم.
در مرحله ی اول سایت opentopography را باز می کنیم![2](https://github.com/user-attachments/assets/b3604d8d-bd1a-4432-ab14-1648e1ba1772)
 و سپس data را انتخاب کنیم و find data map را م زنیم (فیلترشکن روشن) حالا در نقشه ای که به ما نشان می دهد تهران را پیدا می کنیم و سپس در سمت چپ بالای نقشه select a region را می زنیم![3](https://github.com/user-attachments/assets/68368257-4612-44c2-8369-7673d3bc381a)
 و سپس یک مستطیل دور شهر تهران  می کشیم و آن را انتخاب می کنیم سپس ایمیل خود را می دهیم و درخواست نقشهرا می دهیم (srtm15![4](https://github.com/user-attachments/assets/56a63898-fe4e-4f0f-a6e9-4e73a1d41f5c)
) سپس این فایل را در جی آی اس باز می کنیم. در این مرحله روی هر نقطه ای از نقشه کلیک کنیک ارتفاعش را از سطح دریا به ما نشان می دهد![6](https://github.com/user-attachments/assets/b787a4fe-ddbc-4ebf-95d8-a348107eea17![7](https://github.com/user-attachments/assets/34d3967c-6fcc-4353-8ee3-8ec75557202e)
)
. حالا برای اینکه واضح تر این ارتفاعات و اختلافات را بهتر نشان دهیم گزینه ی symbology را انتخاب می کنیم و shaded relief را می زنیم.![8](https://github.com/user-attachments/assets/166ffbd5-15ea-4362-8b20-7aa5f1db88b0)
 در تب raster layer گزینه ی resampling layer ر می زنیم![9](https://github.com/user-attachments/assets/7b82a3eb-8530-4cdd-80d6-8ed33f75957c)
 و سپس برای واضح تر نشان دادن نقاط گزینه ی cubic را انتخاب می کنیم.
حال یک base map را باز می کنیم و در نوار سمت راست یا همان کاتالوگ در فایل تهران 25000 چهار تا فایل spot height 1+2+3+4 را وارد می کنیم ![10](https://github.com/user-attachments/assets/26396df3-9b68-4b5b-b4f9-8c16093f84a2)
و در مرحله ی بعد فقط لایه ی چهارم را روشن می گذاریم و بقیه را خاموش نگه می داریم.
حالا سوال ایثن است که چطور یک لایه ی raster ازش بسازیم؟ بهش میگیم میان یابی. می خواهیم ارزش بین نقاط رو بدست بیاریم (interpolate) حالا در بخش toolboxes گزینه ی spatial analyst tools را انتخاب میکنیم و سپس interpolation را می زنیم. حالا بین این ابزار ها که دیده می شود همه برای میان یابی اند اما هر کدام فرمول جدایی دارند اگه نقطه ها به هم نزدیکند مهم نیست برای همین ما از idw استفاده می کنیم.
فرمول idw = وزن نقاط/فاصله سلول یا نقاط پیرامون
ابزار idw را که انتخاب کردیم در پنجره ی وارد شده input را روی spot height 4 می گذاریم ![11](https://github.com/user-attachments/assets/11a2d041-9b7f-458d-bccc-bea748003bed![12](https://github.com/user-attachments/assets/7f68e72c-e780-4785-89f9-ac0d6e16275d)
)
و سپس run را می زنیم.حالا یک لایه ی elevation تهیه می شود به نام idw.![13](https://github.com/user-attachments/assets/f34ec9e0-8c62-44a8-88d7-86daefafafb0)
