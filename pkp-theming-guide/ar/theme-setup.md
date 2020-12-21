# إعداد السمة & تكوين

الآن بعد أن قمنا بتحديد بنية HTML و CSS في موضوع ما، نحن بحاجة إلى تسجيل إضافتنا مع تطبيق OJS أو OMP. سنقوم بذلك مع بعض ملفات PHP و XML.

دعونا نلقي نظرة على هيكل الملفات لموضوع أساسي سوف نسميه `الموضوع التعليمي`.

```
/plugins/themes/tutorial-theme/index.php
/plugins/themes/tutorial-theme/Tutorial-theme/TutorialThemePlugin.inc.php
/plugins/themes/tutorial-theme/version.xml
/plugins/themes/tutorial-theme/en_US/locale.po
/plugins/themes/tutorial-theme/styles/index.less
/plugins/themes/tutorial-theme/themes/variables.الأقل
/plugins/themes/sttorial-theme/structure.less
plug/plugins/themes/themes/tutoriyles/formyles/formeses/formes_es_unes/themes.

```

ملف `/plugins/themes/tutorial-theme/index.php` يستخدم لتحميل الموضوع الخاص بنا. نقوم بتحميل ملف صف الموضوع ونمثالية على كائن جديد

```php
<?php
require_once('TutorialThemePlugin.inc.php');
إرجاع البرنامج التعليمي الجديد Plugin();
?>
```

`/plugins/themes/tutorial-theme/TutorialThemePlugin.inc.php` هو المكان الذي نحدد فيه ملف صف الموضوع الخاص بنا. يمكننا بعد ذلك تحميل ورقات الأنماط وتنفيذ أي إجراءات أخرى نريدها مع [واجهة برمجة التطبيقات](theme-api.md).

```php
<?php
استيراد ('lib.pkp.classes.plugins. hemePlugin')؛
فصل تعليمي ملحق البرنامج المساعد يمدد موضوع البرنامج المساعد

    / **
     * تحميل الأنماط المخصصة لموضوع
     * @return null
     */
    وظيفة عامة في() {
        $this->إضافة ستيلي('stylesheet', 'أسطور/فهرس. مقياس)؛
    }

    /**
     * احصل على اسم العرض لهذا الموضوع
     * @return string
     */
    function getDisplayName() {
        العودة 'ثيمة البرنامج التعليمي';
    }

    /**
     * احصل على وصف هذه الإضافة
     * @return string
     */
    function getDescription() {
        ارجع 'مثالًا على مظهر OJS أو OMP مبني مع وثائقنا المذهلة. ;
    }
}
```

ملف `/plugins/themes/tutorial-theme/version.xml` مطلوب لتكوين البيانات الوصفية حول الموضوع الذي نستخدمه OJS و OMP لتحميله وعرضه بشكل صحيح.

```xml
<?xml version="1.0" ترميز UTF-8"?>
<!DOCTYPE الإصدار SYSTEM "../../lib/pkp/dtd/pluginVersion. td">
<version>
    <! - يجب أن تتطابق قيمة التطبيق مع اسم الدليل الخاص بالسمة -->
    <application>الموضوع التعليمي</application>
    <type>الملحقات. هي</type>
    <release>1.0.0.</release>
    <date>2016-11-21</date>
    <lazy-load>1</lazy-load>
    <class>البرنامج التدريبي</class>
</version>
```

ملف `/plugins/themes/tutorial-theme/locale/en_US/locale.po` يسمح لنا بجعل أي مقاطع في موضوعنا جاهزة للترجمة. نحن نفعل ذلك من خلال تعيين سلاسل مفتاح.

```po
"مشروع - Id-Version: \n"
"Report-Msgid-Bugs-to \n"
"آخر مترجم: \n"
"Language-Group : \n"
"MIME-Version: 1.\n"
"نوع المحتوى: نص/سهل؛ charset=UTF-8\n
"ترميز المحتوى: 8bit\n
"POT-Creation-Date: 2020-06-19T13:50:00+00:00\n
"PO-Revision-date 2020-06-19T13:50:00+00\n
"اللغة: \n

msgid "الإضافات". إسم hemes.tutorial-theme.name"
msgstr "موضوع البرنامج التعليمي"

msgid "plugins.themes.tutorial-theme.description"
msgstr "موضوع مثال لOJS أو OMP تم بناؤه باستخدام وثائقنا الرائعة".
```

تذكر كيف أعطينا القالب إسم ووصف في صف إضافة القالب؟ يمكننا الآن تحديث هذه الأساليب لتحميل المقاطع المترجمة.

```php
/**
     * احصل على اسم العرض لهذا السمة
     * @return string
     */
    function getDisplayName() {
        return __('plugins. الموضوع التعليمي. اللعبة)؛
    }

    /**
     * احصل على وصف هذه الإضافة
     * @return string
     */
    function getDescription() {
        return __('plugins. hemes.tutorial-theme.description');
}
```

إذا كنت تبني موضوع لاستخدامك الشخصي، فلن تحتاج إلى هذا. لكننا نوصي دائما بإنشاء قدرات الترجمة لأي موضوع سيتم توزيعه. ويمتد نطاق مجتمع مستخدمي مشروع المعرفة العامة إلى عشرات البلدان واللغات التي تحتاج جميعها إلى برمجيات بلغتها الخاصة.

أخيرا يحمّل `/plugins/themes/tutorial-theme/styles/index.less` ملفاتنا CSS/LESS المخصصة. في ملف الصف المساعد للموضوع الخاص بنا، ربما كنت قد لاحظت طريقة `في` التالية:

```php
public function init() {
        $this->addStyle('stylesheet', 'styles/index.less');
    }
```

باستدعاء `نمط الإضافة` والإشارة إليه إلى ملف LESS الرئيسي، سيقوم التطبيق تلقائياً بتجميع وتحميل ملف CSS على واجهة أي مجلة أو اضغط باستخدام هذا الموضوع.

_إذا لم تكن متأكداً من ملف LESS ، تحقق من القسم على CSS/LESS أعلاه._

## استكشاف المزيد

هذا الجزء من الدليل المواضيعي قد أدخلك على بنية مظهر OJS أو OMP. لكن هناك الكثير الذي يمكنك القيام به مع [قالب API](theme-api.md).

واصل القراءة للحصول على المزيد من النصائح العملية حول كيفية استخدام [سمات الأطفال](child-themes.md)، كامل الوثائق على [واجهة برمجة التطبيقات](theme-api.md) و [خيارات السمات API](theme-options-api.md)، بالإضافة إلى الروابط مع الأمثلة الحالية للمواضيع المخصصة في البرية.

