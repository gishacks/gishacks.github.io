تفاوت‌های for و while:
1. استفاده از for:

وقتی از for استفاده می‌کنیم، معمولاً قصد داریم روی یک مجموعه یا بازه‌ی مشخصی از داده‌ها عملیات انجام دهیم و تعداد دفعات تکرار مشخص است.

تعداد تکرار معلوم است: به عنوان مثال، وقتی می‌خواهیم از عدد ۱ تا ۱۰۰ چاپ کنیم، می‌دانیم که تعداد تکرارها ۱۰۰ بار است.

پیمایش عناصر یک آرایه یا لیست: اگر بخواهیم هر عنصر از یک لیست یا آرایه را پردازش کنیم، از for استفاده می‌کنیم.

کار کردن با بازه‌های عددی (range): مثلا می‌خواهیم از یک عدد شروع کنیم و تا عددی مشخص ادامه دهیم.
2. استفاده از while:
از while برای مواقعی مناسب است که نمی‌دانیم چند بار باید حلقه تکرار شود، بلکه تنها یک شرط داریم که تا زمانی که این شرط برقرار باشد، حلقه باید ادامه یابد.

تعداد تکرار مشخص نیست: این حلقه تا زمانی که شرطی خاص برقرار باشد، ادامه می‌یابد.


شرط ادامه: برای مثال، اگر بخواهیم حلقه تا زمانی که یک متغیر به مقدار خاصی رسید ادامه پیدا کند، از while استفاده می‌کنیم.
----------------------------------------------------------------------------

``` python
import time
from datetime import datetime
from zoneinfo import ZoneInfo
import shutil
import os
from tqdm import tqdm
import requests
import geopandas as gpd
import pandas as pd

steps = 2
step = 0
period = 5 * 60  # 5 دقیقه
tehran_tz = ZoneInfo("Asia/Tehran")

while True:
    now = datetime.now(tehran_tz)
    timestamp = now.strftime("%Y%m%d_%H%M")
    temp_path = os.path.join('data', 'traffic_temp', timestamp)
    
    os.makedirs(temp_path, exist_ok=True)

    for x in tqdm(range(x_min, x_max + 1), desc='Downloading X Tiles ...'):
        for y in range(y_min, y_max + 1):
            url = URL_Template.format(z=ZOOM, x=x, y=y)
            outfile = os.path.join(temp_path, f"ZOOM_{x}_{y}.mvt")
            try:
                resp = requests.get(url, headers=None, timeout=15)
                if resp.status_code == 200 and resp.content:
                    with open(outfile, 'wb') as f:
                        f.write(resp.content)
                else:
                    print(f"[WARN] {resp.status_code}: {url}")
            except Exception as e:
                print(f"[ERROR] {e}: {url}")

    gdfs = []
    for file in os.listdir(temp_path):
        if file.endswith('.mvt'):
            mvt_path = os.path.join(temp_path, file)
            gdf = gpd.read_file(mvt_path)
            gdfs.append(gdf)

    merge_gdfs = gpd.GeoDataFrame(pd.concat(gdfs, ignore_index=True), crs='EPSG:4326')
    merge_gdfs.to_file(os.path.join(OUT_DIR, f'traffic_{timestamp}.shp'))

    shutil.rmtree(temp_path)

    step += 1
    if step < steps:
        print(f"Idle for {period // 60} mins before next step. Run so far {step} / {steps}")
        time.sleep(period)
    else:
        print(f"Completed. Ran {step} / {steps}!")
        break


```

بخش اول: وارد کردن کتابخانه‌ها
```python
import time
```
کتابخانه time﻿ برای کار با زمان است. در این کد از آن برای توقف موقت برنامه (مثلاً ۵ دقیقه صبر کردن) استفاده می‌شود.

```python
from datetime import datetime
```
یک کلاس است که تاریخ و زمان را نگهداری می‌کند. به ما کمک می‌کند که زمان فعلی را بگیریم و آن را به فرمت دلخواه تبدیل کنیم.

```python
from zoneinfo import ZoneInfo
```

 برای تعیین منطقه زمانی است. چون می‌خواهیم زمان تهران را داشته باشیم، از این استفاده می‌کنیم.

```python
import shutil
```
کتابخانه shutil﻿ برای عملیات پیشرفته روی فایل‌ها و پوشه‌هاست. در اینجا برای حذف پوشه‌های موقت استفاده می‌شود.

```python
import os
```
 کتابخانه‌ای است برای کار با سیستم عامل. با آن می‌توانیم پوشه بسازیم، مسیر فایل‌ها را بسازیم، یا لیست فایل‌های یک پوشه را ببینیم.

```python
from tqdm import tqdm
```

یک نوار پیشرفت (progress bar) در خط فرمان نمایش می‌دهد. وقتی حلقه‌ای طولانی داریم، این نشان می‌دهد چند درصد کار انجام شده است.

```python
import requests
```
کتابخانه requests﻿ برای ارسال درخواست به اینترنت است. با آن می‌توانیم فایل یا داده از یک آدرس اینترنتی دانلود کنیم.



