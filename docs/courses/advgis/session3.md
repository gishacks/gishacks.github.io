---
title: جلسه ۳ - تحلیل سطح
---

# نقشه پایه 

شما می توانید برای کارهای شهرسازی، خودتان یک **نقشه پایه** درست کنید و به همه ی افراد این امکان را بدهید تا از آن نقشه پایه استفاده کنند. برای دیدن یک مجموعه ای از نقشه های پایه، می توانید
[اینجا کلیک کنید](https://leaflet-extras.github.io/leaflet-providers/preview/) 

آدرس مشخص شده در تصویر را کپی کنید:

![آدرس نقشه‌های پایه](https://www.dropbox.com/scl/fi/zauorpsf7sdf5rlon98es/Screenshot-2025-10-10-013039.png?rlkey=9opvypwijqwrp9jq4dz2beupp&st=82afwh66&dl=1)

وارد نرم افزار **ArcGIS Pro** شوید. روی گزینه Add Data کلیک کنید. سپس گزینه Data From Path را انتخاب کرده و نقشه را add کنید:

![اضافه کردن نقشه پایه](https://www.dropbox.com/scl/fi/7a2u33c0u98qk9hlsuoed/Screenshot-2025-10-10-014058.png?rlkey=6qx93kea0dsbqrl7p6kmsgix7&st=cgjp04da&dl=1)

برای اضافه کردن نقشه پایه در نرم افزار **QGIS**، ابتدا از قسمت plugins، و سپس manage and install pluginsرا انتخاب کنید: 

![افزودن پلاگین](https://www.dropbox.com/scl/fi/mmyaw2xvyyj80bt3s6nyt/Screenshot-2025-10-10-021449.png?rlkey=51yew7gr027pwm0d0giojko2p&st=hq45rm26&dl=1)

پلاگین **QuickMapServices**را سرچ و نصب کنید: 

![نصب پلاگین](https://www.dropbox.com/scl/fi/j93c641428m7vzmvfkj8e/Screenshot-2025-10-10-021939.png?rlkey=nz6ne2tv5byhio7gxp4ml5sry&st=ngpazr3t&dl=1)

حالا در منوی web، یک گزینه ای اضافه شده به اسم QuickMapServices، روی آن کلیلک و سپس گزینه settings را انتخاب کنید. سپس به قسمت more services بروید و گزینه Get contributed pack را انتخاب کرده و save کنید: 

![افزودن نقشه‌های موجود](https://www.dropbox.com/scl/fi/bah2wy4q45c7p82aqpdnk/Screenshot-2025-10-10-023100.png?rlkey=jqj5okbeqsai464ij3he1rage&st=4mifjlb8&dl=1)


حالا از همان منوی web، میتوانید نقشه های پایه ای را که از بخش های مختلف طبقه بندی کرده است، اضافه کنید:

![اضافه کردن نقشه‌های پایه](https://www.dropbox.com/scl/fi/uy0t8lfliurfrkdnhrf8a/Screenshot-2025-10-10-023834.png?rlkey=2pkqzb4mw0vvvjcb2cffs7yjg&st=gr5rnyvv&dl=1)

# خروجی عکس گرفتن از نقشه پایه در Qgis روی لایه نقشه پایه اضافه شده در نرم افزار Qgis راست کلیک کرده، سپس Export و بعد save as را بزنید: 

![خروجی گرفتن از نقشه‌های پایه](https://www.dropbox.com/scl/fi/e9p776ri8mzxoh2g6fayw/Screenshot-2025-10-10-024304.png?rlkey=je83ie3g7hap5ye8d3gqpkiog&st=24bk4ytb&dl=1)

در صفحه باز شده، فورمت GeoTIFF، تیک گزینه Create VRT را بردارید، در قسمت Extent، گزینه Map Canvas Extent یعنی محدوده نقشه ای که مشخص کردیم و در صفحه قابل مشاهده است. گزینه Calculate from Layer یعنی محدوده خروجی، شبیه یک لایه دیگری که شما دارید و مشخص می کنید، باشد. گزینه Current Layer Extent یعنی محدوده کل گوگل را در نظر می گیرد. در قسمت Resolution، و گزینه Horizontal، کیفیت نقشه را می توانید تعیین کنید. عدد ثابتی را نمی توان تعیین کرد؛ می توانید عددهای مختلف وارد کنید تا به کیفیت مطلوب دست پیدا کنید. هرچقدر این عدد کوچک تر باشد، کیفیت تصویر بهتر و هر چقدر آن عدد بزرگتر باشد، حجم کمتر خواهد بود که باید یک تعادل بین این دو مورد برقرار کنید. 

![تنظیمات خروجی](https://www.dropbox.com/scl/fi/tad14bxp87use7c0ysyt2/Screenshot-2025-10-10-031723.png?rlkey=l1yhbt25b6iiiq9azgvd6313n&st=dfna655d&dl=1)

