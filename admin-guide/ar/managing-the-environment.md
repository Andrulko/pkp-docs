# إدارة بيئة الخادوم

إدارة تطبيق PKP تعني عموماً:

* (ب) ضمان الوفاء بمتطلبات النظام؛
* تهيئة النظام وتطبيقه بشكل سليم للعمل بشكل صحيح؛
* إدارة عملية التثبيت والترقية.

تطبيقات PKP هي تطبيقات ويب PHP/MySQL بسيطة نسبياً، ويمكن تشغيلها فقط في أي مكان، توفر نسخة حديثة نسبياً من PHP و MySQL متاحة. خيارات تكوين أخرى (مثل PostgreSQL، MS SQL) ممكنة.

يمكن تنزيل حزمة التنزيلات لتطبيقات PKP من موقع PKP في المواقع التالية:

* OJS: [https://pkp.sfu.ca/ojs/ojs_download](https://pkp.sfu.ca/ojs/ojs_download)
* OMP: [https://pkp.sfu.ca/omp/omp_download](https://pkp.sfu.ca/omp/omp_download)
* OCS: [https://pkp.sfu.ca/ocs/ocs_download](https://pkp.sfu.ca/ocs/ocs_download)

جميع التطبيقات التي تشحن مع مجموعة كاملة من وثائق التكوين والتثبيت والترقية، موجودة في دليل `docs/` في تحميل الحزمة. وينبغي الرجوع إليها كمورد رئيسي لأي سؤال يتعلق بالتكوين أو التركيب أو الترقية. وينبغي استعراضها دوريا (لا سيما كجزء من أي عملية للتحديث). يوفر PKP هذه الإرشادات على الويب، ونحن نقدم روابط سريعة أدناه.

## الحلول المستضيفة

إذا لم يكن لديك الخبرة أو الموظفين أو الرغبة في تثبيت وإدارة OJS بمفردك، توفر خدمات النشر في PKP حلول الاستضافة الكاملة بعدد من النقاط السعرية. للمزيد من المعلومات، انظر [موقع خدمات النشر PKP](https://pkpservices.sfu.ca).

## متطلبات النظام والتثبيت

ويمكن الاطلاع على تفاصيل متطلبات النظام العامة وتوصيات التشكيلات وتعليمات التثبيت العامة في مختلف ملفات README التطبيق:

* OJS: [https://pkp.sfu.ca/ojs/README](https://pkp.sfu.ca/ojs/README)
* OMP: [https://pkp.sfu.ca/omp/README](https://pkp.sfu.ca/omp/README)
* OCS: [https://pkp.sfu.ca/ocs/README](https://pkp.sfu.ca/ocs/README)

## ترقية

يمكن العثور على تعليمات الترقية في المواقع التالية:

* OJS: [https://pkp.sfu.ca/ojs/UPGRADE](https://pkp.sfu.ca/ojs/UPGRADE)
* OMP: [https://pkp.sfu.ca/omp/UPGRADE](https://pkp.sfu.ca/omp/UPGRADE)
* OCS: [https://pkp.sfu.ca/ocs/UPGRADE](https://pkp.sfu.ca/ocs/UPGRADE)

## تثبيت وإدارة التطبيقات عبر Git

يتيح لك استخدام Git لإدارة برنامج PKP الخاص بك التحكم بشكل أكبر في التحديثات وإصلاحات الأخطاء من مستودع PKP الرسمي. باستخدام Git، يمكنك إنشاء فروع محلية لتخصيص التعليمات البرمجية الخاصة بك، والتحقق واختبار أحدث التغييرات في إصدار البرنامج الخاص بك، قم بمسح التعليمات البرمجية الخاصة بك بسهولة أكبر، و قم بإنشاء طلبات سحب للعودة إلى مستودع PKP لمشاركتها مع المجتمع الأكبر.

يتطلب تثبيت OJS و OMP مع Git تثبيت واستخدام [Node.js](https://nodejs.org/en/) و [الملحن](https://getcomposer.org/). وكلتا الأداتين مطلوبتان لتحديث حالات التبعية التي تستخدمها مكتبة PKP. ولا يحتاج نظام OCS حاليا إلى هذه الأدوات.

تعليمات التثبيت عبر Git يمكن العثور عليها مباشرة في مستودعات GitHub الخاصة بنا في المواقع التالية:

* OJS: [https://github.com/pkp/ojs](https://github.com/pkp/ojs)
* OMP: [https://github.com/pkp/omp](https://github.com/pkp/omp)
* OCS: [https://github.com/pkp/ocs](https://github.com/pkp/ocs)