بخش دوم: تنظیمات اولیه
```python
steps = 2
step = 0
```
متغیر steps﻿ تعداد دفعاتی که می‌خواهیم داده دانلود کنیم را مشخص می‌کند (در اینجا ۲ بار). متغیر step﻿ شمارنده‌ای است که از ۰ شروع می‌شود و هر بار یکی اضافه می‌شود.

```python
period = 5 * 60
```
این متغیر فاصله زمانی بین هر دانلود را به ثانیه مشخص می‌کند. 5 * 60﻿ یعنی ۵ دقیقه یا ۳۰۰ ثانیه.

```python
tehran_tz = ZoneInfo("Asia/Tehran")
```
یک شیء منطقه زمانی برای تهران می‌سازیم تا بتوانیم زمان دقیق تهران را بگیریم.

بخش سوم: حلقه اصلی
```python
while True:
```
یک حلقه بی‌نهایت است که تا زمانی که دستور break﻿ اجرا نشود، ادامه می‌یابد.

```python
now = datetime.now(tehran_tz)
```
زمان فعلی را با منطقه زمانی تهران می‌گیریم و در متغیر now﻿ ذخیره می‌کنیم.

```python
timestamp = now.strftime("%Y%m%d_%H%M")
```
تاریخ و زمان را به یک رشته متنی با فرمت خاص تبدیل می‌کنیم. مثلاً 20251114_2334﻿ که یعنی سال ۲۰۲۵، ماه ۱۱، روز ۱۴، ساعت ۲۳، دقیقه ۳۴. این برای نام‌گذاری فایل‌ها استفاده می‌شود.

```python
temp_path = os.path.join('data', 'traffic_temp', timestamp)
```
یک مسیر کامل برای پوشه موقت می‌سازیم.  مثلاً data/traffic_temp/20251114_2334﻿.

```python
os.makedirs(temp_path, exist_ok=True)
```
پوشه را می‌سازیم. پارامتر exist_ok=True﻿ یعنی اگر پوشه از قبل وجود دارد، خطا ندهد و ادامه بده.

بخش چهارم: دانلود کاشی‌ها
```python
for x in tqdm(range(x_min, x_max + 1), desc='Downloading X Tiles ...'):
```
یک حلقه که از x_min﻿ تا x_max﻿ (شامل x_max﻿) تکرار می‌شود. tqdm﻿ نوار پیشرفت نمایش می‌دهد و desc﻿ متنی است که روی نوار پیشرفت نمایش داده می‌شود.

```python
for y in range(y_min, y_max + 1):
```
یک حلقه تو در تو برای مختصات y﻿. این دو حلقه باعث می‌شوند تمام کاشی‌های یک ناحیه مستطیلی دانلود شوند.

```python
url = URL_Template.format(z=ZOOM, x=x, y=y)
```
آدرس کامل هر کاشی را می‌سازیم. URL_Template﻿ یک رشته قالبی است مثل "http://example.com/{z}/{x}/{y}.mvt"﻿ که مقادیر {z}﻿، {x}﻿، {y}﻿ با اعداد واقعی جایگزین می‌شوند.

```python
outfile = os.path.join(temp_path, f"ZOOM_{x}_{y}.mvt")
```
نام و مسیر فایل خروجی را می‌سازیم. f"ZOOM_{x}_{y}.mvt"﻿ یک f-string است که متغیرها را داخل رشته قرار می‌دهد. مثلاً ZOOM_100_50.mvt﻿.

```python
try:
    resp = requests.get(url, headers=None, timeout=15)
```
بلوک try-except﻿ برای مدیریت خطاهاست. اگر خطایی رخ دهد، برنامه متوقف نمی‌شود. requests.get﻿ درخواست دانلود را ارسال می‌کند و timeout=15﻿ یعنی اگر ظرف ۱۵ ثانیه جواب نیامد، خطا بده.

```python
if resp.status_code == 200 and resp.content:
```
بررسی می‌کنیم که آیا دانلود موفق بوده (یعنی موفق) و محتوایی وجود دارد.

```python
with open(outfile, 'wb') as f:
    f.write(resp.content)
```
فایل را برای نوشتن باز می‌کنیم. 'wb'﻿ یعنی حالت نوشتن دودویی (برای فایل‌های غیر متنی). with﻿ باعث می‌شود فایل بعد از اتمام کار خودکار بسته شود. محتوای دانلود شده را در فایل می‌نویسیم.

```python
else:
    print(f"[WARN] {resp.status_code}: {url}")
```
اگر دانلود موفق نبود، یک پیغام هشدار نمایش می‌دهیم.

```python
except Exception as e:
    print(f"[ERROR] {e}: {url}")
```
اگر هر خطای دیگری رخ داد (مثلاً مشکل اینترنت)، پیغام خطا را نمایش می‌دهیم.

بخش پنجم: ادغام فایل‌ها
```python
gdfs = []
```
یک لیست خالی برای نگهداری داده‌های جغرافیایی می‌سازیم.

```python
for file in os.listdir(temp_path):
```
لیست تمام فایل‌های درون پوشه موقت را می‌گیریم و روی آنها حلقه می‌زنیم.

python
if file.endswith('.mvt'):
فقط فایل‌هایی که با .mvt﻿ تمام می‌شوند را پردازش می‌کنیم.

