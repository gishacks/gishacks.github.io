---
title: جلسه ۴ - تهیه نقشه از طریق نمایش داده‌ها ۲
--- در مرحله ی اول از سایت gishacks.ir قسمت ترفند ها و سپس نقشه پایه ها گزینه ی openstreetmap را پیدا می کنیم <img width="1881" height="929" alt="pic 1 gis" src="https://github.com/user-attachments/assets/3d627871-79bd-430d-8b4d-81fc254a8ac6" />
و سپس لینک آن را کپی کرده و در arcgis pro قسمت add data و سپس add data from path لینک را paste می کنیم<img width="1919" height="1002" alt="pic 2 gis" src="https://github.com/user-attachments/assets/bdda6dc0-53ce-4a61-b845-ec128f98b13f" />
.
سپس از قسمت add data- browse فایل پایگاه اطلاعات مکانی، حوضه و بلوک را انتخاب کرده و وارد می کنیم<img width="1920" height="1027" alt="pic 3 gis" src="https://github.com/user-attachments/assets/2cb5ae30-c82a-4154-bda1-910817e8fa07" />
.
در نوار سمت راست یا همان symbology- primary symbols را روی chart و نوع آن را نیز  pie chart  انتخاب می کنیم<img width="1920" height="1029" alt="pic 4 gis" src="https://github.com/user-attachments/assets/e5c39d9a-f9b8-4c26-9187-2252d3185538" />
.
بار دیگر primary symbols را روی dot density تنظیم می کنیم تا به صورت نقطه حوضه و بلوک را به ما نشان دهد<img width="1920" height="1024" alt="pic 5 gis" src="https://github.com/user-attachments/assets/35aff595-151e-458a-a341-447c6cfa600a" />
.
بار دیگر primary symbols را روی proportional symbols قرار میدهیم.<img width="1913" height="1022" alt="pic 6 gis" src="https://github.com/user-attachments/assets/98759789-2619-4736-ab96-c72e41cdf171" />
 تفاوت بین graduated و proportional این است که graduated بازه بندی می کند اما proportional دسته بندی نمی کند و به صورت دیفالت هر چقدر جمعیت بیشتر باشد دایره های ما را بزرگ تر می کند و در نقشه قرار می دهد
حال تمام لایه ها به جز لایه ی base map را خاموش می کنیم و در پایگاه اطلاعات مکانی فولدر زلزله های پیشین را وارد می کنیم <img width="1920" height="1029" alt="pic 7 gis" src="https://github.com/user-attachments/assets/672a0c5a-812b-40a7-9bd6-1c3549251584" />م
سپس در primary symbols  گزینه ی heatmap را انتخاب  می کنیم<img width="1920" height="1031" alt="pic 8 gis" src="https://github.com/user-attachments/assets/1c1f3d08-4bf3-4d7a-aedc-ea5591465948" />
 (تمرکز یک پدیده را در یک جا به این طریق می توان نشان داد این روش کاری به ویژگی ها ندارد) حال اگر قسمت weight field را به ZMAG تغییر دهیم نحوه ی تراکم تغییر می کند و هم شدت و هم تراکم در نظر گرفته می شود<img width="1916" height="1024" alt="pic 9 gis" src="https://github.com/user-attachments/assets/dadda9e3-85e6-4b44-85d6-9973bd7ba43b" />
.
حال در سایت USGS earthquake catalog فایل اکسل تمام زلزله های ایران را در ده سال اخیر که بالای 2 ریشتر بوده اند را پیدا می کنیم و در arc gis pro وارد می کنی<img width="1529" height="936" alt="pic 10 gis" src="https://github.com/user-attachments/assets/19c48947-b6ef-422f-bea3-ba6cb8f19a0c" <img width="1920" height="1029" alt="pic 11 gis" src="https://github.com/user-attachments/assets/571276b5-f0bd-47b6-af5e-4f024bf6256c" />
/>
م
حالا در نوار سمت چپ این فایل پدیدار می شود روی آن راست کلیک می کنیم و create point table را باز می کنیم
حال دوباره در primary symbols، heat map را انتخاب می کنیم weight field را mag انتخاب می کنیم method را نیز روی dynamic تنظیم می کنیم (وقتی method را constant می گذاریم کل نقاط را می گیرد و می گوید کجا تمرکزش بیشتر است اما وقتی dynamic را انتخاب می کنیم و زوم می کنیم مبنا بر حسب شهر تغییر می کند<img width="1913" height="1010" alt="pic 13 gis" src="https://github.com/user-attachments/assets/53598fd7-a945-40d9-98cb-d04d27b4c8e3" />
.
حال برای تهیه انیمیشن از قسمت view گزینه ی add را انتخاب می کنیم تا timeline پدیدار شود<img width="1920" height="1026" alt="pic 14 gis" src="https://github.com/user-attachments/assets/d5731642-b2eb-4d0b-8763-12393c850cc0" />
 سپس روی فولدر اکسل راست کلیک می کنیم و از قسمت properties گزینه ی تایم را انتخاب می کنیم و روی filter layer content based on attribute values را انتخاب می کنیم (این گونه به برنامخه می فهمانیم که زمان مهم است و اعداد نوشته شده معنی زمان دارند). این گونه یک نوار بالای نقشه پدیدار می شود<img width="1920" height="1030" alt="pic 15 gis" src="https://github.com/user-attachments/assets/06013438-009a-4395-838f-8aab9000c796" />
 روی ساعت بغل نوار کلیک می کنیم که کل بازه ی زملنی انتخاب شود و سپس در قسمت انیمیشن export را انتخاب می کنیم و با فرمت gif فیلم را ذخیره می کنیم.<img width="395" height="968" alt="pic 17 gis" src="https://github.com/user-attachments/assets/d2ab8251-d908-400e-88ed-cf9ce93872b4" />
 
.

