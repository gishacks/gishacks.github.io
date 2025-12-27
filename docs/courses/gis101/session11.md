---
title: مکان‌یابی مدرسه و تمرین تحلیل مطلوبیت
---
# مکان‌یابی مدارس ابتدایی

## معیارهای ارزیابی
تراکم جمعیت
فاصله از مدارس موجود
فاصله از گسل
شیب
آلودگی هوا
فاصله از پارک

### معیارهای مهم و مورد نظر ما
فاصله از گسل
شیب
فاصله از پارک


## امتیاز‌دهی یا rating
بازه امتیازدهی را بین 5 و 5- در نظر می‌گیریم

# وزن‌دهی
ترتیب اهمیت معیارها: در این مرحله اگر بطور مثال دو معیار (فاصله از گسل و شیب زمین)
# روی هم‌اندازی
پس از وزن دهی میبینیم که یک لایه‌ای تشکیل میشود که با توجه به وزن دهی نشان داده میشود.


# تحلیل شبکه یا network analysis
برای تحلیل سطح پوشش برای ما دسترسی مهم است نه نزدیکی!
برای سنجش فاصله، صرفا فاصله مطرح نیست، بلکه مسیرها و راه ها مهم هستند.
## استفاده از سایت open route service برای تحلیل شبکه
یک .maps اضافه می‌کنیم به نام سایت تا صفحه نقشه برای ما نمایان شود
حال نقطه مورد نظر که برای ما تهران است را در نقشه انتخاب میکنیم
حالا find a place را میزنیم و یک نقطه در تهران را انتخاب میکنیم
حالا در نوار موجود داریم:
range: بیشترین فاصله از نظر راهها به نقطه انتخابی
interval: تعداد لایه ها یا لایه بندی (یعنی تعیین میکنیم که با توجه به رینج مثلا هر 1 کیلومتر یک لایه داشته باشیم.)
در واقع لایه بندی بر اساس راه ها است و نه فاصله!!!!
حالا میتوانیم برای دانلود این لایه ها و داده ها در نوار روی شکل دانلود کلیک کنیم و فرمت را روی geo json بگذاریم.

## کار عملی
لایه شبکه معابر را باز میکنیم (از لایه حمل و نقل)
برای آوردن لایه geo json:
analysis/ toolboxes/ conversion tools/ json/ json to feature/ آوردن فایلی که دانلود کردیم
برای فرمت geo json، نرم‌افزار آرک جی آی اس پرو مناسب نیست و کیو جی آی اس مناسب‌تر است.

به network dataset نیاز داریم.
در حالت عادی جی ای اس درکی از خطوط که بمعنای معبر هستند ندارد. پس ابتدا باید به نرم افزار بفهمانیم که معبر داریم و معبر چیست.

## ساخت network dataset
view/ catalog/ databases/ my project 20 (for example)/ right click on my project 20/ new/ dataset name: tehrannetwork/ سیستم مختصات نیز با همان کد 32639 درست میشود.
حالا روی دیتا ست ساخته شده راست کلیک میکنیم و ایمپورت و فیچر کلسز را انتخاب می‌کنیم.
حالا روی دیتا ست تهران نتورک راست کلیک میکنیم و نیو را میزنیم و نتورک دیتا ست را انتخاب میکنیم
تیک شبکه معابر را میزنیم و نام دیتا ست را tehran_nd میگذاریم
حالا روی لایه تهران ان دی کلیک راست میکنیم و properties را انتخاب میکنیم و از قسمت سمت چپ travel attributes را انتخاب میکنیم:
type: driving
length: meters
u turns: all
ok
حالا اگر لایه شبکه معابر را خاموش کنیم میبینیم که آنچه میماند یک سری خطوط خاکستری است که بمعنای شناخت شبکه معابر و راه ها توسط نرم افزار است.
حالا در تب analysis بخش network analysis را انتخاب میکنیم
حالا از تب های بالا service area layer را انتخاب میکنیم و روی import facilities کلیک میکنیم.
و اینپوت لوکیشن را لایه بیمارستان قرار میدهیم اوکی را میزنیم

حالا تنظیمات دیگر در این تب را نیز طبق عکس زیر اعمال میکنیم و سپس ران را میزنیم.