```python
mvt_path = os.path.join(temp_path, file)
gdf = gpd.read_file(mvt_path)
```
مسیر کامل فایل را می‌سازیم و سپس فایل MVT﻿ را با geopandas﻿ می‌خوانیم. این فایل را به یک GeoDataFrame تبدیل می‌کند.

```python
gdfs.append(gdf)
```
در اینجا GeoDataFrame را به لیست اضافه می‌کنیم.

```python
merge_gdfs = gpd.GeoDataFrame(pd.concat(gdfs, ignore_index=True), crs='EPSG:4326')پ
```
تمام GeoDataFrame‌ها را به هم می‌چسبانیم. pd.concat﻿ آنها را به صورت عمودی (ردیف به ردیف) ترکیب می‌کند. ignore_index=True﻿ یعنی شماره ردیف‌ها را از نو شروع کن. crs='EPSG:4326'﻿ سیستم مختصات جغرافیایی (طول و عرض جغرافیایی) را تعیین می‌کند.

```python
merge_gdfs.to_file(os.path.join(OUT_DIR, f'traffic_{timestamp}.shp'))
```
داده‌های ادغام شده را به صورت یک فایل شیپ فایل ذخیره می‌کنیم. نام فایل شامل تاریخ و زمان است.

بخش ششم: پاکسازی و کنترل حلقه
```python
shutil.rmtree(temp_path)
```
کل پوشه موقت و تمام محتویات آن را حذف می‌کنیم. rmtree﻿ یعنی حذف بازگشتی (پوشه و زیرپوشه‌ها و فایل‌های داخل آن).

```python
step += 1
```
شمارنده را یکی افزایش می‌دهیم. این معادل step = step + 1﻿ است.

```python
if step < steps:
```
بررسی می‌کنیم که آیا هنوز مرحله بیشتری باقی مانده یا نه.

```python
print(f"Idle for {period // 60} mins before next step. Run so far {step} / {steps}")
time.sleep(period)
```
پیغامی نمایش می‌دهیم که چند دقیقه صبر می‌کنیم. //﻿ عملگر تقسیم صحیح است که نتیجه را گرد می‌کند. سپس برنامه را به اندازه period﻿ ثانیه متوقف می‌کنیم.

```python
else:
    print(f"Completed. Ran {step} / {steps}!")
    break
```
اگر به تعداد دفعات مورد نظر رسیدیم، پیغام پایان کار را نمایش می‌دهیم و با break﻿ از حلقه خارج می‌شویم.

خلاصه کارکرد کلی
این کد هر ۵ دقیقه یکبار (۲ بار در مجموع) داده‌های ترافیک را از یک سرویس نقشه به صورت کاشی‌های MVT دانلود می‌کند، آنها را در یک پوشه موقت ذخیره می‌کند، سپس تمام کاشی‌ها را می‌خواند، به هم می‌چسباند و به صورت یک فایل شیپ فایل نهایی ذخیره می‌کند. در نهایت فایل‌های موقت را پاک می‌کند و منتظر دوره بعدی می‌ماند.

در بخش بعدی 
```python
import osmnx as ox

G_OSM = ox.graph_from_bbox(*BBOX, network_type='drive')

# استخراج بخش‌های جاده‌ای
osm_segments = ox.graph_to_gdfs(G_OSM, nodes=False, edges=True)

# استخراج نقاط (نودها)
osm_nodes = ox.graph_to_gdfs(G_OSM, nodes=True, edges=False)

# چاپ داده‌ها
print(osm_segments.head()) 
print(osm_nodes.head())    
```
این خط شبکه جاده‌ای را از OpenStreetMap دانلود می‌کند.
بخش‌های این خط:

استفاده از ox.graph_from_bbox()﻿: تابعی از کتابخانه OSMnx است که داده‌های شبکه خیابان‌ها را از OpenStreetMap بر اساس یک محدوده جغرافیایی (bounding box) دانلود می‌کند.​

همچنین network_type='drive'﻿: نوع شبکه را مشخص می‌کند. 'drive'﻿ یعنی فقط جاده‌هایی که ماشین می‌تواند در آنها تردد کند. انواع دیگر عبارتند از 'walk'﻿ برای مسیرهای پیاده، 'bike'﻿ برای مسیرهای دوچرخه، و 'all'﻿ برای همه انواع.​​

وG_OSM﻿: خروجی این تابع یک graph (گراف) است. گراف یک ساختار داده ریاضی است که از نقاط (nodes) و خطوط رابط (edges) تشکیل شده است. در شبکه جاده‌ای، نقاط معمولاً تقاطع‌ها و انتهای خیابان‌ها هستند و خطوط رابط خود خیابان‌ها هستند.​​

خط دوم: استخراج بخش‌های جاده‌ای
```python
osm_segments = ox.graph_to_gdfs(G_OSM, nodes=False, edges=True)
```
این خط بخش‌های جاده‌ای (خیابان‌ها) را از گراف استخراج می‌کند و به یک GeoDataFrame تبدیل می‌کند.​

