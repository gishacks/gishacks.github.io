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
