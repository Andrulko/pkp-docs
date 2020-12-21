# وثائق خيارات القالب API

خيارات السمة تسمح لك بتقديم إعدادات الإعدادات الخاصة بالسمة. وهي تستخدم في أغلب الأحيان لتوفير اختيارات الألوان والخطوط حتى تتمكن المجلة من تكييف الموضوع مع العلامة التجارية الخاصة بها.

الخيارات المضافة إلى السمة ستظهر تحت اختيار السمة في الإعدادات > الموقع > مظهر > قسم السمة.

![لقطة شاشة لخيارات الموضوع في الخلفية](theme-options.png)

## إضافة خيار السمة

يجب تكوين جميع خيارات السمة في طريقة `init()` للموضوع الخاص بك. المثال أدناه سينشئ منتقي الألوان, أضفه إلى الإعدادات عند تحديد السمة الخاصة بك, وتوفير قيمة افتراضية لاستخدامها عندما لا يكون المستخدم قد حدد واحدة منها.

```php
وظيفة عامة init() {
    $this->إضافة Option('baseColour', 'FieldColor', [
        'التسمية' => __('الإضافات'. hemes.default.option.color. abel'),
        'description' => __('plugins.themes.default.option.colour. سكريبتون'),
        'الافتراضي' => '#1E6292',
    ]);
}
```

إضافة خيار للتحديد من قائمة.

```php
وظيفة عامة() {
    $this->إضافة اختياري('typography', 'الحقول'، خيارات الحقول', [
        'نوع' => 'راديو',
        'التسمية' => __('الإضافات'. hemes.default.option.typography.label'),
        'description' => __('plugins. hemes.default.option.typography. سكريبيا')،
        'خيارات' => [
            [
                'قيمة' => 'notoSans',
                'التسمية' => __('الإضافات'. hemes.default.option.typography. OtoSans')،
            ]،
            [
                'القيمة' => 'notoSerif',
                'التسمية' => __('الإضافات'. hemes.default.option.typography. OtoSerif')،
            ]،
        ]،
        'الافتراضي' => 'notoSans',
    ])؛

```

إضافة مربع اختيار لتمكين أو تعطيل ميزة.

```php
وظيفة عامة init() {
    $this->إضافة Option('showDescriptionInJournalIndex', 'خيارات الحقول', [
        'التسمية' => __('المدير'. الإعداد. ontextSummary')،
        'خيارات' => [
            [
                'قيمة' => صحيح,
                'التسمية' => __('الإضافات'. hemes.default.option.showDescriptionInJournalIndex. (بالإنكليزية)، و
            ]، و
        ]،
        'الافتراضي' => false,
    ])؛
}
```

إضافة حقل نص لوصف قسم.

```php
الدالة العامة init() {
    $this->addOption('callToAction', 'FieldText', [
        'label' => __('plugins.themes.default.option.callToAction.label'),
        'default' => false,
    ]);
}
```

> يمكن مشاهدة جميع مكونات حقل النموذج في مكتبة واجهة المستخدم [](/dev/ui-library/dev). 
> 
> {:.tip}

استخدم أي نوع من الحقول التي توسع فئة `الحقل` باستثناء `حقل التحميل` و `حقل التحميل`. تحميل الملفات غير مدعوم حتى الآن لخيارات الموضوع.


## استخدام خيار السمة

احصل على قيمة خيار السمة واستخدامها في السمة الخاصة بك. المثال أدناه سوف يستخدم اللون المحدد وينقله إلى ورقة نمط LESS قبل تجميعه، الكتابة فوق القيمة الافتراضية `@bg-base`.

```php
الدوال العامة() {
    $baseColour = $this->getOption('baseColour');
    $this->modifyStyle(
        'stylesheet',
        ['addLessVvariables' => ”@bg-base:$baseColour; ]
    )؛
}
```

احصل على خيارات السمة من أي قالب باستخدام متغير `$activeTheme`.

```html
{if $activeTheme->getOption('showDescriptionInJournalIndex')}
    <section>
        {$currentContext->getData('description')}
    </section>
{/if}
```