استفاده از ox.graph_to_gdfs()﻿: تابعی است که گراف را به GeoDataFrame تبدیل می‌کند. GeoDataFrame مانند یک جدول است که ستون‌های جغرافیایی دارد.​

این nodes=False﻿: یعنی نقاط (تقاطع‌ها) را در خروجی نیاور.​

همچنین edges=True﻿: یعنی فقط یال‌ها (خیابان‌ها و بخش‌های جاده‌ای) را در خروجی بیاور.​

چرا این کار را انجام می‌دهیم؟ گراف یک ساختار داده پیچیده است که برای تحلیل‌های خاص مناسب است، اما برای کار با داده‌های جغرافیایی، پردازش، و ذخیره‌سازی، GeoDataFrame راحت‌تر است چون می‌توانیم آن را مانند یک جدول فیلتر کنیم، ستون‌ها را تغییر دهیم، و به فرمت‌های مختلف (مثل Shapefile) ذخیره کنیم.​

استفاده از osm_segments﻿: یک GeoDataFrame است که هر ردیف آن یک قطعه از جاده را نشان می‌دهد. این جدول ستون‌هایی مانند نام خیابان، نوع جاده، حداکثر سرعت، و هندسه خط (LineString) دارد.​

خط سوم: استخراج نقاط (نودها)
```python
osm_nodes = ox.graph_to_gdfs(G_OSM, nodes=True, edges=False)
```
این خط نقاط شبکه (تقاطع‌ها و انتهای خیابان‌ها) را از گراف استخراج می‌کند.
در​ این خط nodes=True﻿: یعنی نقاط (nodes) را در خروجی بیاور.​

و edges=False﻿: یعنی یال‌ها (خیابان‌ها) را در خروجی نیاور.​

و osm_nodes﻿: یک GeoDataFrame است که هر ردیف آن یک نقطه (تقاطع یا انتهای خیابان) را نشان می‌دهد. این جدول ستون‌هایی مانند طول و عرض جغرافیایی، و هندسه نقطه (Point) دارد.​

خط‌های چهارم و پنجم: نمایش داده‌ها
```python
print(osm_segments.head())
print(osm_nodes.head())
```
استفاده از .head()﻿: یک متد از pandas است که ۵ ردیف اول یک جدول را نمایش می‌دهد. این برای بررسی سریع ساختار داده‌ها مفید است.​

خط اول: اولین ۵ قطعه جاده را نمایش می‌دهد. شما می‌توانید ببینید هر خیابان چه ویژگی‌هایی دارد (مثلاً نام، طول، نوع).​

خط دوم: اولین ۵ نقطه (تقاطع) را نمایش می‌دهد. شما می‌توانید مختصات جغرافیایی و سایر اطلاعات هر تقاطع را ببینید.​

خلاصه کارکرد کلی
این کد سه کار اصلی انجام می‌دهد:​

شبکه جاده‌ای یک منطقه را از OpenStreetMap دانلود می‌کند (در قالب گراف)

بخش‌های جاده‌ای (خطوط) را از گراف جدا می‌کند و به GeoDataFrame تبدیل می‌کند

نقاط تقاطع را از گراف جدا می‌کند و به GeoDataFrame تبدیل می‌کند

بعد از این مراحل، شما دو جدول جغرافیایی دارید که می‌توانید آنها را تحلیل کنید، فیلتر کنید، روی نقشه نمایش دهید، یا به فرمت‌های دیگر (مثل Shapefile) ذخیره کنید.​

---------------------------------------------------------------

```python
osm_segments = osm_segments.reset_index()
```
وقتی که داده‌ها را از OpenStreetMap می‌گیرید و آن‌ها را به GeoDataFrame تبدیل می‌کنید، ممکنه ایندکس‌ها درست مرتب نشده باشند یا ترتیبشان به هم خورده باشد.

با استفاده از reset_index(), ایندکس‌ها به شکل استاندارد (عدد صحیح متوالی) برمی‌گردند و ستون ایندکس قبلی به نام "index" به DataFrame اضافه می‌شود.

---------------------------------------------------------------------------

