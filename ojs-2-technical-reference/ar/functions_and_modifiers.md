# الدوال & المعدِّلات

تمت إضافة عدد من الوظائف إلى وظائف القالب المدمجة في Smarty's للمساعدة في المهام المشتركة مثل التوطين.

- `ترجم` (على سبيل المثال `{translkey="my.locale.key" myVar="value"}`: هذه الوظيفة توفر ترجمة خاصة بلغة محددة. (انظر قسم التدويل). يمكن استبدال المتغير باستخدام بناء على النمط الذكي؛ باستخدام المثال أعلاه، إذا كان الملف `locale.xml` يحتوي على:

````
<message key="my.locale.key">myVar يساوي "{$myVar}".</message>
````

وسيكون الناتج الناتج كما يلي:

````
ميفار يساوي "القيمة".
````

(لاحظ أنه لا يسمح إلا بالاستبدالات المباشرة في الملفات المحلية). لا يمكنك الاتصال بالأساليب على الكائنات أو وظائف الذكاء.)

- `تعيين` (على سبيل المثال `{translate<unk> assign:"myVar" key="my.locale.key"}`: تعيين قيمة لمتغير قالب. هذا المثال مشابه لـ `{translate ...}`، إلا أن النتيجة تم تعيينها إلى متغير الذكي المحدد بدلاً من عرضها على المتصفح.

- `html_options_transl` (على سبيل المثال `{html_options_transles=$myValuesArray المحدد =$selectedOption}`): تحويل مجموعة من النموذج

````
array('optionVal1' => 'locale.key.option1', 'optionVal2' => 'locale.key.option2')
````

إلى مجموعة من HTML `<option>...</option>` وسوم النموذج

````
<option value="optionVal1">ترجمة "locale.key.option1" هنا</option>
<option value="optionVal2">ترجمة "locale.key.option2" هنا</option>
````

للاستخدام في القائمة المحددة.

- `get_help_id` (على سبيل المثال `{get_help_id key="myHelpTopic" url="true"}`: يعرض معرف الموضوع أو عنوان URL الكامل (اعتماداً على قيمة معامل url) إلى صفحة المساعدة المحددة المسماة.

- `أيقونة` (على سبيل المثال `{icon name="mail" alt="..." url="http://link.url.com" تعطل "true"}`): يعرض أيقونة مع رابط URL المحدد أو معطل أو مفعل كما هو محدد. معلمة الاسم يمكن أن تأخذ على القيم `تعليق`، `حذف`، `تحرير`، `حرف`، `البريد`، أو `عرض`.

- `help_topic` (على سبيل المثال `{help_topic key="(dir)*.page. opic" text="foo"}`: يعرض وصلة لموضوع المساعدة المحدد، مع معلمة النص تعرف محتوى الرابط.

- `page_links`: (على سبيل المثال `{page_linkator=$submissions}`): يعرض روابط الصفحة لقائمة الصفحات المرتبطة بـ `أيتيتيرتور` (في هذا المثال ، `$submissions`).

- `page_info`: (على سبيل المثال `{$page_info name="submissions" محرر =$submissions}`): يعرض معلومات الصفحة (على سبيل المثال رقم الصفحة وإجمالي عدد الصفحات) لقائمة الصفحات المرتبطة بـ `التيميتيرتور` في هذه الحالة `$submissions`).

- `تكرار`: (على سبيل المثال `{$iterate from=Subitem=submission}`): تحرر من خلال عناصر في `محددة` من الفئة الفرعية، مع كل عنصر مخزون كمتغير ذكي مع الاسم المورد. (هذا المثال يكرر من خلال عناصر في `$submissions` محرر، الذي كل عنصر مخزون كمتغير قالب اسمه `$submission`.) لاحظ أنه لا توجد إشارات بالدولار تسبق أسماء المتغيرات -- المعلمات المحددة هي أسماء متغيرة، وليست متغيرات نفسها.

- `strip_unsafe_html`: (على سبيل المثال `{$myVar|strip_unsafe_html}`): إزالة وسوم وسمات HTML والسمات التي تعتبر "غير آمنة" للاستخدام العام. يتيح هذا المعدِّل بعض علامات HTML البسيطة ليتم تمريرها إلى المتصفح البعيد، لكن تنظيف أي شيء متقدم يمكن استخدامه في الهجمات المستندة إلى XSS.

- `call_hook`: (على سبيل المثال: `{call_hook name="قوالب::Manager::Index::ManagementPages"}`) استدعاء رابط إضافي عن طريق الاسم. سيتم استدعاء أي إضافات مسجلة ضد الرابط المسمى.

وهناك العديد من الأمثلة على استخدام كل وظيفة من هذه الوظائف في النماذج المقدمة مع OJS 2.x.
