# مصادقة المستخدم و تسجيل الدخول الفردي

لمزامنة حسابات المستخدم عبر تطبيقات متعددة، يدعم OJS و OCS LDAP و Shibboleth، وكلاهما يحظى بدرجات متفاوتة من الدعم في التطبيقات الأخرى، بما في ذلك نظام دكتوراه في البكالوريوس (Drupal) ونظام ووردبرس (DordPress)، ونظم إدارة المحتوى الأخرى.

*LDAP* (بروتوكول الوصول إلى الدليل الخفيف)، في حين أنه ليس قوي مثل Shibboleth (على سبيل المثال LDAP لا يدعم تسجيل الدخول الفردي، حيث يتم تسجيل الدخول إلى إحدى الخدمات تلقائياً إلى كل خدمة أخرى)، هو خيار شائع لإضفاء الطابع المركزي على المصادقة على خادم. تطبيق LDAP الشهير هو [OpenLDAP](https://www.openldap.org/) تنفيذ مفتوح المصدر للبروتوكول.

*Shibboleth* هو بديل قوي لـ LDAP لإدارة المستخدم والتوثيق، وقد نمت شعبيته. يوفر Shibboleth قدرات مزامنة الحساب لـ LDAP فضلا عن وظائف تسجيل الدخول الأحادي (حيث تسجيل الدخول إلى إحدى الخدمات تلقائيا يسجل في جميع الخدمات)، توفير تكامل أكثر سلاسة بين تطبيقات الويب الخاصة بك. ومع ذلك، يمكن أن يكون شيبوليث أكثر تعقيدا للتثبيت والتكوين من LDAP.

## إعداد LDAP
إنشاء خادم LDAP خارج نطاق هذا الدليل، ولكن يرجى الرجوع إلى قسم الموارد للحصول على دليلين مفيدين يساعدان في الإعداد ومصدر LDAP. وبالمثل، يرجى الرجوع إلى الوثائق الخاصة بتطبيقاتك الأخرى على الإنترنت للمساعدة في الاندماج في LDAP.

لإعداد LDAP في OJS و OCS، قم بتسجيل الدخول كمدير الموقع، وتحت 'إدارة الموقع' على الصفحة الرئيسية للمسؤول ، انقر فوق 'مصادقة المصادقة'. تحت 'إنشاء مصدر المصادقة', حدد 'LDAP' وانقر فوق 'إنشاء'. سيؤدي هذا إلى إثارة صفحة إعدادات LDAP.

![](./assets/LdapAuthSources.png)

*تحذير*: يرجى ملاحظة أن البرنامج المساعد LDAP لا يشحن مع OCS بشكل افتراضي -- سيتعين عليك استلامه من إصدار حديث من OJS (أو من CVS). يمكن العثور على مزيد من المعلومات [هنا](http://pkp.sfu.ca/bugzilla/show_bug.cgi?id=2960).

عنوان إعداد LDAP الخاص بك تعسفي؛ اتركه كما هو أو اختر عنوانك الخاص. الإعدادات الثلاثة التالية تقوم بتخصيص مستوى التكامل بين OJS/OCS وخادم LDAP الخاص بك.

* *تمكين مزامنة الملف الشخصي للمستخدم*. إذا تم تحديده، معلومات المستخدم بما في ذلك كلمات المرور، الاسم، عنوان البريد الإلكتروني، سيتم مزامنة رقم الهاتف والبيانات الشخصية الأخرى تلقائيًا بين مصدر LDAP و OJS/OCS، مما يسمح بملف تعريف متسق للمستخدم عبر التطبيقات.
* *تمكين تعديل كلمة مرور المستخدم*. إذا تم تحديده، يسمح للمستخدمين بتغيير كلمة المرور الخاصة بهم واستعادة كلمات المرور المفقودة.
* *تمكين إنشاء المستخدم*. إذا تم تحديده، سيتم إضافة أي مستخدم تم إنشاؤه داخل OJS/OCS تلقائيًا إلى مصدر LDAP.

المجموعة التالية من الإعدادات تكوينات OJS/OCS للسماح بالاتصال مع خادم LDAP.

![](./assets/LdapSettings.png)

* *اسم مضيف الخادم*. النطاق/عنوان IP للخادم الذي يستضيف مصدر LDAP. إذا كان OJS/OCS يعمل على نفس الخادم مثل LDAP ، فيمكنك إدخال `localhost`.
* *منفذ الخادم*. إذا كان LDAP يعمل على منفذ غير قياسي، أدخل الرقم هنا. اتركه فارغاً إذا لم تكن متأكداً.
* *قاعدة DN*. هذا هو المكان الذي تصبح فيه معقدة قليلا. LDAP مصمم مثل شجرة الدليل، مثل نظام ملفات الكمبيوتر الخاص بك. لتحديد إدخال الدليل للبحث عن المستخدمين، يتطلب البرنامج المساعد LDAP قاعدة DN أو 'اسم متميز' لبدء البحث. في المثال المقدم، `ou=people,dc=example,dc=com`، 'ou' (أو 'Organization Unit') تعني المجموعة الرئيسية للمستخدمين، الذي يجب أن تكون قادراً على تحديده من ملفات تكوين مصدر LDAP الخاص بك. وبالمثل، يجب أن يكون 'dc' (أو 'مكون النطاق') تحت 'لاحق' في ملف تكوين مصدر LDAP الخاص بك. كل مكون نطاق يعني مكون اسم النطاق الخاص بك (على سبيل المثال.com يحتوي على مكوني النطاق 'مثال' و 'com'. إذا كنت تستخدم المضيف المحلي، استخدم `dc=localhost,dc=localdomain`.
* *مدير DN*. مثل قاعدة DN، ولكن هذا الإعداد مطلوب لكي تتواصل المكون الإضافي مع مصدر LDAP كمدير ، i. - إجراء تغييرات إدارية. يجب أن تكون مكونات النطاق هي نفس DN، ولكن cn (أو 'اسم مشترك`، أي الاسم المستعار للمستخدم الجذر يجب أن يكون 'مدير' أو أي شيء تم تعيينه في تكوين خادم LDAP الخاص بك.
* *سمة اسم الحساب*. هذه القيمة تحدد بشكل فريد كائن المستخدم، ويجب أن تكون 'uid' لـ OpenLDAP ، ولكن قد تكون مختلفة بالنسبة لمصادر LDAP الأخرى (e). .، سيكون SAMAccountName لـ Microsoft Active Guide).
* *كلمة مرور المدير*. كلمة المرور لحساب المدير (مطلوبة فقط إذا تم تمكين مزامنة ملف تعريف المستخدم/كلمة المرور أو خيارات إنشاء المستخدم).
* *تشفير كلمة المرور*. لأسباب أمنية، من المستحسن أن تستخدم شكلا ما من أشكال تشفير كلمة المرور. إذا كان لديك PHP الإصدار 4.3.0 أو أكثر، نقترح استخدام SSHA.

اختياري، إذا كان PHP الإصدار 5.0 أو أكثر، يمكنك تكوين LDAP لاستخدام SASL (المصادقة الوسيطة وطبقة الأمن) للمصادقة. بما أن هذه الميزة للمستخدمين المتقدمين، يرجى الرجوع إلى الروابط في قسم الموارد للحصول على مزيد من المعلومات.

## إعداد Chbboleth

*ملاحظة*: يرجى ملاحظة أن دعم شيبوليث لم يتم ترحيله بعد إلى OCS.

يتم صيانة شيبوليث بواسطة [مبادرة الإنترنت 2 Middleware Initi](http://shibboleth.internet2.edu/)، وعلى هذا النحو يوفر موقعهم الشبكي موقعا مركزيا للتنزيلات والوثائق. وهي توفر حاليا مزود خدمة شيبوليث رقم 2.1 في شكل ثنائي لجميع نظم التشغيل الرئيسية، فضلا عن توفير شفرة المصدر. وللحصول على مزيد من المعلومات عن تثبيت وإعداد مزود خدمة شيبوليث، يرجى الرجوع إلى وثائق الدعم الخاصة بشبكة إنترنت.

بمجرد إعداد Shibboleth على النظام الخاص بك، يتطلب التكامل مع تطبيق PKP الخاص بك تحرير التكوين `. ملف nc.php` موجود في الدليل الأساسي، في قسم `[security]`. المتغيرات المعنية كلها تقع تحت متغير `implicit_auth`- بدون تعليق أنه بحذف المنصة الدراسية، وعدم التعليق على جميع المتغيرات الأخرى التي تبدأ بـ `implicit_auth`. لاحظ أنه لا يتم الرجوع إلى أي من المتغيرات الضمنية الأخرى إذا تم التعليق على المتغير الرئيسي أو لم يتم تعيينه إلى 'تشغيل'. عن طريق تشغيل `implicit_auth` ، عملية تسجيل الدخول ستمر عبر شيبوليث وسيتم تعديل العديد من النماذج بحيث لا تطلب معلومات شخصية مخزنة في شيبوليث.

![](./assets/ShibbolethSettings.png)

في البداية، يتم تعيين جميع المتغيرات إلى قيم [اتحاد شيبوليث للمكتبة الرقمية في تكساس](http://www.tdl.org/shibboleth/). بما أنك على الأرجح غير منتسب إلى TDL، فسيتعين عليك تغيير القيم لتعكس إعدادات Shibboleth الخاصة بك. إذا كان طلبك جزءًا من اتحاد مؤسسي، فاستفسر عن الدعم الفني لهذه القيم. خلاف ذلك، سيتعين عليك التحقيق في ملفات التكوين في Shibboleth. هذا يمكن أن يصبح معقدا ، وهناك فرق بين المتغيرات في شيبوليث 1.x و شيبوليث 2.x. ابتداء من Shibboleth 2.0، يتم تخزين هذه القيم كمتغيرات بيئة خادم الويب، ويمكنك تحديدها من خلال البحث في خريطة السمة. ملف ml (عادة في دليل `shibboleth_dir/etc/shibboleth/` )، حيث يتم الإشارة إلى السمة من خلال السمة 'id' لكل عنصر من عناصر السمة. بشكل افتراضي، يجب أن تكون القيم `Shib-EP-[AttributeId]` حيث `[AttributeId]` هي القيمة في السمة 'id' ، مع الحرف الأول رسملة. قد تكون هذه القيم أيضًا في شكل `HTTP_SHIB_EP_[AttributeID]` مع `[AttributeID]` في جميع الأغلف.

يحتوي متغير `implicit_auth_admin_list` على قائمة من الـ UINs (عناوين البريد الإلكتروني) مفصولة بمسافات. إذا قام المستخدم بتسجيل الدخول مع أحد هذه الشبكة، فسيتم تسجيل الدخول تلقائيًا باستخدام امتيازات المسؤول. يمكن العثور على `implicit_auth_wayf_url` في `shibboleth.xml` أو `shibboleth2.xml` (اعتماداً على الإصدار الذي تستخدمه). سوف تكون موجودة في وسم `<SessionInitiator>`كسمة الرابط.

## الأسئلة المتكررة

### لا أستطيع تسجيل الدخول إلى OxS باستخدام بيانات اعتماد LDAP.

ويتمثل أحد المكونات الرئيسية لOxS في وجود سجل ثابت لنشاط المستخدمين، ولا سيما فيما يتعلق بالتقديمات والتحرير. إذا كانت سجلات المستخدم مخزنة خارج OxS، لا يوجد ضمان بأن السجل سيبقى على حوله أو سيبقى متسقا، مما يسبب مشاكل مع OxS. وبالتالي، لن تعمل بيانات اعتماد LDAP إلا إذا كان هناك مستخدم مطابق في OxS.

مع ذلك، هناك عدة طرق لجلب مستخدمي LDAP إلى قاعدة بيانات OxS الخاصة بك. إذا كنت ترغب في القيام بإغراق المستخدمين مرة واحدة في OxS ، يمكنك إنشاء ملف XML مع معلومات المستخدم لاستيراده إلى OxS (انظر إضافة XML المستخدمين). وعلاوة على ذلك، يمكن كتابة رمز لإدراج المستعملين تلقائيا في قاعدة البيانات عند تسجيلهم في تطبيق آخر. تُظهر وظيفة التنفيذ في `classes/Manager/form/UserManagementForm.inc.php` كيفية تسجيل المستخدمين في OJS، ويمكن نمذجتهم في وظائف تسجيل المستخدم في تطبيق آخر. ومن المحتمل أن يتم تنفيذ مجموعة متنوعة من الحلول الأخرى للتغلب على ذلك.

### يبدو أن OxS هاش كلمات المرور بشكل مختلف عن في LDAP. كيف أحصل على OxS للامتثال لتقنية التجزئة في LDAP؟

بشكل افتراضي، يقوم OJS و OCS بإرفاق اسم المستخدم لكلمة المرور قبل التجزئة. لتغيير هذا السلوك، قم بتعديل دالة `encryptCredentials in classes/security/Validation.inc.php`. إذا قمت بتغيير سلوك تجزئة كلمة المرور، فسيتعين عليك إعادة تعيين جميع كلمات المرور الموجودة في قاعدة البيانات.

أحصل على هذا الخطأ عند محاولة الاتصال بخادم LDAP الخاص بي: `خطأ قاتل في PHP: اتصل إلى وظيفة غير محددة ldap_connect()`

ملحق LDAP الخاص بـ PHP غير مدرج بشكل افتراضي، وقد يتعين تجميعه. راجع [دليل تثبيت PHP](http://ca.php.net/manual/en/ldap.installation.php) لمزيد من المعلومات.

## الموارد

* [HOWTO سريعة : Ch31 : تسجيلات الدخول المركزية باستخدام LDAP وRADIUS ](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch31_:_Centralized_Logins_Using_LDAP_and_RADIUS)
* [دليل المدير OpenLDAP 2.1 : استخدام SASL](https://www.openldap.org/doc/admin21/sasl.html)
* [ساتل Cyrus SASL لمديري النظام](http://www.sendmail.org/~ca/email/cyrus/sysadmin.html)
* [وثائق الشيبوليث](https://wiki.shibboleth.net/confluence/display/SP3)