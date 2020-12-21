# توصيات التكوين لامتثال GDPR

وستوفر الممارسات التالية مستوى أعلى من الدعم لخصوصية البيانات، ويوصى بها كجزء من محاولة معقولة للوفاء بمتطلبات قاعدة البيانات الديموغرافية والاقتصادية.

**استخدم SSL/HTTPS لجميع حركة مرور الويب.** يمكن استخدام OJS و OMP بالاقتران مع شهادة SSL بحيث يتم تشفير جميع حركة المرور بين المستخدم والخادم ونقلها عبر [HTTPS](https://en.wikipedia.org/wiki/HTTPS). من أجل تمكين ذلك، قم بتثبيت شهادة SSL للنطاق الخاص بك (أو اطلب من مزود الخدمة القيام بذلك) وتعيين "force_ssl" إلى "تشغيل" في الإعدادات الخاصة بك. ملف nc.php

**تعطيل استخدام CDN.** [شبكات توصيل المحتوى](https://en.wikipedia.org/wiki/Content_delivery_network) (CDNs) تستخدم من قبل OJS و OMP لتسليم بعض المحتوى، بما في ذلك جافا سكريبت والخطوط. ويمكن لأي شبكة CDN تسجيل وتتبع معلومات الزوار المفصلة كلما تم تحميلها بواسطة متصفح الويب، بما في ذلك الوقت؛ عنوان IP المستخدم؛ متصفح الويب؛ والصفحة محملة. يمكن تعطيل CDNs في config.inc.php عن طريق تعيين "enable_cdn" إلى "إيقاف". (ملاحظة: لن يؤدي ذلك بالضرورة إلى تعطيل الناموسيات المدمجة التي تضاف إلى النظام بطرق أخرى) مثل عن طريق تخصيصات البرمجة، أو عن طريق إضافات طرف ثالث، أو في الحقول النموذجية.)

**تقييد استخدام البرامج النصية الأخرى لطرف ثالث.** لا ينبغي استخدام البرامج النصية لطرف ثالث، مثل Google Analytics، إلا إذا كان التطبيق مطلوبا وكانت الآثار مفهومة. وينبغي تحديد استخدام هذه البرامج النصية بشكل سليم في بيان الخصوصية.

**إخفاء هوية بيانات الاستخدام.** لكل من OJS و OMP إضافة إحصائيات الاستخدام التي توفر مقاييس مفصلة على مشاهدات الصفحات وتحميلات ملفات Galley. كما أنها تنشئ وتخزن ملفات سجل تحتوي على معلومات مفصلة بما في ذلك عنوان IP والتاريخ والوقت الذي تمت زيارته، ومشاهدات الصفحات ومعلومات المتصفح. هذا البرنامج المساعد يحتوي على خيار "احترام خصوصية البيانات" الذي سيقوم بتجزئة عناوين IP، وإبلاغ الزوار بأنه يجري تتبع هذه البيانات (مع خيار عدم التطبيق). ويمكن الحصول على مزيد من المعلومات في المواقع التالية:

* OJS 2: إدارة اليومية > إضافات النظام > إضافات عامة > إضافة إحصائيات الاستخدام > الإعدادات.
* OJS/OMP 3: الإعدادات > الموقع > الإضافات > الإضافات العامة > إضافة إحصائيات الاستخدام > الإعدادات.

وسيتطلب تمكين خيار "احترام خصوصية البيانات" مساعدة مباشرة لمدير النظام.

**استخدم البرنامج المساعد الشريف للمشاركة/وسائل التواصل الاجتماعي.** منصات التواصل الاجتماعي مثل تويتر وفيسبوك كلها توفر طرق لتضمين خيارات المشاركة وغيرها من الميزات الاجتماعية في مواقعك، ولكن مشابهة لخيارات سكريبت CDNs وغيرها من خيارات سكريبت طرف ثالث، هذه البرامج النصية المدمجة تسمح عادة لمنصة وسائل الإعلام الاجتماعية بتعقب استخدام موقعك. [OJS-de](http://www.ojs-de.net)، شبكة مستخدم OJS الألمانية، قام بتطوير [ملحق](https://github.com/ojsde/shariff) لتوفير وسائل التواصل الاجتماعي ومشاركة الوظائف باستخدام [حل شرف مع احترام الخصوصية](https://github.com/heiseonline/shariff). متاح هنا، لOJS 2 و 3، و OMP 3: [https://github.com/ojsde/shariff/releasases](https://github.com/ojsde/shariff/releases).