# استفاده از ابزارdensity
تراکم به معنای تقسیم یک چیز بر واحد سطح است
تحلیل های اسپیشال آنالیز از نوع رستری هستند.

## point density و kernel density
در کرنل، حرکت ها نرم تر نمایش داده میشوند و قابل فهم تر هستند

در کار جدید
بلاک جمعیتی سال 75 را باز میکنیم و از این طریق آن را تبدیل به نقطه میکنیم
data management tools/ feature/ feature to point



حوزه آب خیز را با مقصدش مینشاسیم
مثلا حوزه آب خیز دریاچه ارومیه
تمام آب‌هایی که به دریاچه ارومیه میریزند

## تصاویر مربوط به مراحل فوق
![توضیح تصویر](https://www.dropbox.com/scl/fi/bi23svtjlgenel8ygwiw9/WhatsApp-Image-2025-12-28-at-00.00.15.jpeg?rlkey=9y6ff9kdht3fe65yp5bg69m4a&st=cascnjn9&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/84g89y4wtqp6nfa39x0ze/WhatsApp-Image-2025-12-28-at-00.00.19.jpeg?rlkey=91ll7rdrrh3vfthdbnj1acwbb&st=h9s1o724&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/bg5fa951wzwv2a5dxhf3q/WhatsApp-Image-2025-12-28-at-00.00.20.jpeg?rlkey=c3qztoef72zae4e7mwow9razu&st=c0c5e8xf&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/c7h9xbgxmyamzzjrz7up5/WhatsApp-Image-2025-12-28-at-00.00.22.jpeg?rlkey=7sp21712d44grze1spvlu0lcy&st=4d8myr1s&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/vx23zfyzrqwagsvcm4ble/WhatsApp-Image-2025-12-28-at-00.00.29-2.jpeg?rlkey=hu3avu79o7xc78pwj3dz7e9gm&st=e994y4gr&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/r11z4725eeot8da0qgv01/WhatsApp-Image-2025-12-28-at-00.00.29-3.jpeg?rlkey=jzfontn3pvk3u2en57hu2ba4f&st=z0zrrdrq&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/lqexlqy6gcop38alm5cq6/WhatsApp-Image-2025-12-28-at-00.00.29-4.jpeg?rlkey=9o689e2yuq93cwbp3l2uea3uu&st=id60ssga&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/86xnd4jz31965i9sc6w3i/WhatsApp-Image-2025-12-28-at-00.00.29-5.jpeg?rlkey=lggw91novl30wpv16klmfyp8c&st=pboxudmm&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/dob8l5kh0bkjqzshe5yfy/WhatsApp-Image-2025-12-28-at-00.00.29.jpeg?rlkey=qkjq5uzvr3e8jxk2vrfml56de&st=ljhkpxkf&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/84i9gib4kw9uosyo7zg86/WhatsApp-Image-2025-12-28-at-00.00.30-2.jpeg?rlkey=s8ruo6tzy37t1x6x33kkbz9af&st=j7mv1qvo&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/cf1cc5n5vqgst08u760zs/WhatsApp-Image-2025-12-28-at-00.00.30-3.jpeg?rlkey=jdjjldxmbocmzhma42grfycnd&st=mj72udsz&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/g01fbppomjbh7jc8vzcyl/WhatsApp-Image-2025-12-28-at-00.00.30-4.jpeg?rlkey=r3avfy4u8ctoi2z0u000e5vec&st=gdzzudga&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/helsvzpjur4vgl7kfb3zr/WhatsApp-Image-2025-12-28-at-00.00.30-5.jpeg?rlkey=5hyjhb48a7pfwic884ru988vj&st=xoq5lmdb&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/30vtcdqhyex6uhan3903s/WhatsApp-Image-2025-12-28-at-00.00.30-6.jpeg?rlkey=yzt987n1nx732m7kou70hgprt&st=w9l96zq2&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/qth4m6d06dwk704wvo8cn/WhatsApp-Image-2025-12-28-at-00.00.30-7.jpeg?rlkey=35ofnltmt1q4t7gd20c9kjwtu&st=h3p2aka2&dl=0)
![توضیح تصویر](https://www.dropbox.com/scl/fi/nxeueft4hezp91cw65i73/WhatsApp-Image-2025-12-28-at-00.00.30.jpeg?rlkey=15687firbd7rbxu4u24y0lewa&st=jb7ja8ie&dl=0)
