---
title: بدء - دليل الإضافات لOJS و OMP
---

# بدء العمل

في هذا الدليل، سننشئ ملحق عام سنقوم بتسميته مثال البرنامج التعليمي.

> قم بتنزيل مثال عمل [البرنامج المساعد](https://github.com/pkp/tutorialExample) الذي سنبنيه في هذا البرنامج التعليمي من GitHub. 
> 
> {:.notice}

تقوم الإضافة بتخزين جميع ملفاتها في مجلد واحد في OJS أو OMP. سوف تكون الإضافة `عامة` إضافة، لذلك نضعها في هذا الدليل. كل إضافة تتطلب ثلاثة ملفات.

```
ojs
<unk>
<unk> <unk> <unk> <unk> <unk> <unk> plugins
<unk> <unk>
<unk> <unk> <unk> <unk> <unk> <unk> generic
<unk> <unk>
<unk> <unk> <unk> <unk> <unk> tutorialexample
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> ', index. hp
<unk> <unk> <unk> <unk> <unk> ', TutorialExamplePlugin.inc.php
<unk> <unk> <unk> <unk> ', version.xml
```

> يجب أن يكون اسم الدليل أحرف وأرقام. لا توجد مسافات ، `-`، أو `_` حروف مسموح بها. 
> 
> {:.tip}

## الإصدار.xml

توفر `version.xml` المعلومات المطلوبة لتحميل الإضافة.

```xml
<?xml version="1.0" ترميز UTF-8"?>
<!DOCTYPE الإصدار SYSTEM "../../lib/pkp/dtd/pluginVersion. td">
<version>
    <application>نموذج تعليمي</application>
    <type>الملحقات. نومينيك</type>
    <release>0.1.0.</release>
    <date>2019-05-15</date>
    <lazy-load>1</lazy-load>
    <class>البرنامج المساعد التعليمي</class>
</version>
```

`<application>` يجب أن يطابق اسم الدليل. `<type>` يجب أن يكون القسم الخاص بالبرنامج المساعد [](./categories). `<class>` يجب أن يتطابق مع اسم الصف الخاص بالبرنامج المساعد.

## TutorialexamplePlugin.inc.php

يجب أن يكون لكل ملحق فصل يسجل ويدير الملحق.

```php
<?php
استيراد ('lib.pkp.classes.plugins. نيركبلوجين)؛
البرنامج التعليمي المثل الإضافي يوسع برنامج GenericPlugin
    سجل الدالة العامة$category، $path، $mainContextId = NULL) {

    // سجل الملحق حتى عندما لا يتم تمكينه
    $success = parent::register($category, $path)؛

        إذا كان ($success && $this->getEnabled()) {
      // قم بشيء عندما يتم تمكين الملحق
    }

        العودة $success;
    }

  /**
   * قدم اسم لهذه الإضافة
   *
   * الاسم سوف يظهر في قائمة الملحقات حيث يمكن للمحررين
   * تمكين وتعطيل الملحقات.
   */
    وظيفة عامة getDisplayName() {
        إرجاع 'مثال تعليمي';
    }

    /**
   * قدم وصفاً لهذه الإضافة
   *
   * سيظهر الوصف في قائمة الإضافات حيث يمكن للمحررين
   * تمكين وتعطيل الإضافات.
   */
    وظيفة عامة getDescription() {
        إرجاع 'هذا البرنامج المساعد هو مثال تم إنشاؤه لدرس تعليمي حول كيفية إنشاء البرنامج الإضافي. ;
    }
}
```

## index.php

الملف `index.php` مطلوب لتحميل فئة الإضافات الصحيحة.

```php
<?php
require_once('TutorialExamplePlugin.inc.php');
إرجاع البرنامج التعليمي الجديد tutorialExamplePlugin();
```

انتقل إلى الإعدادات > الموقع > الإضافات ومحاولة تمكين وتعطيل الإضافات الخاصة بك. إذا كان هناك خطأ عند تمكينه، تحقق من المكون الإضافي الخاص بك مقابل [مثال العمل](https://github.com/pkp/tutorialExample)

---

تعلم كيفية اختيار الفئة [الإضافية الصحيحة](./categories) للملحقة الخاصة بك.
