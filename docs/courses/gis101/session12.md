---
title: جلسه 22 - ساخت نقشه آنلاین
---
در این جلسه با تحلیل سطح و تحلیل آماری آشنا شدیم. یا همان network analysis 
اول در سایت open route service در بخش find a place روی سه خط می زنیم تا یک پنجره برای ما باز شود در آنجا یک گزینه هست به نام find and go  ازمون میپرسه که چه mode ای میخوایم در قسمت بالا ماشین را انتخاب می کنیم. برای تحلیل سطح پوشش می خواهیم reach را تعیین بکنیم روبروی find a place یک نقشه هست روی آن کلیک می کنیم و بعد تهران را انتخاب می کنیم. در قسمت پایین در بخش پارامتر interval را روی 1 می گذاریم و range را روی 5 تنظیم می کنیم.![2](https://github.com/user-attachments/assets/0b30892d-c90d-42c7-9887-34a6687aa1dd![3](https://github.com/user-attachments/assets/c90dba7b-2bde-46d3-90de-33e7b0619acb)
)
 در بخش isochrones می توانیم جمعیت و تمام موارد دیگر را ببینیم روی ابر بالا کلیک می کنیم تا فایل را دانلود کنیم. فرمت حتما geojson باشد.![4](https://github.com/user-attachments/assets/1575ee5d-3d53-4ce0-9051-fa731356f0cf)
 حالا یک پروژه ی جدید می سازیم و فایل شبکه ی معابر را وارد می کنیم. geojson یک فرمت متداول در وب هست و باید آن را وارد ارک جی ای اس بکنیم. در قسمت toolbox  در بخش conversion tools ابزار json to features را انتخاب می کنیم![8](https://github.com/user-attachments/assets/c6981901-e8d0-403a-8202-a38eb6c224a2)
 و در این مرحله فایل دانلود شده را وارد می کنیم. برای تحلیل شبکه نیاز به network dataset داریم. gis نمی فهمد که ایتن خطوط معبر هستند ما باشد بهش بفهمونیم که اینا معبر هستند پس باید network dataset بسازیم.در پنل catalog database را انتخاب کرده و روی نام جلسه راست کلیک می کنیم و روی create feature dataset کلیک می کنیم![5](https://github.com/user-attachments/assets/e1a50812-405c-446d-9d04-11ef05d48ee8)
(من این گزینه را نداشتم و از قسمت سرچ آن را آوردم)  حالا این مجموعه ای از لایه ها برای ما میسازدو نام آن را network می گذاریم و coordinate 32639 قرار می دهیم. سپس ران را می زنیم. دوباره روی همان لایه ی network راست کلیک می گذاریم و سپس import را می گذاریم و سپس feature class و در آخر input را می گذاریم روی شبکه معابر و ران را می زنیم.![6](https://github.com/user-attachments/assets/3703eabd-7921-4c92-8830-57380a73ab5d)

دوباره روی network راست کلیک می کنیم و new  را می زنیم و سپس network data set را می زنیم و target را network می گذاریم. نام  آن  را tehran_nd انتخاب می کنیم![7](https://github.com/user-attachments/assets/eab58790-04ad-4a84-8f29-b6ea905f9409)
.در بخش elevation هم no elevation را می زنیم.حالا دوباره روی لایه ی tehran_nd کلیک می کنیم و properties را می زنیم و travel attributes را انتخاب کرده و روی سه خط پنجره می زنیم. در نوار اول drive را انتخاب می کنیم. type را driving است و costs را روی length تنظیم میر کنیم![9](https://github.com/user-attachments/assets/d3e9529c-0bbb-4964-92ce-02a383f8d799)
 و اوکی را می زنیم و مود ساخته می شود. حالا راست کلیک می کنیم روی لایه و build را انتخاب می کنیم![10](https://github.com/user-attachments/assets/3dc13388-2a41-43f7-b245-3d3b6aa5ee72)
. و ران را می زنیم. حالا به برنامه فهماندیم که این یک شبکه اس بیمارستان را اد می کنیم و در تب analysis گزینه ی network analysis را انتخاب می کنیم و service area را می زنیم![12](https://github.com/user-attachments/assets/3c31622e-1f89-4911-9a20-43f3c8d1210a)
 و یک تبی به نام service area layer تشکیل می شود و در بخش facilities  ورودی را بیمارستان تنظیم می کنیم.![13](https://github.com/user-attachments/assets/62093524-3d53-4354-bc5b-a60c696bb663)
 و در cutoffs مشخص می کنیم که فاصله چقدر باشه و چیارو تحلیل می کند از یک نقطه و به یک نقطه با هم فرق دارند. یک overlap داریم که میگه اگه اینا روی هم افتادن باید چیکار کنه و ما میگیم که روی dissolve تنظیم بشه![14](https://github.com/user-attachments/assets/f3ab0856-6332-4554-849f-18962f9825e5)
 چون از نظر گرافیکی بهتر است. ران را می زنیم سپس بافر را می زنیم![15](https://github.com/user-attachments/assets/cb2336ca-054e-4e91-b6ee-27e323fea5f2)
 و ورودی را بیمارستان انتخاب می کنیم و فاصله را 100 می گذاریم در آخر هم از بخش polygon ها خروجی میگیریم![16](https://github.com/user-attachments/assets/79b944ad-a460-4aa3-81b4-0c3d67b30dd9)
.
