---
title: جلسه ۱۱ - جمع‌آوری و ساخت لایه‌ها GIS
---
در این جلسه می خواهیم با arc tool box کار انجام دهیم. اول فایل های گسل، بیمارستان و کاربری طرح جامع را باز می کنیم.![pic1](https://github.com/user-attachments/assets/5dec7c77-51c8-44fb-8cab-9bbea207b1b9)
 سپس در تب analysis  گزینه ی tools را می زنیم تا پنجره ی سمت راست برای ما باز شود. در این پنجره قسمت toolboxes گزینه ی analysis tools را باز می کنیم و buffer را انتخب می کنیم سپس در input بیمارستان می زنیم و فاصله را 150  انتخاب کرده و گزینه ی run را انتخاب می کنیم.![pic2](https://github.com/user-attachments/assets/21802439-3abf-427e-918c-44d69cc3c892)
(حتما حواسمان باشد گزینه ی dissolve type باید روی no dissolve باشد). گسل را جدولش را باز می کنیم اینجا می خواهیم یک کاری انجام دهیم. آنهایی که در type 3 خورده اند باید روی حریمشان 150 نوشته شود. آنهایی که 6 خورده اند باید 300 باشد و بقیه ی اعداد روی 50 تنظیم شوند. پس با add field شروع کرده و یک فیلد جدید به نام buffer و data type short یا big integer می سازیم سپس آن را سیو کرده و پنجره را می بندیم.![pic 3](https://github.com/user-attachments/assets/ddae240b-dc4e-48be-b625-093c22730970)
 حال  در select by attribute بخش where ، type را انتخاب می کنیم و نوار کناری is equal to 3 را انتخاب کرده![pic4](https://github.com/user-attachments/assets/2025167c-1a7b-4084-8d42-afbe444e7194)
 اوکی را می زنیم و calculate field را باز می کنیم در این بخش عدد 150 را تایپ کرده و پنجره را می بندیم![pic5](https://github.com/user-attachments/assets/545aff8a-836b-448c-a395-5f0785082cd7)
 حال اگر در جدول دقت کنیم تمام گزینه هایی که type 3 دارند بافر آنها عدد 150 خورده است. این مرحله را برای بقیه ی اعداد نیز تکرار می کنیم. باری دیگر select by location را انتخاب کرده و selection type را روی switch to the current تنظیم می کنیم![pic6](https://github.com/user-attachments/assets/cd3a348a-13c1-4de2-8d82-736fbc87f5d5)
 و اوکی را می زنیم.  دوباره پنجره ی buffer را باز می کنیم و دوباره اینپوت را روی گیل می گذاریم اما این بار به جای linear فیلد را انتخاب میکنیم. میگه تو چه فیلدی؟ فیلد را بافر می گذاریم و سپس dissolve type را dissolve features using the listed fields unique.. می گذاریم و ران را می زنیم![pic7](https://github.com/user-attachments/assets/6c9a5121-19fa-4386-96f8-3451e062f7e1)
 .حال در نوار سمت راست گزینه ی multiple ring buffer را انتخاب می کنیم. و سپس در دیستنس سه عدد 100و 200 و 500 را وارد می کنیم![pic8](https://github.com/user-attachments/assets/40b0aaba-759f-4b0c-9590-cd671ec6b90c)
 (می خواهیم قطعات در فاصله ی 200 تا 500 متری را انتخاب کنیم.) حالا لایه ی multiple ring را در نوار سمت چپ پیدا کرده و جدول آن را باز می کنیم. سومین ردیف را انتخاب می کنیم.![pic9](https://github.com/user-attachments/assets/63cc30df-8f5d-4a7c-a11d-d3b50bf6a187)
 حالا select by attribute را باز کرده input را روی کاربری تنظیم کرده relationship را intersect می گذاریم سلکتینگ فیچر را مولتیپل رینگ می گذاری![pic 11](https://github.com/user-attachments/assets/4064ea42-49b9-45e9-b31b-c896c4b765c1)
![pic 12](https://github.com/user-attachments/assets/47d2c7c5-1ddd-4cba-9a43-296ff819229a)
م