```python

import glob
import os
import geopandas as gpd
import pandas as pd

traffic_files = glob.glob(os.path.join(OUT_DIR, 'traffic_*.shp'))
traffic_gdfs = {}

for filepath in traffic_files:
    timestamp = os.path.basename(filepath).replace('traffic_20', '').replace('.shp', '')
    gdf = gpd.read_file(filepath).to_crs(osm_segments.crs)
    traffic_gdfs[timestamp] = gdf

osm_segments['max_speed_kmh'] = pd.to_numeric(osm_segments['maxspeed'], errors='coerce')
osm_segments['max_speed_kmh'] = osm_segments['max_speed_kmh'].fillna(30)
osm_segments['max_speed_mps'] = osm_segments['max_speed_kmh'] * 1000 / 3600

congestion_factors = {
    'low': 0.9,
    'moderate': 0.7,
    'heavy': 0.5,
    'severe': 0.3
}

for ts, tgdf in traffic_gdfs.items():
    joined = gpd.sjoin(
        osm_segments,
        tgdf[['geometry', 'congestion']],
        how='left',
        predicate='intersects'
    )
    
    joined = joined.groupby(['u', 'v', 'key']).agg({'congestion': 'first'}).reset_index()
    joined = joined.rename(columns={'congestion': f'cg_{ts}'})
    
    osm_segments = osm_segments.merge(
        joined[['u', 'v', 'key', f'cg_{ts}']],
        on=['u', 'v', 'key'],
        how='left'
    )
    
    osm_segments[f'cg_w_{ts}'] = osm_segments[f'cg_{ts}'].map(congestion_factors).fillna(1)
    osm_segments[f'adj_spd_{ts}'] = osm_segments['max_speed_mps'] * osm_segments[f'cg_w_{ts}']
    osm_segments[f'trvl_time_{ts}'] = osm_segments['length'] / osm_segments[f'adj_spd_{ts}']
```
بخش اول: وارد کردن کتابخانه‌ها و یافتن فایل‌ها
```python
import glob
import os
import geopandas as gpd
import pandas as pd
```
کتابخانه glob﻿ برای جستجوی فایل‌ها با الگوی خاص استفاده می‌شود. کتابخانه os﻿ برای کار با مسیرها و سیستم عامل است. geopandas﻿ برای کار با داده‌های جغرافیایی و pandas﻿ برای مدیریت جداول داده استفاده می‌شود.​

```python
traffic_files = glob.glob(os.path.join(OUT_DIR, 'traffic_*.shp'))
```
متغیر traffic_files﻿ لیستی از تمام فایل‌های شیپ فایلی که با traffic_﻿ شروع می‌شوند را در پوشه OUT_DIR﻿ پیدا می‌کند. علامت *﻿ یک wildcard است که به معنای "هر چیزی" است. مثلاً traffic_20251114_2330.shp﻿ و traffic_20251114_2335.shp﻿ را پیدا می‌کند.​

```python
traffic_gdfs = {}
```
دیکشنری خالی است که قرار است داده‌های ترافیکی را با کلید timestamp (زمان) ذخیره کند.​

بخش دوم: خواندن فایل‌های ترافیکی
```python
for filepath in traffic_files:
```
حلقه‌ای است که روی تمام فایل‌های پیدا شده تکرار می‌شود.​

```python
timestamp = os.path.basename(filepath).replace('traffic_20', '').replace('.shp', '')
```
زمان (timestamp) را از نام فایل استخراج می‌کند. ابتدا os.path.basename()﻿ فقط نام فایل را بدون مسیر کامل برمی‌گرداند (مثلاً traffic_20251114_2330.shp﻿). سپس replace()﻿ قسمت traffic_20﻿ و .shp﻿ را حذف می‌کند و فقط 251114_2330﻿ باقی می‌ماند.​

```python
gdf = gpd.read_file(filepath).to_crs(osm_segments.crs)
```
فایل شیپ فایل را می‌خواند و به GeoDataFrame تبدیل می‌کند. متد .to_crs()﻿ سیستم مختصات جغرافیایی (CRS) را به همان سیستمی که osm_segments﻿ دارد تبدیل می‌کند تا بتوانیم آنها را روی هم قرار دهیم. این مرحله برای تحلیل‌های مکانی بسیار مهم است.​

```python
traffic_gdfs[timestamp] = gdf
```
داده‌های خوانده شده را با کلید timestamp در دیکشنری ذخیره می‌کند.​

بخش سوم: محاسبه سرعت‌های مجاز
```python
osm_segments['max_speed_kmh'] = pd.to_numeric(osm_segments['maxspeed'], errors='coerce')
```
ستون maxspeed﻿ که از OpenStreetMap آمده را به عدد تبدیل می‌کند. پارامتر errors='coerce'﻿ یعنی اگر مقداری قابل تبدیل به عدد نبود، آن را NaN﻿ (مقدار خالی) قرار بده.​

```python
osm_segments['max_speed_kmh'] = osm_segments['max_speed_kmh'].fillna(30)
```
مقادیر خالی (NaN﻿) را با عدد ۳۰ پر می‌کند. این یعنی اگر سرعت مجاز برای یک جاده مشخص نبود، فرض می‌کنیم ۳۰ کیلومتر بر ساعت است.​

```python
osm_segments['max_speed_mps'] = osm_segments['max_speed_kmh'] * 1000 / 3600
```
سرعت را از کیلومتر بر ساعت به متر بر ثانیه تبدیل می‌کند. فرمول: ۱ کیلومتر = ۱۰۰۰ متر و ۱ ساعت = ۳۶۰۰ ثانیه، پس ضرب در ۱۰۰۰ و تقسیم بر ۳۶۰۰.​

بخش چهارم: تعریف ضرایب ترافیک
```python
congestion_factors = {
    'low': 0.9,
    'moderate': 0.7,
    'heavy': 0.5,
    'severe': 0.3
}
```
دیکشنری است که برای هر وضعیت ترافیک یک ضریب کاهش سرعت تعریف می‌کند. مثلاً 'low'﻿ (ترافیک کم) یعنی ماشین‌ها با ۹۰٪ سرعت مجاز حرکت می‌کنند، و 'severe'﻿ (ترافیک شدید) یعنی فقط ۳۰٪ سرعت مجاز.​

