---
title: جلسه 21 - ساخت نقشه آنلاین
---
در مرحله ی سوم و چهارم تحلیل مطلوبیت وزن دهی و روی هم اندازی است. دستوری داره جی آی اس که هر دو مرحله رو با هم انجام میده: weighted overlay تو پنجره ای که باز میشه در بخش scale رو معرفی می کنم (همون خط کشی که داده بودیم برای reclassify(
بعد داخل همون پنجره کنار rasters یک فلش رو به پایین داره اونو می زنیم و دو تا لایه ی reclassify موت رو انتخاب می کنیم (یک دانه راجع به فاصله از گسل و دیگری شیب است). بعد ازمون میپرسه که کدوم معیار برامون مهم تره. باید تو قسمتی که 
درصد-مساوی داره درصد مهم بودن هر کدوم رو مشخص می کنیم که جمعشون باید 100 بشه. فاصله از گسل رو میذاریم 70 و شیب رو میذاریم 30. اوکی را می زنیم و سپس ران![1](https://github.com/user-attachments/assets/87deb933-171f-4925-88b7-c53149f7afc3)
.
لایه ی خروجی را راست کلیک می کنیم و سپس add to display  مدل را سیو می کنیم.![2](https://github.com/user-attachments/assets/c3962458-107c-4250-ba01-9c4729beb39b![3](https://github.com/user-attachments/assets/6f41204c-f262-489d-aea1-3c277311d4f3)
)
 حال سوال اینجاست مطلوب ترین محله برای ساخت مدرسه کجاست؟
حال لایه ی کاربری را اضافه می نیم و جدول آن را باز می کنیم. ما فقط پارسل های بایر را نیاز داریم پس از select by attribute  بایر ها را انتخاب می کنیم.![4](https://github.com/user-attachments/assets/441d5985-68ec-493f-be87-7f1a15356b23![5](https://github.com/user-attachments/assets/3b3a9996-4697-44ba-98a3-b0c19bde3019)
)
 حال روی لایه ی راست کلیک می کنیم و سپس data را می زنیم و export را می زنیم و export features را می زنیم تا اکسپورت شود و زمین های بایر انتخاب می شود![6](https://github.com/user-attachments/assets/7eacfcfc-4a30-4deb-9d1d-3c09b9e53bbf)
. 
ازzonal statistics as table  در بخش input همان export features باشد و سپس input value raster را خروجی تحلیل مطلوبیت می گذاریم. در بخش zone field باید منحصر به فرد باید انتخاب کنه هر پارسل رو برای همین می گذاریم object id 
سپس statistics type رو all می گذاریم. و سپس run را می گذاریم![7](https://github.com/user-attachments/assets/3d2ab4d8-0f9e-4a08-a4e2-ad7cd2abe530)
. حالا در contents یک جدول تشکیل می شود. حالا باید تعداد پارسل ها در zonal با اون selection باید یکی بشه در خالت عادی اما ما چون cell size رو 100 در 100 گرفته بودیم بعضیاشون انقدر کوچیکن که حساب نشدن پس بهتر بود که cell size  رو کوچیک بذاریم مثلا 10 در 10.
می خواهیم اطلاعات جدول zonal رو به جدول بایر ها join کنیم.![8](https://github.com/user-attachments/assets/31b56fb3-5e57-4f76-8e69-8164841e8862)
 حالا input را روی object id می گذاریم و join field را می گذاریم object id1 و تیک leep all input records را بر میداریم.
حالا فیلد min رو بر اساس بزرگ به کوچک مرتب می کنیم![9](https://github.com/user-attachments/assets/57a0f77e-d964-4acc-ae65-fc7ec3dcadad)
 و بر اساس فیلد mean سیمبولوژی را تنظیم می کنیم![10](https://github.com/user-attachments/assets/29ad3202-3784-49f1-916c-8482af209258)
.

