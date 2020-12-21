# التسجيل التلقائي باستخدام mEDRA/DataCite

هذه الفقرة لا تكون ذات صلة إلا إذا قررتِ تسجيل المؤسسات الرسمية مباشرة من داخل مكتب خدمات الرقابة الداخلية. ويلزم الوصول إلى حساب لدى وكالة التسجيل.

## تطبيق على حساب mEDRA/DataCite الخاص بك

كمدير يومية يرجى الانتقال إلى الصفحة الرئيسية لموصل الوكالة:

- لـ mEDRA: استيراد / تصدير البيانات &gt; mEDRA للتصدير/التسجيل المساعد
- لبيانات Cite: استيراد/تصدير البيانات &gt; تصدير/تسجيل البيانات Cite

هناك ستجد إشعارا تمهيديا قصيرا حول كيفية التقدم بطلب حساب التسجيل الخاص بك. يرجى اتباع الإرشادات والروابط هناك.

## تكوين بيانات اعتماد الحساب الخاص بك

بمجرد استلام اسم المستخدم وكلمة المرور الخاصة بك من وكالة التسجيل، سيتعين عليك اتباع رابط "التهيئة" على الصفحة الرئيسية للموصل. يمكنك إدخال بيانات الاعتماد الخاصة بك هناك. عناصر واجهة المستخدم المطلوبة للتسجيل التلقائي ستظهر فقط بعد تهيئة بيانات الاعتماد الخاصة بك. إذا كنت لا ترى أزرار "تسجيل" أو "تحديث" أو "إعادة تعيين" المذكورة في الفقرات التالية، فيرجى التحقق مرتين من صفحة الإعداد.

## التحقق من تنسيق التصدير (اختياري، المستخدمين المتقدمين فقط)

يمكن لمعظم المستخدمين تخطي هذه الفقرة والقفز مباشرة إلى الفقرة التالية. إذا كان أنت مستخدم متقدم يعرف تنسيقات O4DOI أو DataCite وتريد التحقق من ما يتم تصديره بالضبط إلى وكالة التسجيل ثم يمكنك إلقاء نظرة على XML الذي تم إنشاؤه قبل تسجيله.

للقيام بذلك انتقل إلى الصفحة الرئيسية للموصل وحدد واحدة من القوائم ذات العناصر القابلة للتصدير. عند النقر على زر "تصدير" لكائن واحد أو يمكنك تحديد عدد من الكائنات والنقر على زر "تصدير" في نهاية القائمة ثم يمكنك تنزيل تنسيق XML بالضبط كما سيتم تصديره إلى وكالة التسجيل. إذا قمت بتحديد أكثر من كائن واحد في كل مرة قد تضطر إلى تثبيت أداة "تشغيل" على خادم OJS الخاص بك وأداة لاستخراج القطران على جهاز الكمبيوتر المحلي الخاص بك، انظر "متطلبات التثبيت" أعلاه للحصول على التفاصيل.

تصدير الملف لن يغير حالة تسجيل الكائن. يمكنك النظر إلى XML في أي وقت. في حالة موصل "mEDRA" سوف ترى تنسيق إشعار "التسجيل" عندما لم يتم تسجيل الكائن من قبل. بعد التسجيل الأول سترى تنسيق الإشعار "التحديث". في حالة موصل "DataCite" فإن تنسيقي "التسجيل" و"التحديث" هما نفس الشكل.

## تسجيل DOI جديدة

المسار السريع للتسجيل التلقائي هو:

- افتح الرابط "تصدير كل شيء غير مسجل ..." على الصفحة الرئيسية للموصل،
- تحقق من قائمة الكائنات غير المسجلة وتأكد من أن جميع الكائنات قد تم اختيارها بشكل افتراضي،
- انقر فوق زر "تسجيل" في أسفل القائمة و
- انتظر رسالة "التسجيل بنجاح!".

هذا كل شيء. سيتمكن معظم المستخدمين على الأرجح من القيام بكل تسجيلات DOI الخاصة بهم هكذا. إذا كنت لا تنوي تحديث البيانات الوصفية بعد التسجيل، فهذا هو كل ما ستفعله على الإطلاق.

إذا كنت ترغب في تسجيل كائنات محددة بشكل انتقائي، فيمكنك القيام بذلك في أي من القوائم التي يمكنك الوصول إليها من خلال الصفحة الرئيسية للموصل. يمكنك إما تسجيل العناصر عن طريق النقر على رابط "السجل" المقابل أو عن طريق التحقق من عدة عناصر يدوياً والنقر على زر "السجل" في أسفل القائمة.

ستختفي الكائنات التي تم تسجيلها بنجاح من قائمة "تصدير كل الأشياء الغير مسجلة..."

## تحديث بيانات تعريف DOI

