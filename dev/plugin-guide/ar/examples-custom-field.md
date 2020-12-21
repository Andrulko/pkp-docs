---
title: مثال - إضافة حقول مخصصة - دليل الإضافات لOJS و OMP
---

# إضافة حقول مخصصة

يمكن أن تضيف الإضافات خصائص إلى أي كيان يستخدم ملف مخطط وتعديل النماذج لتشمل حقول الإدخال لهذه الخواص.

> تعرف على المزيد حول [كيانات](/dev/documentation/en/architecture-entities) و [مخططات](/dev/documentation/en/architecture-entities#schemas). 
> 
> {:.notice}

في المثال أدناه، نضيف حقل `مؤسسة` إلى المجلة أو إعدادات الضغط. وسيتيح ذلك للمحرر تحديد الجهة الداعمة المؤسسية أو الجهة الداعمة التي يمكن استخدامها بعد ذلك في موضوع المجلة أو الصحافة.

```php
صف مؤسسة-HomePlugin يمدد GenericPlugin {

  سجل الوظائف العامة($category، $path، $mainContextId = فارغ
        $success = الوالد::register($category، $path)؛
        إذا ($success && $this->getEnabled()) {

      // استخدم رابط لتوسيع مخطط كيان السياق
      Hookregistry:register('Schema::get::context', المصفوفة($this، 'addToSchema'))؛

      // استخدام الرابط لإضافة حقل إلى نموذج المتقن في إعدادات الصحف/الضغط.
      Hookregistry::register('Form::config::bepre', ary($this, 'addToForm'))؛
        }
        إرجاع $success؛
  }

  /**
   * توسيع مخطط الكيان السياقي مع ممتلكات منزلية مؤسسية
   */
  وظيفة إضافية ($hookName، $args{
        $schema = $args[0]؛
        $schema->خصائص ->مؤسسة البيت = (كائن) [
            'نوع' => 'سلسلة',
            'apiSummary' => صحيح،
            'تعدد اللغات' => صحيح،
            'المصادقة' => ['nullable']
        ]؛
  }

  /**
   * قم بتوسيع نموذج الترميز لإضافة حقل مدخل مؤسسي منزلي
   * في إعدادات صحف/الصحافة
   */
    إضافة وظيفة عامة ($hookName, $form) {

    // فقط تعديل نموذج الملمس
        إذا (! efined('FORM_MASTHEAD') <unk> $form->id ! = FORM_MASTHEAD) {
            العودة؛
    }

    // لا تفعل أي شيء على مستوى الموقع كله
        $context = التطبيق: :getrequest()->getContext();
        إذا (!$context) {
            العودة؛
    }

    // إضافة حقل إلى النموذج
        $form->addField(جديد \PKP\components\forms\FieldText('institutionalHome', [
            'التسمية' => 'المنزل المؤسسي'،
            'مجموعة' => 'النشر'،
            'قيمة' => $context->getData('institutionalHome')،
        ])؛
    }
}
```

عندما يضيف المحرر منزل مؤسسي في المجلة أو يضغط على الإعدادات، يمكنك استرجاعه من فئة `DataObobjec` للسياق.

```php
$context = تطبيق::get()->getrequest()->getContext();
$institutionalHome = $context->getLocalizedData('institutionalHome');
```

أو استخدمه في قالب على واجهة القارئ.

```html
<p>البيت المؤسسي: {$currentContext->getLocalizedData('institutionalHome')}</p>
```

---

عرض المزيد من [الأمثلة](./examples).
