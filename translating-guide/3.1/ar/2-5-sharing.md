---
book: دليل الترجمة
version: 3.1
---

## شارك الترجمات الخاصة بك

1. حفظ ووضع الملفات الخاصة بك
2. اقتراح إدراج الملفات إلى PKP

### حفظ ووضع الملفات بشكل صحيح

بمجرد أن تقوم بترجمة ملفات XML الضرورية، سوف تحتاج إلى وضعها في دلائل فرعية مسماة بشكل صحيح، استخدام رموز لغة ISO للغة والبلد الخاص بك (e. ., يتم ترجمة الملفات في `locale/en_US` إلى الفرنسية ويتم حفظها في دليل فرعي يسمى `locale/fr_CA`.  راجع [ملفات XML](2-2-xml-files) للحصول على تفاصيل الموقع.

يجب أيضا إضافة اللغات الجديدة إلى الملف `تسجيل/محليات. ml`، بعد يمكن تثبيته في النظام من خلال الموقع إدارة واجهة الويب.


### ارتبط بالترجمة الخاصة بك

GitHub "طلب سحب" هو الطريقة المفضلة لتقديم ترجماتك إلى PKP.

سوف تجد أن هذا الرابط مفيد للغاية لإنشاء مستودع محلي الخاص بك وإرسال التغييرات الخاصة بك مثل الوارد وصفها في [Github وثائق المساهمين في PKP](http://pkp.sfu.ca/wiki/index.php?title=Github_Documentation_for_PKP_Contributors) (PKP wiki).

بمجرد إعدادك مستودع محلي ومصدر أصلي، سوف تحتاج إلى إرسال التغييرات الخاصة بك إلى مستودع github البعيد ("الأصل") كما هو مقترح في [معلومات للمطورين](http://pkp.sfu.ca/wiki/index.php?title=Information_for_Developers#PKP_library_submodule_changes) (PKP wiki).

لاحظ أنه بقدر ما تكون ملفات الترجمة في الجذر ولكن أيضا في مجلد الوحدة الفرعية "lib/pkp"، سوف تحتاج إلى دفعات TWO: واحدة لمستودع "OxS" الرئيسي والأخرى للوحدة الفرعية "pkp-lib".

وخلاصة القول إن هذه هي العملية التي تحتاج إلى اتباعها:

1.  فورك مستودعات "أكسس" و "lib-pkp" إلى حساب github الخاص بك.
2.  استنسخ شوكك إلى المستودع المحلي الخاص بك.
3.  قم بإدخال التعديلات المحلية.
4.  اضغط أولاً "lib-pkp" ثم "oxs" (منفصل) إلى مستودع البعيد.
5.  تقديم 2 "طلبات سحب" منفصلة (واجهة github).

هذه هي التعليمات المحددة التي تحتاج إلى تشغيلها بعد التوكيد على كلا المستودعين:

```
# شاهد مستودع القاعدة الخاص بك (pe: ojs-dev_2_4)، بما في ذلك الوحدات الفرعية.
git الخروج ojs-dev_2_4
git submodule upd--init --resive\
cd lib/pkp
git Checout ojs-dev_2_4
cd ../..
```

```
# إنشاء فرع مع الترجمات الجديدة الخاصة بك (كلاهما، في "OxS" و "pkp-lib")
git Checout -b tra-es_ES-245 origin/ojs-dev-2_4
cd lib/pkp
git Checout -b tra-es_ES-245 origin/ojs-dev-2_4
cd. /..
```

```
# إذا كنت تعمل مع الأدوات الخارجية (ب: أدوات CAT التي تنشئ XMLs) الجديدة قم بنسخ الملفات المصدرية الخاصة بك على الملفات الموجودة.
cp origen/* .-أ
```

```
# قم بإدخال التغييرات الخاصة بك (أول في الوحدة الفرعية الخاصة بك)
cd lib/pkp
git إضافة.
git الالتزام -a
cd ../..
git يضاف
git إلتزام-أ
```

```
# أرسل التغييرات الخاصة بك إلى مستودع github الخاص بك.
git push -u الأصل tra-es_ES-243
cd lib/pkp
git push -u الأصل tra-es_ES-243
cd ../..
```

```
# قم بإنشاء "طلب سحب" وإرسال عملك إلى مستودع PKP الرسمي (الوحدة الفرعية الأولى، ثم الجذر).
```

### بعض النصائح

إضافة مشروع فرعي:

```
git submodule add [git://github.com/marcbria/adminlocker](git://github.com/marcbria/adminlocker) plugins/generic/adminLocker
```

تغيير مستودعك البعيد (pe: من git إلى https)

```
git set-url الأصل عن بعد https://github.com/marcbria/pkp-lib.git
```

إضافة معلومات الألوان:

```
git config --العالمي --إضافة لون .ui صحيح
```

ارسم الفروع:

```
سجل git --الرسم البياني --oneline --كل https://github.com/pkp/ojs/Network
```

### تصدير ترجمة

*(OJS 2.x plugin only)* You can export a translation by clicking the <em>Export</em> link across from the language name on the Translator plugin page: the system will compress all locale files for that one translation to a downloadable tar.gz package. هذا مفيد بشكل خاص إذا كنت بحاجة إلى ترحيل لغة مترجمة حديثاً إلى بيئة OJS أو OCS أخرى. أو إذا كنت ترغب في المساهمة بالتغييرات الخاصة بك في PKP.

