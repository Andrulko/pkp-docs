---
generateHeadingToc: صحيح
---

# شبكة حفظ PKP

## مقدمة

وتسمح شبكة حفظ PKP (PKP PN) للناشرين في مجلات OJS بالحفاظ على محتواها رقمياً. هذا يعني في حالة توقف المجلة عن النشر أو عدم الاتصال، وستكون هناك طريقة لمواصلة الوصول على المدى الطويل إلى المقالات والقضايا.

تودع PN PKP المحتوى باستخدام برنامج [LOCKSS](http://www.lockss.org/) الذي يوفر الحفاظ اللامركزي والموزع. وهذا يتيح للمجلات التي لا تشكل جزءا من أي خدمة أخرى لحفظ التكنولوجيا الرقمية (مثل CLOCKSS أو Portico) إمكانية الحفاظ على إمكانية الوصول إليها على المدى الطويل.

وتعمل شبكة PPKN كأرشيف مظلم، مما يعني أن المستعملين النهائيين لن يتمكنوا من الوصول إلى المحتوى المحتفظ به إلا بعد وقوع "حدث محفز". بعد حدث تحريك، سيقوم موظفو PKP باستيراد المحتوى المحتفظ به إلى واحدة أو أكثر من أمثلة OJS التي تستضيفها المؤسسات الأعضاء في PKP. بمجرد تحميلها إلى مثيلات OJS المضيفة، سيكون المحتوى متاحاً للجمهور.

يرجى ملاحظة أن أرشفة المحتوى الخاص بك في PKP PN ليس نفس النسخ الاحتياطي لموقع OJS الخاص بك. لا يمكن استخدام أرشيف PKP إذا فقدت المحتوى على موقعك وتحتاج إلى استعادته. النسخ الاحتياطي المتكرر لموقعك يجب أن يتم بشكل منفصل.

بالإضافة إلى ضمان الوصول طويل الأجل إلى المحتوى الخاص بك، إن وجود استراتيجية حفظ رقمية وحفظ الملفات وجعل هذا الأمر صريحا كجزء من سياسة هو أحد المكونات الرئيسية في [عملية طلب شعبة الشؤون الإدارية والسياسة](https://docs.pkp.sfu.ca/doaj/en/) وأحد المعايير للحصول على ختم شعبة الشؤون الإدارية.

## تثبيت & تكوين

### PKP PN Criteria

من أجل استخدام PKP PN، يجب أن تحتوي جريدتك على ما يلي:

* نسخة متوافقة من OJS - OJS 3.1.2 أو أحدث
* ISSN
* نشر مقالة واحدة على الأقل

لتهيئة الإضافة، سوف تحتاج إلى تسجيل الدخول كمسؤول

### تثبيت & الترقية

1. الذهاب إلى الإعدادات > الموقع > إضافة > معرض الإضافات
2. للمستخدمين الجدد، سوف تحتاج إلى تثبيت الإضافة.
3. للمستخدمين الذين استخدموا PKP في الماضي، قد يتطلب منك تحديث الإضافة؛ إذا كان الأمر كذلك، ابحث عن الإضافة على صفحة معرض الإضافات وانقر على تحديث.
4. للتثبيت اليدوي والتكوين لملحق PKP ، يرجى الرجوع إلى [GitHub README](https://github.com/pkp/pln).
5. بمجرد أن يتم تحديث أو تمكين الإضافة، انقر فوق الإعدادات لمراجعة وقبول شروط الاستخدام. سيتم ملء معرف اليومية تلقائيا.
6. انقر حفظ

![صورة شاشة إضافة PN PKP مع شروط استخدام خانات الاختيار مملوءة بحقل معرف اليومية المأهول تلقائياً، وزر الحفظ](./assets/pkp-pn-terms.png)

## استخدام الإضافة

بمجرد التمكين، سيقوم البرنامج المساعد تلقائياً بإيداع محتوى المجلة المنشور في PKP PN في كل مرة يتم فيها نشر مشكلة. هذه هي عملية الإيداع التلقائية:

1. ويأتي هذا الإيداع بسبب نشر عدد من المنشورات. سوف يكون هذا مبني على مجموعة المهام المجدولة مع الفاصل الافتراضي هو 24 ساعة.
2. ثم يتم نقل الإيداع إلى خادم التجهيز الخاص بالشبكة، حيث يتم التحقق من محتوياتها، والتحقق من الفيروسات، وما إلى ذلك.
3. ثم يتم نقل الإيداع من خادم التجهيز إلى شبكة LOCKS.
4. عندما يثبت أن جميع النسخ الموجودة على شبكة LOCKSS متطابقة، تحذف الصحيفة الإيداع من أجل حفظ مساحة التخزين.

سيبدأ البرنامج المساعد PKP محتوى التغليف الذي سيتم إيداعه في غضون 24 ساعة إلى 48 ساعة من التكوين ونشر الإصدار الجديد. ولكن سيستغرق الأمر بضعة أيام ليمر خلال الدورة بأكملها.

البرنامج المساعد PKP لا يدعم حاليا إيداع مقالات منفردة غير مسندة لمشكلة. ستتحقق الإضافة من أي تغييرات أو تحديثات (بعد إنشاء الإيداع). وإذا حدث تغيير في مادة مودعة أو أُسندت مادة جديدة إلى مسألة مودعة، تقوم الإضافة بإعادة تعيين الإيداع تلقائياً بحيث يتم إعادة إيداع هذه المشكلة في المرة القادمة التي يتم فيها تنفيذ "المودع".

### Reset

خيار إعادة التعيين لإيداع المشكلة سيتم إعادة حزمة وإرسال الملفات إلى خادم التجهيز لإعادة المعالجة. ويمكن القيام بذلك إذا كان هناك خطأ مشار إليه.

## الحالة

### التحقق من الحالة في OJS

للتحقق من حالة البرنامج المساعد PKP PN ، انقر فوق السهم الأزرق بجانب عنوان البرنامج المساعد الذي يتبعه الحال.

![تم توسيع صورة قائمة إضافات PKP على شاشة معرض الإضافات، مع سهم يشير إلى رابط الحالة](./assets/pkp-pn-status-button.png)

الشئ الرئيسي للبحث عنه في صفحة حالة PKP هو عمود حالة LOCKS. إذا تم الحفاظ على المشكلة بنجاح، فإن حالة LOCKSS سوف تشير إلى "اتفاق****، بمعنى أن الشبكة بأكملها توافق على أن هناك نسخة متسقة من المشكلة المؤرشفة.

قائمة الحالة سوف تحدد النوع، نوع معرف الكائن، عدد العناصر التي تم التحقق منها، ومختلف الحالات.

![صورة لشاشة حالة البرنامج المساعد PN PKP تظهر معلمات حالة LOCKSS لعدة مشكلات](./assets/pkp-pn-status-menu.png)

* **المعرف**: معرف قاعدة البيانات الداخلية للإيداع.
* **النوع**: سواء كان الإيداع مشكلة أو مقالة. وفي الوقت الحاضر، لا توجد سوى مسائل يجري حلها. يتم تصدير كل عدد وتخزينه كحقيبة مضغوطة. ولدى الحقيبة معلومات عن المجلة (عنوان المجلة، ISSN، وما إلى ذلك) ومعلومات عن حقوق التأليف والنشر والترخيص بشأن كل مقالة من المقالات في هذه القضية.
* **تم التحقق**: التاريخ الذي قام فيه البرنامج المساعد للمجلة مؤخرا بالتحقق من حالة الإيداع في خادم التجهيز. بمجرد اكتمال الإيداع وتوصل جميع العقد في شبكة LOCKSS إلى اتفاق، سيتوقف البرنامج المساعد عن التحقق من حالته.

الأعمدة الرئيسية التي تريد النظر فيها هي:

* **الحالة المحلية** تشير إلى حالة تثبيت OJS في التغليف ونقل كل مشكلة إلى خادم التجهيز.
  * **جديد**: الملحق على علم بالإيداع، ولكن لم ينشئ ملف حزمة لخادم التجهيز.
  * **حزمة**: تم إنشاء ملف الحزمة. لم يتم إبلاغ خادم التجهيز بالإيداع.
  * **تم نقل**: تم إرسال الإيداع إلى خادم التجهيز لمزيد من المعالجة والتحقق.
* **حالة المعالجة** تشير إلى حالة كل مشكلة في التدبير المنزلي على خادم التجهيز.
  * **استلم**: خادم التجهيز قام بتنزيل ملف الإيداع من المجلة.
  * **تم التحقق من صحتها**: تم التحقق من صحة الحزمة ومسحها للفيروسات وهي الآن جاهزة للإرسال إلى شبكة LOCKS.
  * **المرسل**: خادم التجهيز قد أبلغ شبكة LOCKSS أن الإيداع جاهز.
* **حالة LOCKSS** تشير إلى حالة كل مشكلة بمجرد إرسالها بنجاح إلى شبكة LOCKS.
  * **استلم**: شبكة LOCKSS أقرت بالإيداع.
  * **المزامنة**: العقد على شبكة LOCKSS تقوم بتنزيل الايداع والتحقق منه.
  * **الاتفاق**: العقد الموجودة على شبكة LOCKSS قد تأكدت من أن جميعها لديها نسخة من الإيداع.

ويقدم الرسم البياني الوارد أدناه موجزا مرئيا لعملية الإيداع.

![مخطط سير العمل لـ PKP](./assets/pkp-pn-status-chart.png)

*وستتاح معلومات إضافية بشأن حالة الإيداع والأخطاء عند إصدار نشرة OJS 3-3.*

### التحقق من الحالة على قائمة PKP PN Journal

بالإضافة إلى التحقق من حالة البرنامج المساعد PKP ، يمكنك أيضًا التحقق من [قائمة مشكلات المجلات](http://pkp.sfu.ca/files/pkppn/onix.csv). يتم تحديث هذه القائمة ليلاً.

### التحقق من الحالة على المفاتيح

للتحقق من حالة الأرشيف الخاصة بك خارجيا، يرجى زيارة [سجل Keepers](https://keepers.issn.org/). باستخدام وظيفة البحث، أدخل ISSN أو عنوان المجلة. انقر فوق علامة التبويب حالة الأرشيف تحت اسم اليومية.

يرجى ملاحظة أن سجل Keepers يقوم باستكمال بيانات حيازاته من PKP شهرياً.

![صورة تظهر سجل سائقي](./assets/pkp-pn-keepers-registry.png)

## استكشاف الأخطاء

### لقد قمت بتمكين البرنامج المساعد ولا تظهر شروط الاستخدام بعد النقر فوق التحديث

![صورة لمثال على شروط الاستخدام التي لا تظهر في شاشة إعداد PKP PN.](./assets/pkp-pn-refresh-terms.png)

تحقق من أنه تم إدخال ISSN في [إعدادات Journal](https://docs.pkp.sfu.ca/learning-ojs/en/journal-setup#masthead) الخاص بك. بمجرد أن تصبح هذه المعلومات في جريدتك، سوف تدرج شروط الاستخدام.

### لا تزال حالة البرنامج المساعد تعرض "حالة الشبكة: PKP PLN لا تعرف عن هذه الصحيفة حتى الآن." ولا توجد مشاكل مدرجة تحت الودائع

يرجى الملاحظة، قد يستغرق الأمر بعض الوقت حتى يتمكن LOCKSS من مزامنة الإيداع عبر جميع المخبآت في الشبكة.

إذا استمرت الرسالة لأكثر من 24 ساعة، ربما لم تقم بإعداد كرون بشكل صحيح. يمكن أن تكون الأسباب الأخرى تثبيت OJS القديم، مشكلة في الاتصال بخادم التجهيز، أو خادم التجهيز الذي لا يصل إلى المجلة بشكل صحيح.

إذا كنت لا تزال تواجه هذه المشكلة، يرجى الاتصال بخدمات النشر PKP إذا كنت أحد العملاء المستضافين. للمجلات التي تستضيف ذاتياً، يرجى إنشاء مشاركة على [منتدى مجتمع PKP](https://forum.pkp.sfu.ca/) وإدراج عنوان المجلة و عنوان URL.

![الصورة التي تظهر شاشة حالة الملحق تظهر PKP PLN لا تعرف عن هذه الصحيفة حتى الآن. خطأ](./assets/pkp-pn-unknown-journal.png)

### تشير حالة LOCKSS إلى أنها متفقة، ولكني لا أستطيع أن أرى جريدتنا على Keepers أو على قائمة PKN Journal

[قائمة PN Journal في PKP](http://pkp.sfu.ca/files/pkppn/onix.csv) يتم تحديثها كل يوم بينما يقوم سجل Keepers بتحديث بيانات حيازاته من PKP كل شهر. إذا كنت تعتقد أن المجلة الخاصة بك يجب أن تكون مدرجة على أساس هذه الأطر الزمنية، يرجى الاتصال بخدمات النشر PKP إذا كنت أحد العملاء المستضافين. للمجلات التي تستضيف ذاتياً، يرجى إنشاء مشاركة على [منتدى مجتمع PKP](https://forum.pkp.sfu.ca/) وإدراج مجلتك UUID أو URL.

### تلميحات استكشاف الأخطاء

بالنسبة للمستعملين ذوي المعارف التقنية هناك عدد من تلميحات استكشاف الأخطاء المتاحة في صفحة [PKP PN GitHub](https://github.com/pkp/pln) إذا واجهت أي مشاكل مع التغليف و إيداع المحتوى.