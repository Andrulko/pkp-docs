# سمة Bootstrap3
[Bootstrap 3](https://getbootstrap.com/docs/3.4/) هو إطار HTML و CSS و JavaScript لتطوير تطبيقات ويب سريعة الاستجابة ومحمولة أول. بسبب شعبيتها، العديد من المطورين على دراية بتقنيات HTML و CSS و JavaScript المستخدمة في الإطار.

موضوع [Bootstrap3](https://github.com/NateWr/bootstrap3) هو جهد مجتمعي لتوفير موضوع أساسي مبني على هذه التقنيات. يقوم بتنفيذ شكل مجلة OJS باستخدام علامة الـ bootstrap HTML الأساسية، ويوفر عددا من أنماط الطرف الثالث لبوتستراب 3 خارج الصندوق.

موضوع Bootstrap3 المجتمعي مصمم ليكون قاعدة وليس منتج نهائي. ضمان التوافق على نطاق واسع مع موارد Bootstrap 3، وتيسير تقديم المطورين المعتادين على العمل مع Bootstrap 3، هذا الموضوع يوفر فقط علامات باستخدام المكونات الأساسية من إطار Bootstrap 3.

وهذا يعني أنه، في معظم الحالات، سوف تحتاج إلى القيام بعمل أكثر قليلاً مع [موضوع فرعي](child-themes.md) من أجل الصقل خارج موقعك.

وتوضح مواقع المكتب هذه المواضيع الخاصة بالطفل في Bootstrap:
- [الافتراضي](https://demo.publicknowledgeproject.org/ojs3/demo/index.php/boot1)
- [ورق](https://demo.publicknowledgeproject.org/ojs3/demo/index.php/boot2)
- [يومية](https://demo.publicknowledgeproject.org/ojs3/demo/index.php/boot3)
- [ييتي](https://demo.publicknowledgeproject.org/ojs3/demo/index.php/boot5)
- [حجر رملي](https://demo.publicknowledgeproject.org/ojs3/demo/index.php/boot6)
- [Cyborg](https://demo.publicknowledgeproject.org/ojs3/demo/index.php/boot4)

## تثبيت Boostrap3

طريقة **أبسط** للحصول على سمة Bootstrap3 هي تنزيل [أحدث إصدار](https://github.com/NateWr/bootstrap3/releases) من مستودع التطوير. فك حزمة ملف `.zip` ونقل دليل `bootstrap3` إلى تثبيت OJS الخاص بك في `/plugins/themes/bootstrap3`.

طريقة **أسرع** للحصول على سمة Bootstrap3 هي استخدام git من سطر الأوامر.

```
git الوحدة الفرعية إضافة https://github.com/NateWr/bootstrap3.git plugins/themes/bootstrap3
```

بمجرد التثبيت، يجب عليك الذهاب إلى **إعدادات > الموقع > الإضافات** في منطقة مشرف OJS الخاص بك وتمكين سمة Bootstrap3. يمكنك بعد ذلك تصفح **الإعدادات > الموقع > المظهر** لاختيار واحدة من سمات الموضوع المجمعة.

## قالب مجمع "سباتيش"
وهناك عدة "حلقات" من طراز Bootstrap 3 مجمعة مع الموضوع. وتوفر هذه السباحة حزمة مخصصة من المتغيرات والأنماط التي تصنف ألوان الموضوع وطباعته وأكثر.

ويتم الإفراج عن كل من الحدائق التي يتم توفيرها بموجب رخصة متوافقة مع قاعدة البيانات العالمية. وهناك آلاف أخرى من محلات Bootstrap 3 (غالبا ما تسمى المواضيع) التي يمكن شراؤها من المواقع التجارية على الإنترنت.

## استكشاف Bootstrap
بما أن موضوع Bootstrap هو مجرد قاعدة، فإنه يحتاج إلى القليل من العمل لتنفيذ موضوع رائع بشكل كامل. من المستحسن إذا كنت تعمل مع هذه الملفات أن تكون على دراية بعناصر [Bootstrap 3](https://getbootstrap.com/docs/3.4/getting-started/) و [LESS](http://lesscss.org/features/).

للبدء، استكشف ملف متغيرات Bootstrap الأساسية:

- [الإضافات/themes/bootstrap3/bootstrap/less/variables.less](https://github.com/NateWr/bootstrap3/blob/master/bootstrap/less/variables.less)

كل لون أو خط، إلخ، معلن هنا وكل موضوع من المواضيع المجمعة المختلفة يتخطى هذه المتغيرات في الأساس. على سبيل المثال ، إليك ملف متغيرات موضوع الفلاسلي:

- [الإضافات/الموضوع/bootstrap3/bootstrap-themes/flatly/variables.less](https://github.com/NateWr/bootstrap3/blob/master/bootstrap-themes/flatly/variables.less)

ومن ثم فإنها تحتوي على القليل من التعليمات البرمجية الإضافية "LESS" لتضييق بعض الأشياء الأخرى:

- [الإضافات/themes/bootstrap3/bootstrap-themes/flatly/bootswatch.less](https://github.com/NateWr/bootstrap3/blob/master/bootstrap-themes/flatly/bootswatch.less)

## موضوع Bootstrap3

وتعمل كل مستنقعات الموضوع المجمعة بنفس الطريقة. يتجاوزون ملفات Bootstrap 3 الأساسية مع قيمهم الخاصة. من المحتمل أنك تريد إجراء المزيد من التخصيصات مع السمة الخاصة بك.

للقيام بذلك، سوف ترغب في إنشاء [موضوع فرعي](child-themes.md). إذا لم تكن على دراية بهذه العملية، عد واتبع هذا الدليل لبناء قالب فرعي خاص بك وقم بتعيين الوالد إلى `bootstrapthreethemeplugin`.

يمكنك بعد ذلك استخدام طريقة `modifyStyle()` من [واجهة برمجة التطبيقات الخاصة](theme-api.md) لحقن المتغيرات الخاصة بك.

```php
    /**
     * قم بتحميل الأنماط المخصصة للموضوع
     * @return null
     */
    وظيفة عامة داخل () {
        $this->setParent('bootstrapthreethemeplugin');
        $this->modifyStyle('bootstrap', ary('addLess' => الصفيف('styles/variables. س)))؛
}
```

الآن سيحمل موضوع الطفل الخاص بك ملف LESS إضافي، `styles/variables.less`من دليل ملف الموضوع الخاص بك. يمكنك تجاوز متغيرات Bootstrap 3 في ذلك الملف.

ابحث عن ملف متغيرات [Bootstrap 3](https://github.com/NateWr/bootstrap3/blob/master/bootstrap/less/variables.less). انسخ محتويات هذا الملف في الموضوع الخاص بك على `styles/variables.less`. ثم قم بتعديلها على أي حال تريد.

فيما يلي مثال على مجموعة معدلة من الألوان في `styles/variables.less` الجديدة.

```less
@gray-base: #012434;
@gray-darker: lighten(@gray-base, 13. %);
@gray-dark: lighten(@gray-base, 20%)؛
@gray: lighten(@gray-base, 33. %);
@gray-light: lighten(@gray-base, 46. %)؛
@gray-lighter: lighten(@gray-base, 93. %);

@brand-Preary: darken(#6f72ed, 6. %)؛
@brand-succes: #5cb85c؛
@brand-info: #5bc0de؛
@brand-warning: #f0ad4e;
@brand-danger: #d9534f;
```

إذا كنت ترغب في بناء قالب الطفل الخاص بك من أحد سبائك الموضوع المجمعة، قم بنسخ ملف الـ swatch `المتغيرات` بدلاً من ذلك.

## المساهمة بحجر مجتمع
إذا كنت قد أنشأت نبذة جديدة رائعة تعتقد أنه ينبغي تجميعها مع موضوع Bootstrap3، يمكنك المساهمة بها بفتح طلب سحب على [مستودع التطوير](https://github.com/NateWr/bootstrap3/).

لإضافة مقايضة جديدة إلى موضوع Bootstrap3، تحتاج إلى إعداد جميع الملفات اللازمة لمنحدراتك الجديدة (e). . `myswatch`).

هذا المثال سيوضح كيفية استخدام منصة `المسطحة` كأساس للمسرح الجديد.

1. نسخ المجلد في `الإضافات/themes/bootstrap3/bootstrap-themes/flatly` إلى `الإضافات/themes/bootstrap3/bootstrap-themes/myswatch`
2. احذف ملف `LICENSE` الحالي واستبداله برخصة GPL-متوافقة مع GPL.
3. تحذف المحتويات التالية بحيث تكون الملفات التالية فارغة:
```
الإضافات/themes/bootstrap3/bootstrap-themes/myswatch/bootswatch.less
plugins/themes/bootstrap3/bootstrap-themes/myswatch/variables.less
```

4. إعادة تسمية `bootswatch.less` إلى `myswatch.less`

5. نسخ الملف `الإضافات/themes/bootstrap3/styles/flatly.less` إلى `plugins/themes/bootstrap3/styles/myswatch.less`
6. تحرير `الإضافات/themes/bootstrap3/styles/myswatch.less`: تعديل المراجع الحالية للملفات في `بشكل صارم` مع مراجع إلى Myswatch الجديدة.
```
@import "bootstrap.less";
@import "../bootstrap-themes/myswatch/variables.less";
@import "../bootstrap-themes/myswatch/myswatch.less"; 
```

7. تحرير `plugins/themes/bootstrap3/BootstrapThreeThemePlugin.inc.php` وإضافة خيار جديد لموضوع الطفل الخاص بك، على سبيل المثال `'mytheme' => 'plugins.themes.bootstrap3.options.bootstrapTheme.myswatch',`
8. تحرير `plugins/themes/bootstrap3/locale/en_US/locale.xml` وإضافة إدخال محلي جديد للموضوع الجديد الخاص بك. وعلى سبيل المثال:
```
<message key="plugins.themes.bootstrap3.options.bootstrapTheme.myswatch">سباتي</message>
```

قد ترغب في تغيير حقوق التأليف والنشر ومعلومات الترخيص إلى المواصفات الخاصة بك في ملف LESS أيضًا. وعلى سبيل المثال:
```
/**
 * @file plugins/themes/bootstrap3/myswatch.less
 *
 * Copyright (c) 2014-2016 Simon Fraser University Library
 * Copyright (c) 2003-2016 John Willinsky
 * Distributed under the GNU GPL v2. للاطلاع على كامل المصطلحات، انظر الملف docs/COPYING.
 *
 * ورقة Stylesheet @brief لموضوع القالب الخاص بي.
 */
 ```
