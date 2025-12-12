---
title: جلسه 18 - ساخت نقشه آنلاین
---
لایه ی elevation میشه همون ارتفاع از سطح دریا
الویشن لایه ی رستریش ارتفاعیه کد های h و p برای داه های ارتفاعی هستند h میشه نقاط ارتفاعی , p میشه خطوط تراز یا هم تراز 
حالا همون فایل جلسه ی قبل رو باز می کنیم و راست کلیک می کنیم داخل لایه ی idw  و سپس پراپرتیز رو می زنیم و در اونجا بخش source![11](https://github.com/user-attachments/assets/14401c71-1fdc-44b8-918f-c4bec4107718)
 رو انتخاب می نیم و سپس spatial reference را انتخاب می کنیم.![22](https://github.com/user-attachments/assets/5c463bca-00e8-4338-b28f-74cc212f050c)

حالا می خواهیم سیستم های مختصاتی راا به هم تبدیل کنیم. در data management tools  گزینه ی project and transformations را انتخاب می کنیم و سپس ratser بعدش project raster در پنجره ای که باز میشه روبروی output یک کره  می بینیم روی اون کره کلیک می کنیم و در پنجره ای که باز میشه اونجایی![33](https://github.com/user-attachments/assets/ecb5d145-4bc9-48ef-9a0b-e0007550103a)
 که نوشته xy coordinate عدد 32639 را وارد می کنیم سپس اول دکمه ی اینتر را در کیبورد لپتاپ می زنیم و سپس اوکی را می زنیم![44](https://github.com/user-attachments/assets/c50ae82d-0aed-46a1-b95c-8ba3da049bfa)
 . حالا در اینپوت idw را می گذاریم و سپس run را می زنیم.![55](https://github.com/user-attachments/assets/23d4f700-5380-4702-980d-4a350566027f)

حالا دوباره  در spatial analyst tools sگزینه ی surface را انتخاب می کنیم و سپس slope را می زنیم.اینپوت میشه project raster داخل اسلوپ یک فاکتور z داریم که میتونیم بذاریم همون 1 باشه. در output measurements گزینه ی percentage را انتخاب می کنیم![66](https://github.com/user-attachments/assets/5f205af7-3c84-49a6-ae59-515d3b37244f)
 و برای تحلیل جهت شیب aspect را می زنیم و در زیر مجموعه ی surface اینپوت را روی project raster را می زنیم و سپس run. 
حالا داخل بخش interval یک بار 10 را انتخاب می کنیم![77](https://github.com/user-attachments/assets/a4e2cda6-10ed-4979-a4ef-dcc8274bb599)
 و یک بار دیگر 50 را انتخاب می کن![88](https://github.com/user-attachments/assets/83bdf47f-fce2-4a93-addb-34333e69df76)
یم حالا هر دوی این ها را ران میکنیم و روی لایه ای که تشکیل شده هر کدوم راست کلیک می کنیم و symbology را باز می کنیم سپس روی خط کلیک کرده تا پنجره اش برای ما باز شود و width را می زنیم .
حالا اینتروال 10 را width عش رو 0.2 می گذاریم و 50 را 2 می گذاریم.![999](https://github.com/user-attachments/assets/b6f67dfa-787b-4e23-93eb-df4a5294c198)

حالا در بخش اخر در surface گزینه ی hillshade را می زنیم. در بخش اخر azimuth را 100 می گذاریم و در altitude یک عدد کوچک می گذاریم.![111](https://github.com/user-attachments/assets/befc5a78-2c6c-4906-8ef1-adf99995485e)
