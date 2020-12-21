# البريد الإلكتروني

يوضح هذا الفصل كيفية إرسال رسائل البريد الإلكتروني في OJS, OMP, وOCS؛ خيارات التكوين المتاحة؛ وكيفية استكشاف مشاكل البريد الإلكتروني.

البريد في تطبيقات برنامج PKP يستخدم [مكتبة PHPMailer](https://github.com/PHPMailer/PHPMailer). يمكنك معرفة المزيد حول PHPMailer على [ويكي](https://github.com/PHPMailer/PHPMailer/wiki) الخاص بهم. يمكن العثور على رمز آخر يتعلق بالبريد الإلكتروني في [فئة بريد pkp-lib](https://github.com/pkp/pkp-lib/tree/master/classes/mail).

سجلات رسائل البريد الإلكتروني التي يتم إرسالها مخزنة في جدول `البريد الإلكتروني _log` من قاعدة البيانات.

توفر تطبيقات برمجيات PKP عددا من الخيارات لتكوين رسائل البريد الإلكتروني للعمل في بيئتك. خيارات التكوين التالية متاحة للبريد الإلكتروني في `config.inc.php`:

```
;;;;;;;;;;;;;;;;;;
; Email Settings ;
;;;;;;;;;;;;;;;;;;

[email]

; Use SMTP for sending mail instead of mail()
; smtp = On

; SMTP server settings
; smtp_server = mail.example.com
; smtp_port = 25

; Enable SMTP authentication
; Supported mechanisms: ssl, tls
; smtp_auth = ssl
; smtp_username = username
; smtp_password = password

; Allow envelope sender to be specified
; (may not be possible with some server configurations)
; allow_envelope_sender = Off

; Default envelope sender to use if none is specified elsewhere
; default_envelope_sender = my_address@my_host.com

; Force the default envelope sender (if present)
; This is useful if setting up a site-wide no-reply address
; The reply-to field will be set with the reply-to or from address.
; force_default_envelope_sender = Off

; إجبار DMARC على الامتثال من الرأس (RFC5322). الروم)
؛ إذا كان أي من المستخدمين لديك عناوين بريد إلكتروني في النطاقات غير الخاضعة لسيطرتك
؛ قد تحتاج إلى تعيين هذا لتكون متفقة مع سياسات DMARC المنشورة بواسطة
؛ تلك النطاقات الخاصة بالطرف الثالث.
؛ سيؤدي إعداد هذا إلى نقل عنوان المستخدمين إلى حقل الرد و
؛ من حقل سلك يتم إعادة كتابته مع الافتراضي _envelope_sender.
؛ لاستخدام هذا يجب عليك تعيين force_default_enveloper_sender = التشغيل و
؛ يجب تعيين الظرف الافتراضي_المرسل إلى عنوان صالح في نطاق تملكه.
; force_dmarc_compliant_from = Off

; اسم العرض لاستخدامه مع DMARC ممتثل من رأس
; بشكل افتراضي سيكون للامتثال DMARC اسم فارغ ولكن هذا يمكن أن
؛ يمكن تغييره بإضافة نص هنا.
; يمكنك استخدام '%n' لإدراج اسم المستخدم من الأصل من رأس
; و ''%s' لإدراج اسم مكان الجلوس.
; dmarc_compliant_from_displayname = '%n عبر %s'
```

لمعرفة المزيد عن البريد الإلكتروني داخل واجهة مستخدم OJS، راجع [تعلم OJS 3](https://docs.pkp.sfu.ca/learning-ojs/en/).

## إرسال البريد

بشكل افتراضي، سيقوم PHPMailer بإرسال البريد عبر مرفق PHP المدمج في `البريد ()`.

في ويندوز، تحتاج PHP إلى تكوين لإرسال البريد الإلكتروني من خلال خادم SMTP \(تشغيل إما على نفس الجهاز أو على جهاز آخر\).

على منصات أخرى مثل Linux و Mac OS X، سيقوم PHP بإرسال البريد باستخدام عميل Sendmail المحلي، لذا يجب تشغيل وتكوين MTA المحلية مثل Sendmail أو Postfix للسماح بالبريد الصادر.

راجع [https://www.php.net/manual/en/function.mail.php](https://www.php.net/manual/en/function.mail.php) لمزيد من التفاصيل حول تكوين وظيفة البريد لـ PHP.

يمكن أيضا تكوين برنامجنا لاستخدام خادم SMTP كما هو محدد في `config.inc.php`، إما مع أو بدون مصادقة.

## تعيين عنوان الارتداد

للتحكم في العنوان الذي سيتم إرسال بريد إلكتروني مرتبط به، تحتاج إلى تعيين عنوان مرسل الظرف. تمكين خيار `allow_envelope_sender` في قسم `[email]` من ملف الإعداد؛ عند تمكين هذا الخيار، يظهر حقل "عنوان ارتداد" في قسم البريد الإلكتروني تحت الإعداد.

لاحظ أن هذا الخيار قد يتطلب تغييرات في تكوين خادم البريد الخاص بالخادم بحيث يعمل المستخدم خادم الويب كـ \(e. . "www-data"\) موثوق به من قبل برنامج sendmail؛ وإلا سيتم إضافة رأس "X-Warning" إلى الرسائل الصادرة. اطلع على وثائق خادم البريد الخاص بك إذا كانت الرسائل الصادرة تتضمن مثل هذا الرأس.

على سبيل المثال، Sendmail يحتفظ بقائمة من المستخدمين الموثوق بهم في `/ etc/mail/trusted-users`؛ أنظمة البريد الأخرى تستخدم ملفات مماثلة.

خيار سطر الأوامر المستخدم لتعيين مرسل الظرف هو `-f`.

## البريد الإلكتروني واللغة المحلية

يتم تثبيت قوالب البريد الإلكتروني مباشرة في قاعدة البيانات عند إنشاء مجلة أو صحافة أو مؤتمر. إذا كنت بحاجة إلى تحرير [ملف محلي](https://github.com/pkp/ojs/blob/stable-3_1_2/locale/en_US/emailTemplates.xml)، لن يظهر أي تغيير في ملف القالب الخاص بك حتى تقوم بإعادة تحميل جميع القوالب في النظام.

إعادة تحميل القوالب سوف تتجاوز أي تعديلات قد تكون قمت بها. للحفاظ على هذه التعديلات، سوف تحتاج إلى حفظ هذه التعديلات محليا وإعادة إضافتها إلى القوالب حسب الاقتضاء.

## الاتصالات الأولية والتقنية

تتطلب جميع تطبيقات PKP أن يتم تكوين جهات الاتصال الأساسية والتقنية تحت الإعداد للعمليات اليومية المناسبة. وهذا مطلوب لكل صحيفة أو صحافة أو مؤتمر في المنظومة.

- في OJS 2.x، يمكن القيام بذلك تحت _إعداد الخطوة 1_.
- في OCS 2.x، يمكن القيام بذلك تحت _إدارة موقع الويب الخطوة 1_.
- في OJS/OMP 3.x، يمكن القيام بذلك تحت _إعدادات &gt; يومية &gt; جهة الاتصال_.

## التحقق من البريد الإلكتروني للمستخدمين الجدد

يوفر OJS نموذج تسجيل ذاتي لجميع المستخدمين الذين يمكن تعطيلهم أو إعادة تمكينهم تحت _قائمة المشرف > المستخدم & الأدوار > خيارات الوصول إلى الموقع > تسجيل المستخدم_

حالما يتم تمكين ذلك، كل مستخدم قادر على التسجيل وإنشاء حساب في اليومية له دور كقارئ أو مؤلف و/أو مراجع؛ ومع ذلك، ليس من غير المألوف للمستخدمين إنشاء حسابات غير مرغوب فيها التي ستكشف قائمة المستخدمين الشرعيين وتزيد من عبء العمل على محرري اليومية للتحقق من هذه الحسابات وتنظيفها يدويا.

يمكن تقليل إنشاء حساب البريد المزعج الشامل مع إعدادات في `config.inc.php`:

```
؛ إذا تم تمكينه، يجب التحقق من صحة عناوين البريد الإلكتروني قبل تسجيل الدخول ممكن.
المطلوب_المصادقة = إيقاف

؛ الحد الأقصى لعدد الأيام قبل انتهاء صلاحية الحساب غير المصدق عليه وحذف
المصادقة = 14
```

المعلمة الأولى هي `require_validation`، التي تم تعيينها إلى `إيقاف` بشكل افتراضي. عند التعيين إلى `في`، سيتطلب هذا المعلمة أن يقوم كل مستخدم جديد بتنشيط حسابه قبل أن يكون قادرا على استخدام النظام بشكل كامل.

المعلمة الثانية هي `validation_timeout`، التي تم تعيينها إلى `14` بشكل افتراضي. يعمل هذا المعلم فقط عندما يتم تمكين `require_validation` ، ويعني أن المستخدم لديه 14 يوما لتفعيل حسابه الجديد أو سيتم إزالة الحساب من النظام تلقائيا عند بلوغ الحد الزمني.

## تكوين النظام لاستخدام Gmail SMTP

لاستخدام Gmail SMTP لإرسال البريد الإلكتروني من OJS، يمكنك استخدام الإعدادات التالية في `config.inc.php`.

لـ OJS 2.x:

```
; استخدم SMTP لإرسال البريد بدلا من البريد()
smtp = على

; إعدادات خادم SMTP
smtp_server = "ssl://smtp.gmail. om"
smtp_port = 465

; تمكين مصادقة SMTP
smtp_auth = PLAIN
smtp_username = "user@gmail.com"
smtp_password = "كلمة المرور"
```

لـ OJS 3.x:

```
; استخدم SMTP لإرسال البريد بدلا من البريد()
smtp = على

; إعدادات خادم SMTP
smtp_server = smtp.gmail. om
smtp_port = 465

; تمكين مصادقة SMTP
smtp_auth = ssl
smtp_username = "user@gmail.com"
smtp_password = "كلمة المرور"
```

تتوفر معلومات إضافية حول Gmail SMTP على [https://support.google.com/a/answer/176600?hl=en](https://support.google.com/a/answer/176600?hl=en).

لاحظ أنه قد يتعين عليك إضافة إلى ذلك تكوين كلمات المرور الخاصة بالتطبيقات في Gmail؛ انظر [https://support.google.com/accounts/answer/185833?hl=en](https://support.google.com/accounts/answer/185833?hl=en) للحصول على التفاصيل.

## المسائل المتعلقة بالمنتدى الخاص المعني بإدارة مصائد الأسماك

### إطار سياسة المرسل

ويعتمد إطار سياسة المرسل على الإذن الذي يتلقاه الخادم، الذي قد يكون قيد تشغيل OJS، من خادم آخر يستضيف النطاق الرئيسي. هذا يأذن لخادم OJS بإرسال رسائل البريد الإلكتروني باستخدام ذلك النطاق ويمنع الرسائل من حظرها.

SPF مطلوب عندما يعمل تثبيت OJS الخاص بك على خادم مختلف، بما في ذلك نطاق فرعي، من النطاق الرئيسي الخاص بك؛ على سبيل المثال عندما تستضيف مجلة في المجلة. omain.com على خادم يقع خارج المؤسسة التي تستضيف domain.com.

في هذه الحالة، يجب عليك أن تطلب من موظفي خدمات تكنولوجيا المعلومات تمكين إدخال TXT في منطقة DNS الخاصة بك، الذي يمنح إرسال رسائل البريد الإلكتروني والإشعارات نيابة عن @domain. أم. وفيما يلي مثال لسيناريو محتمل يتطلب سجلا للصندوق الخاص الخاص للأمين العام:

الخادم قيد التشغيل OJS:

```
IP: 10.10.10
اسم الخادم: myojsserver.com (هذا ليس نطاقك، ولكن فقط اسم خادم يعرفه بائع مضيف OJS الخاص بك)
```

سيحتاج هذا الخادم إلى إدراجه في منطقة DNS الخاصة بك كسجل TXT SPF. وفي هذه الحالة، ستحتاج إلى إضافة ما يلي:

```
الاسم: فارغ، أو تعيين إلى @ (اعتمادا على تعليمات مسجل النطاق الخاص بك)
نوع: TXT
القيمة: v=spf1 ip4:10.10.10.10 a:myojsserver.com ~كل
```

إذا كان لديك بالفعل سجل TXT في منطقة DNS الخاصة بك، فستحتاج إلى دمجه للحفاظ على سجل TXT واحد فقط. يجب أن يكون هناك فقط سجل DNS TXT واحد.

### المصادقة على الرسائل المستندة إلى النطاق والإبلاغ عنها والتوافق (DMARC)

في حين يوفر SPF النص لOJS لإرسال رسائل البريد الإلكتروني باستخدام مسار الإرجاع أو ظرف البريد الإلكتروني الذي يحتوي على عنوان بريد إلكتروني مع نطاق آخر غير ذلك الذي يستضيفه خادم OJS، هناك أوقات قد يقوم فيها OJS بإرسال بريد إلكتروني نيابة عن المستخدمين الذين يستخدمون نطاقات لا يمكنك استرجاع سجل SPF لها. Gmail مثال جيد: إذا كان للمشرف `user@gmail. om` عنوان لا توجد طريقة لجعل جوجل تضيفنا كسجل SPF

DMARC يحل هذا عن طريق وضع البريد الإلكتروني للمستخدم في `الرد على:` عنوان، ووضع `default_envelope_sender` في `من:` الحقل. ابتداء من OJS 3.1.2، يمكنك تكوين هذا عن طريق معلمين جديدين في `config.inc. hp` ملف ، على وجه التحديد `force_dmarc_compliant_from` و `dmarc_compliant_from_displayname`. (إذا كنت على OJS 3.1.2+ ولا ترى هذه المعلمات في ملف التكوين المباشر، فأنت تريد مراجعة التكوين `الخاص بك. ملف EMPLATE.inc.php` ونقله كما يظهر هناك.)

## مشاكل في استكشاف البريد الإلكتروني

إذا لم يتم استلام رسائل البريد الإلكتروني من قبل بعض المستخدمين، أول شيء يفعله هو التحقق لمعرفة ما إذا كنت بنفسك تستطيع تلقي البريد الإلكتروني. حاول إرسال بريد إلكتروني لنفسك باستخدام النظام. إذا تلقتها، فإن تطبيق البرنامج ربما يرسل البريد الإلكتروني بشكل جيد. يجب عليك بعد ذلك أن تطلب من المستخدم الذي لديه مشكلة التحقق من مجلدات البريد الإلكتروني غير المرغوب فيها/غير المرغوب فيه.

إذا لم يتمكن المستخدم من العثور على أي سجل للبريد الإلكتروني يتم تصفيته كالبريد المزعج أو غير المرغوب فيه، قد تواجه مشكلة التحقق من صحة **إطار سياسة المرسل** \(SPF\) مع الخادم الخاص بهم. يمكنك تأكيد ذلك من خلال عرض سجل البريد الخاص بالخادم الخاص بك لمعرفة ما إذا كان هناك أي حالات حظر إيصال/إرجاع تم الإبلاغ عنها مع أخطاء التحقق من SPF كنتيجة.

### التوضيح والحل

في النسخة 2.4.6، قام OJS بتغيير طريقة إرسال رسائل البريد الإلكتروني. في السابق، تم إرسال جميع رسائل البريد الإلكتروني باستخدام عنوان البريد الإلكتروني للمستخدم OJS في حقل "FROM". وأدى هذا لسوء الحظ إلى بعض المشكلات مع وضع علامة على رسائل البريد الإلكتروني الصادرة كـ "مثبت" من قبل بعض خوادم البريد الإلكتروني لأن عناوين البريد الإلكتروني في السؤال \(مثلا. james@myinstitution.org"\) لم يتطابق اسم النطاق للخادم الذي يرسل البريد الإلكتروني \(مثلاً: "myjournal.com"\). \(تقنياً، رسائل البريد الإلكتروني كانت فشل في التحقق من إطار سياسة المرسل \(SPF\). وهذه الطريقة هي أكثر خطورة من اعتبارها غير مرغوب فيها: في كثير من الحالات، لن يقوم حتى خادم البريد الإلكتروني المستلم بتعيين البريد الإلكتروني إلى قائمة انتظار البريد غير المرغوب فيها/غير المرغوب فيه، بدلا من ذلك ببساطة اختيار تجاهل هذا البريد الإلكتروني.

#### الحل 1 \(OMP, OJS\):

لمنع حدوث ذلك، اعتمد فريق تطوير PKP طريقة إشعار بالبريد الإلكتروني مشابهة لتطبيقات الويب الأخرى مثل WordPress: إرسال جميع البريد الإلكتروني من النظام باستخدام عنوان بريد إلكتروني مركزي واحد في حقل "FROM". مع عناوين البريد الإلكتروني للمستلمين المستهدفين في حقل "REPLY-TO". عنوان البريد الإلكتروني المركزي الذي سيتم استخدامه بشكل افتراضي هو الذي يتم توفيره في **إعداد مجلة الخطوة 1. : جهة الاتصال الرئيسية**، التي يجب أن تتطابق مع اسم النطاق الذي ترسل منه المجلة البريد. \(إذا كان عنوان البريد الإلكتروني هذا لا يمكن أن يتطابق مع النطاق المرسل على أساس كل يومة، يمكن تكوين عنوان بريد إلكتروني بديل على مستوى الموقع من خلال تكوين OJS. nc.php ملف\). بالإضافة إلى ذلك، تم توفير إعداد جديد "عنوان البريد الإلكتروني" في **إعداد اليومية الخطوة 1. : تعريف البريد الإلكتروني**، الذي يمكن استخدامه لتقديم نص تفسيري للمستلم.

ولتشكيل ذلك على نحو سليم، نقترح ما يلي:

* إذا لم تكن على OJS 2.4.6+ بالفعل، قم بالترقية.
* تكوين عنوان البريد الإلكتروني الذي سيستخدمه OJS لإرسال جميع البريد الإلكتروني باستخدام إعداد "جهة الاتصال الرئيسية" في إعداد اليومية خطوة 1.2
  * إذا كان ممكنا على الإطلاق، فهل يعمل عنوان البريد الإلكتروني الرئيسي لجهة الاتصال الخاصة بك كنقطة اتصال عامة لليومية، وجعلها تتطابق مع اسم نطاق المجلة. على سبيل المثال، إذا كان اسم المجال الخاص بك هو "افتراض"، حاول استخدام عنوان البريد الإلكتروني مثل "editor@hypothesisjournal.com".
* قدم بعض النص التوضيحي باستخدام إعداد "عنوان البريد الإلكتروني" في إعداد اليومية خطوة 1.4. سيظهر هذا النص في الجزء العلوي من كل بريد إلكتروني تم إنشاؤه بواسطة النظام. تذكر أن رسائل البريد الإلكتروني هذه هي عادة إشعارات للمستخدمين، ويجب أن تعامل مثل رسائل البريد الإلكتروني للإشعارات من أنظمة أخرى. ونوصي بالنص التالي:

```
أنت تتلقى هذا البريد الإلكتروني نيابة عن <journal-name>. في حالة الرد المطلوب، يمكنك الرد مباشرة على هذا البريد الإلكتروني.
```

#### الحل 2 \(OCS, ولكن أيضًا OJS و OMP\):

تكوين التثبيت الخاص بك لاستخدام خدمة SMTP لـ GMail. راجع [القسم أعلاه على SMTP](#Sender-Policy-Framework-(SPF)) لمزيد من المعلومات.