بخش پنجم: پیوند دادن داده‌های ترافیک
```python
for ts, tgdf in traffic_gdfs.items():
```
حلقه‌ای است که روی تمام زمان‌بندی‌های ترافیک تکرار می‌شود. متغیر ts﻿ زمان (timestamp) و tgdf﻿ داده‌های ترافیک آن زمان است.​

```python
joined = gpd.sjoin(
    osm_segments,
    tgdf[['geometry', 'congestion']],
    how='left',
    predicate='intersects'
)
```
عملیات spatial join﻿ است که دو لایه جغرافیایی را بر اساس موقعیت مکانی به هم متصل می‌کند. پارامتر how='left'﻿ یعنی تمام ردیف‌های osm_segments﻿ را نگه دار حتی اگر داده ترافیک نداشتند. پارامتر predicate='intersects'﻿ یعنی اگر دو شکل هندسی با هم تقاطع داشتند، آنها را به هم وصل کن.​

```python
joined = joined.groupby(['u', 'v', 'key']).agg({'congestion': 'first'}).reset_index()
```
داده‌ها را بر اساس شناسه منحصر به فرد هر بخش جاده (u﻿، v﻿، key﻿) گروه‌بندی می‌کند. این سه ستون شناسه یال (edge) در گراف OSMnx هستند: u﻿ نود مبدأ، v﻿ نود مقصد، و key﻿ شناسه یال در صورت وجود چند یال بین دو نود. متد agg({'congestion': 'first'})﻿ اولین مقدار ترافیک را برای هر گروه انتخاب می‌کند.​

```python
joined = joined.rename(columns={'congestion': f'cg_{ts}'})
```
نام ستون ترافیک را تغییر می‌دهد و timestamp را به آن اضافه می‌کند. مثلاً cg_251114_2330﻿ که نشان می‌دهد این داده ترافیک مربوط به چه زمانی است.​

```python
osm_segments = osm_segments.merge(
    joined[['u', 'v', 'key', f'cg_{ts}']],
    on=['u', 'v', 'key'],
    how='left'
)
```
داده‌های ترافیک را به جدول اصلی osm_segments﻿ اضافه می‌کند. عملیات merge﻿ دو جدول را بر اساس ستون‌های مشترک (u﻿، v﻿، key﻿) به هم می‌چسباند.​

بخش ششم: محاسبه سرعت و زمان سفر
```python
osm_segments[f'cg_w_{ts}'] = osm_segments[f'cg_{ts}'].map(congestion_factors).fillna(1)
```
وضعیت ترافیک را به ضریب عددی تبدیل می‌کند. متد map()﻿ مقادیر را بر اساس دیکشنری congestion_factors﻿ تبدیل می‌کند. مثلاً 'moderate'﻿ به 0.7﻿ تبدیل می‌شود. متد fillna(1)﻿ برای جاده‌هایی که اطلاعات ترافیک ندارند، ضریب ۱ (بدون کاهش سرعت) می‌دهد.​

```python
osm_segments[f'adj_spd_{ts}'] = osm_segments['max_speed_mps'] * osm_segments[f'cg_w_{ts}']
```
سرعت تعدیل شده را بر اساس ترافیک محاسبه می‌کند. این سرعت واقعی است که با ضرب سرعت مجاز در ضریب ترافیک به دست می‌آید. مثلاً اگر سرعت مجاز ۱۰ متر بر ثانیه و ضریب ۰.۷ باشد، سرعت واقعی ۷ متر بر ثانیه است.​

```python
osm_segments[f'trvl_time_{ts}'] = osm_segments['length'] / osm_segments[f'adj_spd_{ts}']
```
زمان سفر را برای هر بخش جاده محاسبه می‌کند. فرمول ساده است: زمان = مسافت ÷ سرعت. ستون length﻿ طول جاده به متر است و با تقسیم بر سرعت (متر بر ثانیه)، زمان سفر به ثانیه به دست می‌آید. این زمان‌ها بعداً برای محاسبه کوتاه‌ترین مسیر بر اساس زمان (نه فقط مسافت) استفاده می‌شوند.​

خلاصه کارکرد کلی
این کد داده‌های ترافیک لحظه‌ای را با شبکه جاده‌ای OpenStreetMap ترکیب می‌کند و برای هر بخش جاده در هر زمان، سرعت واقعی و زمان سفر را بر اساس وضعیت ترافیک محاسبه می‌کند. این اطلاعات برای تحلیل‌های مسیریابی (routing) و پیش‌بینی زمان سفر در شبکه حمل‌ونقل شهری استفاده می‌شود.​

---------------------------------------------