تصف هذه الفقرة كيفية تحديث البيانات الوصفية لـ DOI موجودة، وليس كيفية تعيين DOI جديد لكائن موجود بالفعل. OJS لا يدعم حاليا تغيير DOI لكائن مسجل مسبقا. لا ينصح بتعيين معرف جديد إلا عندما يتغير محتوى الكائن المقابل تغيرا كبيرا. وفي حالة مكتب خدمات الرقابة الداخلية، قد يؤدي ذلك إلى جولة أخرى من عمليات المراجعة الداخلية أو الخارجية، أو التخطيط، أو التدقيق المطبعي، أو غير ذلك من مهام التحرير. لذلك، إذا كنت ترغب في إعادة تسجيل كائن منشور مع DOI مختلف، فسيتعين عليك إنشاء مشكلة جديدة. المقالة أو الوادي أو الملف التكميلي وتسجيلها ككائن جديد.

بمجرد تسجيل الكائن لأول مرة، فإنه يختفي من قائمة الكائنات غير المسجلة لموصل وكالة التسجيل. غير أنه سيستمر إدراجه في الصفحات الخاصة بكل جسم. الزر المقابل للكائن سوف يتغير إلى "تحديث" بدلاً من "تسجيل". هذه هي الطريقة التي يمكنك بها التعرف على الكائنات التي يعتبرها OJS "مسجلة".

ولن تنقل تلقائيا التغييرات في البيانات الفوقية لمكتب خدمات الرقابة الداخلية إلى وكالة التسجيل. يجب عليك النقر على زر "تحديث" لتحديث البيانات الوصفية للكائن في قاعدة بيانات وكالة التسجيل المناظرة للبيانات الوصفية المحفوظة حاليا في OJS بما في ذلك جميع التغييرات التي أجريت منذ آخر تسجيل أو تحديث للكائن مع وكالة التسجيل.

ملاحظة: في حالة mEDRA قد يحدث أن يظهر كائن كـ "مسجل" في OJS على الرغم من أنك تلقيت رسالة خطأ عبر البريد الإلكتروني بعد النقر على زر "تسجيل" لأول مرة. ويرجع ذلك إلى الطبيعة غير المتزامنة لخدمة التسجيل في نظام mEDRA: لا يعني التحميل الناجح لملف بيانات التعريف في نظام mEDRA قبول ذلك الملف في قاعدة بيانات نظام mEDRA. الرجاء عدم النقر على زر "تحديث" للاستعادة من خطأ بعد التسجيل الأول. اتبع الإتجاهات في "إعادة تعيين حالة DOI" أدناه، بدلاً من ذلك. يمكنك استخدام زر "التحديث" للاستعادة من التحديث الفاشل. الرجاء تصحيح حالة الخطأ الموصوفة في البريد الإلكتروني الذي تلقته من خدمة التسجيل mEDRA ثم انقر فوق زر "تحديث" للعنصر الفاشل مرة أخرى. إذا كنت تستخدم موصل DataCite فلابد أن تكون حالة تسجيل OJS دائماً مطابقة 100% لحالة التسجيل الحقيقية طالما أنك لا تخلط التسجيل التلقائي واليدوي.

## إعادة تعيين حالة تسجيل DOI (مدرا فقط)

في حالة mEDRA يمكن أن تخرج حالة تسجيل كائن في OJS من حالة التزامن مع حالة التسجيل الحقيقية في قاعدة بيانات mEDRA. يحدث هذا عندما يعترف mEDRA برفع ناجح أولاً ولكن في وقت لاحق يرفض الملف بسبب عدم التحقق من ظروف الخطأ أثناء التحميل.

تنسيق mEDRA XML للتسجيل الأول يختلف عن تنسيق XML للتحديث. لذلك، لا يمكنك استخدام زر "التحديث" للاسترداد من الخطأ لأنه سيؤدي فقط إلى فشل تحميل آخر. هذا هو المقصود بزر "إعادة تعيين". يبدو لجميع الأشياء التي تم تسجيلها بالفعل. النقر عليه يزيل جميع معلومات التسجيل للكائن من قاعدة بيانات OJS بحيث يظهر الكائن إلى OJS كما لو أنه لم يتم تسجيله من قبل.

بالطبع لا يجب عليك النقر فوق زر "إعادة تعيين" إذا تم تسجيل الكائن بنجاح كما أنه سيقوم بحذف معلومات التسجيل الصحيحة. إذا حدث لك النقر على زر "إعادة تعيين" بالصدفة فسيتعين عليك إعادة تسجيل الكائن الذي سيؤدي إلى رسالة خطأ من mEDRA (التي يمكنك تجاهلها بأمان في تلك الحالة) ولكن سيتم تصحيح حالة التسجيل في OJS.

ملاحظة: لا تستخدم زر "إعادة تعيين" للاستعادة من أخطاء التحديث! إذا كنت تتلقى رسالة خطأ عبر البريد الإلكتروني بعد النقر على زر "تحديث" ثم انقر فقط على زر "تحديث" مرة أخرى بعد تصحيح المشاكل المذكورة في رسالة الخطأ mEDRA.