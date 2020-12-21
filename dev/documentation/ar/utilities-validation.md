---
title: التحقق - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# المصادقة

يمكن التحقق من صحة البيانات باستخدام [مخطط الكيان](./architecture-entities#schemas) أو `مصنع Validatortory`. في كلتا الحالتين، نحن نستخدم مكتبة Laravel [للتحقق من صحة](https://laravel.com/docs/5.5/validation).

> جميع قواعد التحقق [الخاصة بلارفيل](https://laravel.com/docs/5.5/validation#available-validation-rules) مدعومة باستثناء `قاعدة` موجودة. 
> 
> {:.notice}

## مصنع المصادقة

فئة `ValidatorFactory` هي مغلفة لـ [Laravel's](https://laravel.com/docs/5.5/validation). إنه محاكاة لـ Laravel's `يجعل` طريقة لإنشاء متحقق من الصحة.

```php
$validator = ValidatorFactory::make($props، $rules)؛
```

قم بتشغيل المصادقة واسترجاع الأخطاء.

```php
إذا كان ($validator->فشلات()) {
  $errors = $validator->الأخطاء();
}
```

التحقق من قيمة واحدة.

```php
$props = ['contactEmail' => $userEmail];
$rules = ['contactEmail' => ['email_or_localhost']];
$validator = ValidatorFactory::make($props، $rules)؛
```

أو التحقق من صحة أكثر من قيمة واحدة في المرة الواحدة.

```php
$props = [
  'جهة الاتصال' => $userEmail،
  'اسم جهة الاتصال' => $userName،
]؛
$rules = [
  'contactEmail' => ['email_or_localhost']،
  'contactUsername' => ['alpha_num']،
]؛
$validator = ValidatorFactory::make($props، $rules)؛
```

سيقوم المصادقة بإرجاع أخطاء مفيدة عندما لا تكون القيمة صحيحة. إذا أردت ، يمكنك تخصيص هذه الرسائل عن طريق تمرير حجة إضافية.

```php
$props = ['اسم جهة الاتصال' => $userName]؛
$rules = ['contactUsername' => ['min:6', 'alpha_num']];
$messages = ['contactUsername. في' => 'يجب أن يكون اسم مستخدم جهة الاتصال بالمجلة 6 أحرف على الأقل. ];
$validator = ValidatorFactory::make($props، $rules، $messages)؛
```

## المصادقة على المخطط

يمكن تعريف قواعد التحقق في مخطط الكيان [](./architecture-entities#schemas). في هذا المثال ، `numAnnouncementsHomage` يجب أن يكون عدد صحيح ليس سلبيا.

```json
{
  "numAnnouncementsHomage": {
    "type": "عدد صحيح"،
    "validation": [
      "nullable"،
      "min:0"
    ]
  }
}
```

سيتم تطبيق هذه القواعد عندما يقوم قسم [الخدمة](./architecture-services) في الكيان بالتحقق من صحة إدخال المستخدم الذي يحتوي على `prop numAnnouncementsHomage`. شاهد قسم [التحقق من صحة الخدمة](#service-validation) أدناه.

كل خاصية يمكن أن تكون فارغة أو باطلة يجب أن تكون قاعدة التحقق `غير قابلة للإلغاء` تم تعيينها، أو أنها سترمي خطأ عندما يكون فارغاً.

```json
{
  "البريد": {
    "النوع": "سلسلة"،
    "التحقق": [
      "nullable"
    ]
  }
}
```

> لا تحتاج أبدا إلى إضافة `أصفيف`أو `منطقي`أو `عدد صحيح` أو `سلسلة` قواعد التحقق. سيتم تطبيق هذه تلقائياً استناداً إلى خاصية `نوع`. 
> 
> {:.notice}

## التحقق من الخدمة

يجب على فئة [الخدمة](./architecture-services) في كيان ما تطبيق `طريقة التحقق` التي تحقق من صحة الميزات ضد المخطط. استخدم `خدمة المخطط` للوصول إلى أساليب المساعد للعمل مع المخطط.

```php
صف PKPContextService يعمل EntityWriteInterface {
    /**
     * @copydoc \PKP\Services\EntityProperties\EntityWriteInterface::validate()
     */
    التحقق من صحة الوظيفة العامة$action، $props، $allowedLocales، $primaryLocale) {
        $schemaService = الخدمات:get('schema');
        الاستيراد('lib. kp.classes.validation. مصنع alidator'؛
        $validator = \ValidatorFactory::make(
            $props,
      $schemaService->getValidationRules(SCHEMA_CONTEXT, $allowedLocales)
    )؛
  }
}
```

يتضمن `خدمة المخطط` طريقة مساعد للتحقق من صحة الحقول المطلوبة.

```php
إذا ($action === VALIDATE_ACTION_ADD) {
  \ValidatorFactory::required(
    $validator,
    $schemaService->مطلوب بروبس(SCHEMA_CONTEXT)،
    $schemaService->تعدد اللغات في البرامج (SCHEMA_CONTEXT)،
    $primaryLocale
  )؛
}
```

طريقة المساعد `المسموح بها` سوف ترفع خطأ إذا تم توفير القيم لأي لغة غير مدعومة بالمجلة أو الضغط.

```php
\ValidatorFactory::allowedLocales(
  $validator,
  $schemaService->getMultiingualProps(SCHEMA_CONTEXT),
  $allowedLocales
);
```

طريقة المساعد `المطلوبة PrimaryLocale` ستتحقق من صحة المزايا التي يجب أن تكون مطلوبة في المحلية الأساسية، ولكن غير مطلوبة في بلديات أخرى.


```php
// يتطلب اسم مجلة ليتم توفيره في الموقع الرئيسي
\ValidatorFactory::requirePrimaryLocale(
  $validator,
  ['name']،
  $props،
  $allowedLocales،
  $primaryLocale
)؛
```

ولا يمكن وصف بعض قواعد التحقق في المخطط. وهذا هو الحال عندما يتطلب التحقق من صحة قاعدة البيانات. على سبيل المثال، السياق لا يمكن أن يحتوي على `urlPpath` إذا كان هناك سياق آخر مع ذلك `urlPath`.

In such cases, the [Service](./architecture-services) class's `validate` method should be used to extend the validation check.

```php
التحقق من صحة الدالة ($action، $props، $allowedLocales، $primaryLocale) {
  $schemaService = الخدمات:get('schema');
  الاستيراد('lib. kp.classes.validation. مصنع alidator'؛
  $validator = \ValidatorFactory::make(
    $props,
    $schemaService->getValidationRules(SCHEMA_CONTEXT, $allowedLocales)
  )؛

...

  // تأكد من أن urlPath، في حالة تقديمه، غير موجود بالفعل
  $validator->بعد (function($validator) الاستخدام ($action, $props) {
    إذا (isset($props['urlPath']) && !$validator->الأخطاء()->get('urlPath')) {
      $contextDao = التطبيق: :getContextDAO();
      $contextWithPath = $contextDao->getByPath($props['urlPath'])؛
      إذا كان ($contextWithPath) {
        إذا (!$action === VALIDATE_ACTION_EDIT
            && isset($props['id'])
            && (int) $contextWithPath->getId() == $props['id'])) {
          $validator->الأخطاء ()->إضافة ('urlPath', __('مدير'. ontexts.form. الرياضيون))؛
        }

    }
  })؛

...

  إذا ($validator->فشل()) {
...
  }
}
```

## قواعد مخصصة

أضاف OJS و OMP قواعد التحقق المخصصة لـ ISSN، ORCID، وأكثر من ذلك. ويمكن تطبيق هذه القواعد في المخطط.

```json
{
  "onlineIssn": {
    "type": "سلسلة"،
    "validation": [
      "nullable"،
      "issn"
    ]
  }
}
```

وقد أضيفت القواعد التالية:

- `email_or_localhost` - التحقق من صحة البريد الإلكتروني الخاص بلارفيل `` لقبول رسائل البريد الإلكتروني `@localhost`.
- `issn` - تتطلب [ISSN صالحة](https://www.issn.org/).
- `orcid` - يتطلب [ORCID صالح](https://orcid.org/).
- `العملة` - يتطلب رمز عملة صالح.