این کد یک گراف NetworkX از داده‌های جغرافیایی OSM می‌سازد. هر خیابان به عنوان یک یال در گراف نمایش داده می‌شود که سه ویژگی دارد: طول فیزیکی و دو زمان سفر برای دو بازه زمانی مختلف. برای خیابان‌های دوطرفه، دو یال در جهت‌های مخالف اضافه می‌شود.
```python

import networkx as nx
G = nx.MultiDiGraph()
for idx, row in osm_segments.iterrows():
    u = row['u']
    v = row['v']
    length = row['length']
    time1 = row['trvl_time_251031_1650']
    time2 = row['trvl_time_251031_1656']
    G.add_edge(u, v, length=length, time1=time1, time2=time2)
    
    if not row['oneway']:
        G.add_edge(v, u, length=length, time1=time1, time2=time2)
```
توضیح کد:
```python
G = nx.MultiDiGraph()
```
ساخت یک گراف جهت‌دار چندگانه (MultiDiGraph) خالی است. این نوع گراف سه ویژگی مهم دارد: اول، جهت‌دار است یعنی یال از نود A به نود B با یال از B به A متفاوت است. دوم، چندگانه است یعنی می‌تواند چندین یال موازی بین دو نود داشته باشد. سوم، هر یال می‌تواند ویژگی‌های دلخواه (مانند طول یا زمان) داشته باشد.​

```python
for idx, row in osm_segments.iterrows():
```
حلقه‌ای است که روی تمام ردیف‌های GeoDataFrame به نام osm_segments﻿ تکرار می‌شود. متد iterrows()﻿ دو مقدار برمی‌گرداند: idx﻿ که شماره ردیف (index) است و row﻿ که خود ردیف به صورت یک Series است. این روش استاندارد برای پیمایش داده‌های pandas است.

```python
u = row['u']
v = row['v']
```
استخراج شناسه نودهای مبدأ و مقصد هر یال است. در گراف‌های OSMnx، u﻿ نود شروع (source node) و v﻿ نود پایان (target node) هر خیابان را نشان می‌دهد. این‌ها معمولاً شماره‌های منحصر به فرد نودها در OpenStreetMap هستند.​

```python
length = row['length']
```
طول جاده را از ستون length﻿ استخراج می‌کند. این مقدار معمولاً به متر است و از محاسبات جغرافیایی OSMnx به دست آمده است.​

```python

time1 = row['trvl_time_251031_1650']
time2 = row['trvl_time_251031_1656']
```
زمان سفر را برای دو بازه زمانی مختلف استخراج می‌کند. ستون trvl_time_251031_1650﻿ زمان سفر در تاریخ ۳۱ اکتبر سال ۲۰۲۵ ساعت ۱۶:۵۰ است و trvl_time_251031_1656﻿ برای ساعت ۱۶:۵۶ است. این زمان‌ها قبلاً با در نظر گرفتن وضعیت ترافیک محاسبه شده‌اند.​

```python
G.add_edge(u, v, length=length, time1=time1, time2=time2)
```
یک یال جهت‌دار از نود u﻿ به نود v﻿ به گراف اضافه می‌کند. پارامترهای length﻿، time1﻿، و time2﻿ به عنوان ویژگی‌های (attributes) این یال ذخیره می‌شوند. این ویژگی‌ها بعداً برای الگوریتم‌های مسیریابی (مثل کوتاه‌ترین مسیر بر اساس زمان) استفاده می‌شوند.​

```python
if not row['oneway']:
    G.add_edge(v, u, length=length, time1=time1, time2=time2)
```
بررسی می‌کند که آیا خیابان یک‌طرفه است یا نه. ستون oneway﻿ اگر True﻿ باشد یعنی جاده یک‌طرفه است و فقط از u﻿ به v﻿ قابل تردد است. اگر False﻿ یا NaN﻿ باشد، جاده دوطرفه است و یال معکوس (از v﻿ به u﻿) نیز با همان ویژگی‌ها به گراف اضافه می‌شود.​


خلاصه کارکرد کلی
این کد یک گراف NetworkX از داده‌های جغرافیایی OSM می‌سازد. هر خیابان به عنوان یک یال در گراف نمایش داده می‌شود که سه ویژگی دارد: طول فیزیکی و دو زمان سفر برای دو بازه زمانی مختلف. برای خیابان‌های دوطرفه، دو یال در جهت‌های مخالف اضافه می‌شود. 


-----------------------------------------------

```python

for idx, row in osm_nodes.iterrows():
    attrs = row.drop('geometry').to_dict()
    attrs['geometry'] = row.geometry
    G.add_node(idx, **attrs)
```
این کد تمام نودهای (تقاطع‌ها و انتهای خیابان‌ها) از GeoDataFrame به گراف NetworkX منتقل می‌کند. هر نود با شناسه منحصر به فرد خود و تمام ویژگی‌هایش (مثل موقعیت جغرافیایی، تعداد خیابان‌های متصل، و غیره) به گراف اضافه می‌شود. این کار گراف را کامل می‌کند چون قبلاً یال‌ها (خیابان‌ها) اضافه شده بودند و حالا نودها هم با تمام اطلاعات جغرافیایی‌شان به گراف اضافه می‌شوند.


-----------------------------------------------

```python
G.graph['crs'] = osm_segments.crs
```
این تکنیک مفید است زمانی که داده‌های جغرافیایی را در گراف نگهداری می‌کنید و می‌خواهید اطمینان حاصل کنید که CRS داده‌های جغرافیایی گراف با CRS داده‌های اصلی همخوانی دارد.

----------------------------------------------------

```python
tags = {'amenity': 'fire_station'}
fire_stations = ox.features.features_from_bbox(BBOX, tags)
fire_stations = fire_stations[fire_stations.geometry.type == 'Point']
len(fire_stations)
```

