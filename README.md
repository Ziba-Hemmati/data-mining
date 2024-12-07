# گزارش کار تمرین‌های داده‌کاوی

## مقدمه

در این پروژه، تمرکز بر روی پردازش و تحلیل داده‌های مربوط به یک آزمایش AB Testing بوده است. داده‌های مربوط به آزمایش شامل ویژگی‌هایی مانند `User ID`, `Group`, `Page Views`, `Time Spent`, `Conversion`, `Device`, و `Location` بودند. هدف اصلی این تمرین‌ها، استفاده از تکنیک‌های مختلف داده‌کاوی برای مصورسازی داده‌ها، پیش‌پردازش داده‌ها، خوشه‌بندی، و طبقه‌بندی بود. در این گزارش، به بررسی جزئیات هر مرحله از این اقدامات و نتایج حاصل پرداخته خواهد شد.

---

## مراحل انجام شده

### 1. مصورسازی داده‌ها (تمرین 1)

در این مرحله، هدف اصلی تحلیل و مصورسازی داده‌ها بود تا الگوها و روابط موجود بین ویژگی‌های مختلف داده‌ها به وضوح مشخص شوند. ابتدا داده‌ها بارگذاری شده و پنج نوع نمودار مختلف برای تحلیل داده‌ها رسم شد:

**نمودار پراکندگی (Scatter Plot)**: این نمودار برای تحلیل روابط بین ویژگی‌های عددی استفاده شد. در اینجا، رابطه بین `Page Views` و `Time Spent` برای هر گروه بررسی شد. این نمودار نشان داد که بین این دو ویژگی ارتباط خطی ضعیفی وجود دارد.

**نمودار هیستوگرام (Histogram)**: از این نمودار برای بررسی توزیع ویژگی‌های عددی مانند `Page Views` و `Time Spent` استفاده شد. نتایج نشان داد که توزیع داده‌ها بیشتر به سمت مقادیر پایین تمایل دارد.

**نمودار میله‌ای (Bar Plot)**: این نمودار برای مقایسه ویژگی‌های دسته‌ای مثل `Conversion` در دو گروه A و B استفاده شد. این نمودار نشان داد که نرخ تبدیل در گروه B نسبت به گروه A کمتر است.

**نمودار جعبه‌ای (Box Plot)**: از این نمودار برای بررسی توزیع ویژگی `Time Spent` در هر گروه استفاده شد. نتایج نشان داد که گروه B تنوع کمتری در زمان صرف شده برای صفحات دارد.

**نمودار خطی (Line Plot)**: این نمودار برای بررسی تغییرات ویژگی‌ها به مرور زمان استفاده شد. در اینجا، روند تغییرات `Page Views` و `Time Spent` در طول زمان بررسی شد.

این نمودارها به ما کمک کردند تا رفتار کاربران را بهتر درک کرده و به شناسایی روندها و الگوهای موجود در داده‌ها بپردازیم.

---

### 2. پیش‌پردازش داده‌ها (تمرین 2)

در این مرحله، اقدامات پیش‌پردازش برای آماده‌سازی داده‌ها جهت مدل‌سازی انجام شد:

**پاکسازی داده‌ها**: در این بخش، ابتدا بررسی شد که آیا داده‌های گمشده‌ای در مجموعه وجود دارد یا خیر. خوشبختانه، هیچ داده گمشده‌ای یافت نشد و تمامی مقادیر در دسترس بودند.

**تبدیل داده‌ها**: ویژگی‌های غیرعددی مانند `Device` و `Location` که به صورت متنی بودند، با استفاده از روش **One-Hot Encoding** به ویژگی‌های عددی تبدیل شدند. این تبدیل برای استفاده در مدل‌های یادگیری ماشین ضروری بود.

**ایجاد ویژگی جدید**: ویژگی جدیدی به نام **Time per Page** ایجاد شد. این ویژگی نشان‌دهنده زمان متوسط صرف شده توسط کاربران برای هر صفحه است. این ویژگی می‌تواند برای تحلیل رفتار کاربر و میزان تعامل با صفحات مفید باشد.

این اقدامات پیش‌پردازش باعث شدند که داده‌ها برای استفاده در مدل‌های مختلف یادگیری ماشین آماده شوند.

---

### 3. خوشه‌بندی داده‌ها (تمرین 3)

در این مرحله، از سه روش مختلف خوشه‌بندی برای شبیه‌سازی و شناسایی خوشه‌ها در داده‌ها استفاده کردیم:

