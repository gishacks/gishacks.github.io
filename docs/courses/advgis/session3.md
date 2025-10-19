---
title: جلسه ۳ - تحلیل سطح
# تحلیل فضایی
یکی از روش­ های قابل استفاده برای تحلیل فضایی، روش **تحلیل مطلوبیت** است. 
برای مثال، می خواهیم ایستگاه متروی جدیدی در تهران احداث کنیم، معیارها می تواند گزینه­ های زیر باشد:
ایستگاه­ های متروی موجود  
کاربری­ های اطراف
تراکم جمعیت  
تعداد شاغلین و مراکز تجاری
برای نمونه می خواهیم فاصله تا ایستگاه های متروی موجود را بدست آوریم. 2 نوع ارزیابی وجود دارد:
**نزدیکی**
**دسترسی**

برای شروع، نزدیکی را انتخاب می کنیم:
1. ابتدا باید لایه وکتوری را تبدیل به رستر کنیم. برای اینکار در قسمت vector conversion گزینه Rasterize (vector to raster) را انتخاب می کنیم. در پنجره باز شده، در قسمت Input layer، لایه وکتوری مورد نظر را انتخاب می کنیم. سپس در قسمت A Fixed value to burn ، عدد 1 را تایپ می کنیم. بخش Output Raster را روی گزینه Georeferensed می گذاریم. در قسمت Width و Height ، عدد 10 را تایپ می کنیم. 
https://www.dropbox.com/scl/fi/m80vrog0mdiwqgoxjd15w/Screenshot-2025-10-16-083803.png?rlkey=lf4fi143t5ijjjmps3c82zawd&st=iwiuaulc&dl=0
در قسمت Output Extent، می توانیم گزینه select extent on canvas را انتخاب کنیم و سپس محدوده مورد نظر را سلکت کنیم. در بخش Advanced Parameters، و در قسمت Output data type، گزینه Int 16 را انتخاب می کنیم و سپس Run می کنیم.
https://www.dropbox.com/scl/fi/fvnztm2fviqpqlu7zq1yg/Screenshot-2025-10-16-085112.png?rlkey=m2bq3d4zsc0wdkoui08racjb8&st=h9oc5d3l&dl=0
2. حالا باید نزدیکی را بسنجیم. از قسمت ،  Proximity ،Processing Toolbox را انتخاب میکنیم. در قسمت Input layer ، لایه رستری شده را وارد می کنیم. بعد قسمت Distance units ، گزینه Georeferenced Coordinates را انتخاب می کنیم. یک مسیر ذخیره برای لایه انتخاب می کنیم و run می کنیم. 
https://www.dropbox.com/scl/fi/akofyaka1o038c6tojju8/Screenshot-2025-10-17-121122.png?rlkey=s1c8firvlw7gcmsck2j8ls0dg&st=e1mfknbt&dl=0
3. مرحله بعد، طبقه بندی کردن فاصله هاست. هرچه فاصله از ایستگاه موجود بیشتر باشد، برای احداث ایستگاه جدید مطلوب تر است. از قسمت Reclassify by table ،Processing Toolbox  را انتخاب می کنیم. در قسمت Raster layer ، همان لایه Proximity  را انتخاب می کنیم. از قسمت Reclassification table علامت 3 نقطه را انتخاب میکنیم و Add row را زده و فاصله ها را طبقه بندی می کنیم:
https://www.dropbox.com/scl/fi/o3439p2ez2xaorjms81nz/Screenshot-2025-10-17-122312.png?rlkey=t4pfecg1zf2du83yvasy4qble&st=6lbbaw3p&dl=0
بعد قسمت output type  را در حالت Int 16 می گذاریم:
https://www.dropbox.com/scl/fi/uh40ak8ide551611qp9wy/Screenshot-2025-10-17-122549.png?rlkey=dcv7fqfqs585m31pdt7jtwvrk&st=jev3q3v5&dl=0
در آخر به چنین نقشه ای میرسیم:
https://www.dropbox.com/scl/fi/2qrjd3x6d1updb5tr8qhd/Screenshot-2025-10-17-123602.png?rlkey=6xkqovp9e3rihg9l3d08b7hyb&st=u45cfac0&dl=0
---
# نقشه پایه شما می توانید برای کارهای شهرسازی، خودتان یک **نقشه پایه** درست کنید و به همه ی افراد این امکان را بدهید تا از آن نقشه پایه استفاده کنند. برای دیدن یک مجموعه ای از نقشه های پایه، می توانید [اینجا کلیک کنید](https://leaflet-extras.github.io/leaflet-providers/preview/) آدرس مشخص شده در تصویر را کپی کنید: https://www.dropbox.com/scl/fi/zauorpsf7sdf5rlon98es/Screenshot-2025-10-10-013039.png?rlkey=9opvypwijqwrp9jq4dz2beupp&st=82afwh66&dl=0 وارد نرم افزار **ArcGIS Pro** شوید. روی گزینه Add Data کلیک کنید. سپس گزینه Data From Path را انتخاب کرده و نقشه را add کنید: https://www.dropbox.com/scl/fi/7a2u33c0u98qk9hlsuoed/Screenshot-2025-10-10-014058.png?rlkey=6qx93kea0dsbqrl7p6kmsgix7&st=cgjp04da&dl=0 برای اضافه کردن نقشه پایه در نرم افزار **Qgis**، ابتدا از قسمت plugins، و سپس manage and install plugins را انتخاب کنید: https://www.dropbox.com/scl/fi/mmyaw2xvyyj80bt3s6nyt/Screenshot-2025-10-10-021449.png?rlkey=51yew7gr027pwm0d0giojko2p&st=hq45rm26&dl=0 پلاگین **QuickMapServices** را سرچ و نصب کنید: https://www.dropbox.com/scl/fi/j93c641428m7vzmvfkj8e/Screenshot-2025-10-10-021939.png?rlkey=nz6ne2tv5byhio7gxp4ml5sry&st=ngpazr3t&dl=0 حالا در منوی web، یک گزینه ای اضافه شده به اسم QuickMapServices، روی آن کلیلک و سپس گزینه settings را انتخاب کنید. سپس به قسمت more services بروید و گزینه Get contributed pack را انتخاب کرده و save کنید: https://www.dropbox.com/scl/fi/bah2wy4q45c7p82aqpdnk/Screenshot-2025-10-10-023100.png?rlkey=jqj5okbeqsai464ij3he1rage&st=4mifjlb8&dl=0 حالا از همان منوی web، میتوانید نقشه های پایه ای را که از بخش های مختلف طبقه بندی کرده است، اضافه کنید: https://www.dropbox.com/scl/fi/uy0t8lfliurfrkdnhrf8a/Screenshot-2025-10-10-023834.png?rlkey=2pkqzb4mw0vvvjcb2cffs7yjg&st=gr5rnyvv&dl=0 # خروجی عکس گرفتن از نقشه پایه در Qgis روی لایه نقشه پایه اضافه شده در نرم افزار Qgis راست کلیک کرده، سپس Export و بعد save as را بزنید: https://www.dropbox.com/scl/fi/e9p776ri8mzxoh2g6fayw/Screenshot-2025-10-10-024304.png?rlkey=je83ie3g7hap5ye8d3gqpkiog&st=24bk4ytb&dl=0 در صفحه باز شده، فورمت GeoTIFF، تیک گزینه Create VRT را بردارید، در قسمت Extent، گزینه Map Canvas Extent یعنی محدوده نقشه ای که مشخص کردیم و در صفحه قابل مشاهده است. گزینه Calculate from Layer یعنی محدوده خروجی، شبیه یک لایه دیگری که شما دارید و مشخص می کنید، باشد. گزینه Current Layer Extent یعنی محدوده کل گوگل را در نظر می گیرد. در قسمت Resolution، و گزینه Horizontal، کیفیت نقشه را می توانید تعیین کنید. عدد ثابتی را نمی توان تعیین کرد؛ می توانید عددهای مختلف وارد کنید تا به کیفیت مطلوب دست پیدا کنید. هرچقدر این عدد کوچک تر باشد، کیفیت تصویر بهتر و هر چقدر آن عدد بزرگتر باشد، حجم کمتر خواهد بود که باید یک تعادل بین این دو مورد برقرار کنید. https://www.dropbox.com/scl/fi/tad14bxp87use7c0ysyt2/Screenshot-2025-10-10-031723.png?rlkey=l1yhbt25b6iiiq9azgvd6313n&st=dfna655d&dl=0