شرح کد:

تعریف تگ‌ها برای جستجو:

```python
tags = {'amenity': 'fire_station'}
```


این خط یک دیکشنری به نام tags ایجاد می‌کند که برای جستجوی ایستگاه‌های آتش‌نشانی از آن استفاده می‌شود. amenity با مقدار fire_station به معنی ایستگاه‌های آتش‌نشانی است.

استخراج داده‌ها با استفاده از OSMnx:

```python
fire_stations = ox.features.features_from_bbox(BBOX, tags)
```


این خط از تابع features_from_bbox در کتابخانه OSMnX استفاده می‌کند تا داده‌های ایستگاه‌های آتش‌نشانی را بر اساس یک Bounding Box (BBOX) استخراج کند. tags هم برای فیلتر کردن ایستگاه‌های آتش‌نشانی استفاده می‌شود.

فیلتر کردن نقاط:

```python
fire_stations = fire_stations[fire_stations.geometry.type == 'Point']
```


این خط از داده‌های جغرافیایی (GeoDataFrame) فقط نقاط (که نوع هندسه آن‌ها Point است) را فیلتر می‌کند. این کار با استفاده از فیلتر کردن داده‌ها بر اساس نوع هندسه انجام می‌شود.

شمارش تعداد ایستگاه‌های آتش‌نشانی:

```python
len(fire_stations)
```


این خط تعداد ایستگاه‌های آتش‌نشانی موجود در داده‌های فیلتر شده را محاسبه می‌کند و تعداد نقاطی که به عنوان ایستگاه‌های آتش‌نشانی شناسایی شده‌اند را برمی‌گرداند.

------------------------------------------------------------


```python
fire_stations['nearest_node'] = fire_stations.geometry.apply(
    lambda geom: ox.nearest_nodes(G, geom.x, geom.y)
)
```

شرح کد:

تعریف تابع lambda:

```python
lambda geom: ox.nearest_nodes(G, geom.x, geom.y)
```


در این خط از یک تابع lambda برای اعمال تابع nearest_nodes به هندسه‌های ایستگاه‌های آتش‌نشانی استفاده می‌شود.

تابع nearest_nodes از کتابخانه OSMnX استفاده می‌کند تا نزدیک‌ترین نود (گره) به مختصات (طول و عرض جغرافیایی) ایستگاه‌های آتش‌نشانی را پیدا کند.


```python
fire_stations['nearest_node'] = fire_stations.geometry.apply(
    lambda geom: ox.nearest_nodes(G, geom.x, geom.y)
)
```


در این خط، از apply() برای اعمال تابع lambda به هر هندسه از ایستگاه‌های آتش‌نشانی استفاده می‌شود. به این ترتیب، برای هر ایستگاه آتش‌نشانی، نزدیک‌ترین نود جاده‌ای در گراف G پیدا می‌شود.

نتیجه این عمل به ستون جدید nearest_node در fire_stations اضافه می‌شود.

-------------------------------------------------


```python

cutoff = 10*60  # 10 دقیقه
service_time1 = []
service_time2 = []

for idx, fs in fire_stations.iterrows():
    nearest_node = fs['nearest_node']
    
    # محاسبه زمان سرویس برای دو زمان مختلف
    sa_time1 = nx.single_source_dijkstra_path_length(
        G, nearest_node, cutoff=cutoff, weight=time1
    )
    sa_time2 = nx.single_source_dijkstra_path_length(
        G, nearest_node, cutoff=cutoff, weight=time2
    )
    
    # ساخت زیرگراف برای هر زمان
    subgraph_time1 = G.subgraph(sa_time1.keys()).copy()
    subgraph_time2 = G.subgraph(sa_time2.keys()).copy()
    
    # ذخیره زیرگراف‌ها
    service_time1.append(subgraph_time1)
    service_time2.append(subgraph_time2)
```

-------------------------------------------------------------------


```python

import matplotlib.pyplot as plt
import networkx as nx
import osmnx as ox

# رسم گراف اصلی
fix, ax = ox.plot_graph(
    G,
    show=False,
    close=False,
    node_size=0,
    edge_color='lightgray',
    figsize=(30, 20)
)

# تنظیم حدود نمایشی
minx, miny, maxx, maxy = BBOX
ax.set_xlim([minx, maxx])
ax.set_ylim([miny, maxy])

# رسم مسیرهای سرویس‌دهی زمان 1 به رنگ قرمز
for sa in service_time1:
    ox.plot_graph(sa, ax=ax, node_size=0, edge_linewidth=0.2, edge_color='red', show=False)

# رسم مسیرهای سرویس‌دهی زمان 2 به رنگ آبی
for sa in service_time2:
    ox.plot_graph(sa, ax=ax, node_size=0, edge_linewidth=0.2, edge_color='blue', show=False)

# رسم ایستگاه‌های آتش‌نشانی
fire_stations.plot(ax=ax, marker='o', color='green', markersize=100)

# اضافه کردن عنوان
plt.title('Fire stations Service areas in Time 1 (red), Time 2(blue)')

# نمایش گراف
plt.show()
```