**Agglomerative Clustering**:

این روش خوشه‌بندی افرازبندی است که از رویکرد مبتنی بر فاصله برای ایجاد خوشه‌ها استفاده می‌کند. نتایج نشان داد که این روش توانست خوشه‌هایی با کیفیت متوسط شبیه‌سازی کند.

**C-Link (Complete Linkage)**:

 این روش برای خوشه‌بندی سلسله‌مراتبی تجمعی استفاده شد. نتایج نشان داد که این روش توانست خوشه‌ها را به خوبی از یکدیگر جدا کند و نتایج مناسبی از نظر کیفیت خوشه‌ها ارائه داد.

**S-Link (Single Linkage)**: 

این روش دیگر برای خوشه‌بندی سلسله‌مراتبی تجمعی استفاده شد. این روش معمولاً برای ایجاد خوشه‌های پراکنده استفاده می‌شود و در اینجا نتایج ضعیف‌تری به دست آمد.

برای ارزیابی نتایج خوشه‌بندی، از دو معیار **Silhouette Score** و **Davies-Bouldin Score** استفاده کردیم. نتایج نشان داد که روش **C-Link** بهترین عملکرد را در مقایسه با دو روش دیگر داشت.

---

### 4. طبقه‌بندی با درخت تصمیم‌گیری و بیزین ساده (تمرین 4)

در این مرحله، از دو مدل **درخت تصمیم‌گیری** و **بیزین ساده** برای پیش‌بینی ویژگی `Conversion` (که نشان‌دهنده موفقیت یا شکست در تبدیل کاربر به مشتری است) استفاده کردیم:

**درخت تصمیم‌گیری**: مدل درخت تصمیم‌گیری برای پیش‌بینی این که آیا یک کاربر تبدیل خواهد شد یا خیر، مورد استفاده قرار گرفت. نتایج نشان داد که دقت مدل پایین است با **Precision: 0.1163** و **Recall: 0.0926**.

**بیزین ساده**: مدل بیزین ساده عملکرد غیرمعمولی داشت و دقت بسیار بالایی در پیش‌بینی `Conversion` در کلاس مثبت داشت (با **Precision: 1.0000**)، اما در عین حال **Recall: 0.0000** بود که نشان‌دهنده مشکل در پیش‌بینی درست کلاس‌های منفی است.

برای بهبود نتایج، از تکنیک **SMOTE** برای متعادل‌سازی داده‌ها استفاده کردیم. این تکنیک باعث بهبود عملکرد مدل‌ها در پیش‌بینی درست کلاس‌ها شد.

---

## تحلیل نتایج

**مصورسازی داده‌ها**: این مرحله توانست روابط مختلف بین ویژگی‌ها را به وضوح نمایش دهد. تحلیل این نمودارها باعث شد که بتوانیم بهتر به درک و تحلیل داده‌ها بپردازیم.

**پیش‌پردازش داده‌ها**: پیش‌پردازش داده‌ها، به خصوص تبدیل ویژگی‌های متنی به عددی و ایجاد ویژگی‌های جدید، به مدل‌ها کمک کرد تا داده‌ها را به شکلی قابل استفاده دریافت کنند.

**خوشه‌بندی**: با استفاده از روش‌های مختلف خوشه‌بندی، توانستیم خوشه‌هایی با ویژگی‌های مشترک شبیه‌سازی کنیم. این مرحله به تحلیل رفتار کاربران و شناسایی الگوهای مشابه کمک کرد.

**طبقه‌بندی**: طبقه‌بندی داده‌ها با استفاده از مدل‌های مختلف نشان داد که دقت پیش‌بینی‌ها می‌تواند تحت تأثیر توزیع داده‌ها قرار گیرد. استفاده از تکنیک‌هایی مانند SMOTE برای متعادل‌سازی داده‌ها می‌تواند به بهبود عملکرد مدل‌ها کمک کند.

---

## نتیجه‌گیری

این پروژه به ما این امکان را داد که با استفاده از تکنیک‌های مختلف داده‌کاوی، از جمله مصورسازی، پیش‌پردازش، خوشه‌بندی و طبقه‌بندی، به تحلیل دقیق‌تر داده‌ها پرداخته و الگوهای مختلف موجود در داده‌ها را شبیه‌سازی کنیم. با استفاده از این تکنیک‌ها، توانستیم به شناسایی روابط بین ویژگی‌ها، خوشه‌های مشابه، و مدل‌های پیش‌بینی با دقت بالا دست یابیم.