> إذا اتصلت بـ `$this->getOption(...)` في طريقة `init()` ، تأكد من أن جميع الخيارات قد تم إعلانها أولا. قيم خيارات السمة المضافة بعد المكالمة الأولى إلى `$this->getOption(...)` لن يتم إرجاعها. 
> 
> {:.warning}

## إدارة الألوان

عندما يقوم المستخدم باختيار ضوء أو لون مظلم مع خيار السمة ، يجب تعديل النص لضمان التباين الكافي بين الألوان. استخدم طريقة `isColourDark()` للتحقق من السطوع وإجراء التعديلات.

```php
الدالة العامة() {

        // تعيين لون الخلفية
        $additionalLessVariables[] = '@bg-base:' . $this->getOption('baseColour') . ';';

        // تعيين النص إلى اللون الأبيض إذا كانت الخلفية مظلمة جدا
    إذا (!$this->isColourDark($this->getOption('baseColour'))) {
        $additionalLessVariables[] = '@text-bg-base:white; ;
    }
}
```

## تعديل الخيارات الحالية

قد يحتاج موضوع الطفل إلى تمديد الخيار الموجود الذي يحدده الموضوع الأصلي أو إزالته كلية. تعديل خيار الطباعة.

```php
وظيفة عامة init() {
    $this->modifyOptionsConfig('typography', [
        'نوع' => الراديو،
        'تسمية' => 'الإضافات. إفتراضي. ption.typography.label',
        'description' => 'plugins.themes.default.option. ypography.description',

        // استبدل الخيارات الحالية بخيارات جديدة.
        'خيارات' => [
            'montserratNotoSerif' => 'plugins.themes.default-child.option.typography.montserratNotoSerif',
            'montserratNotoSan' => 'plugins.themes.default-child.option.typography.montserratNotoSans',
        ]
    ])؛
}
```

إزالة خيار الطباعة.

```php
وظيفة عامة init() {
    $this->إزالة الخيار ('typography' );
}
```

احصل على كائن الخيار `الحقل` للتلاعب به مباشرة.

```php
وظيفة عامة init() {
    $typographyField = $this->getOptionConfig('typography');
    $typographField->label = __('plugins.themes.default.option.typography.label');
}
```

احصل على كائنات `الحقل` لجميع خيارات السمة.

```php
الدالة العامة() {
    $allOptions = $this->getOptionsConfig();
    preach (صفيفة) $allOptions ك $option{
...
    }
}
```

## أمثلة

إضافة خيار موضوع لتحديد خط وتحميل ملف الخط المخصص بناء على اختيار المستخدم.

```php
الدالة العامة() {

    // إضافة الخيار
    $this->إضافة ('typography', 'خيارات الحقول', [
        'نوع' => 'راديو',
        'التسمية' => __('الإضافات'. hemes.default.option.typography.label'),
        'description' => __('plugins. hemes.default.option.typography. سكريبيا')،
        'خيارات' => [
            [
                'قيمة' => 'notoSans',
                'التسمية' => __('الإضافات'. hemes.default.option.typography. OtoSans')،
            ]،
            [
                'قيمة' => 'notoSerif',
                'التسمية' => __('الإضافات'. hemes.default.option.typography. otoSerif')،
            ]،
        ]،
        'الافتراضي' => 'notoSans',
    ])؛

    // تحميل خط جوجل الصحيح
    إذا ($this->getOption('typography') == 'notoSerif') {
        $this->addStyle(
            'fontNotoSerif',
            '//خطوط. القفزة om/css؟ amily=Noto+Serif:40040000i700700i',
            ['baseUrl' => ']
        )؛
        $this->modifyStyle(
            'stylesheet',
            ['addLessVvariables' => '@font: "Noto Serif", serif; ]
        )؛
    } أخرى {
        $this->إضافةStyle(
            'fontNotoSans',
            '//خطوط. القفزة om/css؟ amily=Noto+Sans:40040000i700700i',
            ['baseUrl' => ']
        )؛
        $this->modifyStyle(
            'stylesheet',
            ['addLessVvariables' => '@font: "Noto Sans", sans-serif; ]
        )؛
    }
}
```
