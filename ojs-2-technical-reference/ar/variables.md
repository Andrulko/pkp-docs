# المتغيرات

يتم تعيين متغيرات القالب بشكل عام في صفحة أو فئة النموذج التي تسمي القالب. بالإضافة إلى ذلك، يتم تعيين العديد من المتغيرات بواسطة صف `TemplateManager` وهي متاحة لجميع القوالب:

- `defaultCharset`: قيمة إعداد "client_charset" من [i18n] قسم `config.inc.php`
- `اللغة الحالية`: الاسم الرمزي للغة الحالية
- `baseUr`l: URL الأساسي للموقع، على سبيل المثال http://www.mylibrary.com
- `مطلوب`: الاسم الرمزي للصفحة المطلوبة
- `عنوان الصفحة`: الاسم الافتراضي للمفتاح المحلي لعنوان الصفحة؛ يجب استبدال هذا بإعدادات أكثر ملاءمة في القالب
- `موقع الموقع`: إذا كان المستخدم يقوم حاليا بتصفح صفحة مرتبطة بالمجلة، هذا هو عنوان المجلة؛ خلاف ذلك عنوان الموقع من تكوين الموقع
- `publicfilesDir`: عنوان URL لدليل الملفات العامة المنطبق حاليا (انظر القسم المعنون إدارة الملفات)
- `صفحة المسار`: مسار الصفحة والعملية المطلوبة، إذا كان ذلك منطبقاً، مرفقة مسبقاً بخط مسطح؛ على سبيل المثال /user/profile
- `الرابط الحالي`: الرابط الكامل للصفحة الحالية
- `dateFormatTrunc`: قيمة `date_format_trunc` في القسم `[general]` من `التكوين. nc.php` ملف الإعداد؛ يستخدم مع date_formatSmarty وظيفة
- `dateFormatShort`: قيمة date_format_short parameter في `[general]القسم` من `الإعداد. nc.php` ملف الإعداد؛ يستخدم مع date_formatSmarty وظيفة
- `dateFormatLong`: قيمة معلمة date_format_long في `[general]` قسم من `الإعداد. nc.php` ملف الإعداد؛ يستخدم مع date_formatSmarty وظيفة
- (د)`atetimeFormatShor`: قيمة `datetime_format_short` معلمة في `[general]` قسم من `التكوين. nc.php` ملف الإعداد؛ يستخدم مع date_formatSmarty وظيفة
- `datetimeFormatLong`: قيمة `datetime_format_long` معلمة في `[general]` قسم من `التكوين. nc.php` ملف الإعداد؛ يستخدم مع date_formatSmarty وظيفة
- `الحالي`: اسم اللغة المنطبقة؛ على سبيل المثال `en_US`
- `المادةSearchByOptions`: أسماء الحقول القابلة للبحث المستخدمة من قبل ميزة البحث في الشريط الجانبي وعلى صفحة البحث
- `جلسة المستخدم`: كائن الدورة الحالية
- `isUserLoggedin`: Boolean الذي يشير إلى ما إذا كان المستخدم قد تم تسجيل الدخول أم لا
- `lologedInUsername`: اسم المستخدم الحالي ، إذا كان ذلك منطبقا
- `page_links`: الحد الأقصى لعدد الروابط للصفحة التي سيتم عرضها لقائمة مميزة داخل اليومية الحالية أو سياق الموقع.
- `items_per_page`: الحد الأقصى لعدد العناصر التي سيتم عرضها في كل صفحة من قائمة الصفحات في اليومية الحالية أو سياق الموقع.

وبالإضافة إلى ذلك، إذا كان المستخدم يتصفح الصفحات التابعة لمجلة معينة، تكون المتغيرات التالية متاحة:

- `currentJournal`: موضوع المجلة المنطبق حاليا (من `Journal` class)
- `مناوب Locale1`: الإعدادات المحلية البديلة الأولى (`مناوب Locale2`) إعداد المجلة
- `مناوب Locale2`: الإعدادات المحلية البديلة الثانية (`مناوب Locale1`) إعداد المجلة
- `navMenuItems`: تصفح العناصر (`navms`إعداد المجلة
- `pageHeaderTtitle`: مستخدمة من قبل `قوالب/common/header.tpl` لعرض المعلومات الخاصة بالمجلة
- `pageHeaderLogo`: مستخدمة من قبل `قوالب/common/header.tpl` لعرض المعلومات الخاصة بالمجلة
- `بالتناوب في رأس الصفحة`: مستخدمة من قبل `قوالب/common/header.tpl` لعرض المعلومات الخاصة بالمجلة
- `metaSsearchchDescription`: الوصف الحالي لليومية؛ يستخدم في الوسوم الوصفية
- `metaSearchKeywords`: الكلمات الرئيسية لليومية الحالية؛ تستخدم في العلامات الوصفية
- `العناوين الرئيسية للعميل`: العناوين المخصصة لليومية الحالية، إذا تم تعريفها؛ تستخدم في العلامات الوصفية
- `ورقات أنماط`: مجموعة من ورقات الأنماط لتضمينها مع القالب
- `صفحة تذييل الصفحة`: محتوى تذييل مخصص ليتم عرضه في نهاية الصفحة

إذا تم تمكين لغات متعددة، يتم تعيين المتغيرات التالية:

- `تمكين اللغة-تبديل`: تعيين إلى "صواب" عند تمكين هذه الميزة
- `languageTogleLocales`: مصفوفة من المواقع المحددة
