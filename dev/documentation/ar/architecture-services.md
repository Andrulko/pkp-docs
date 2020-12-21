---
title: الخدمات - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# الخدمات

فئة `الخدمة` هي حاوية لتخزين الطرق القابلة لإعادة الاستخدام. يقوم بإحداثيات [الكيانات](./architecture-entities)، [`DAO`s](./architecture-database)، والمنافع الأخرى للقراءة والكتابة من قاعدة البيانات، وإرسال رسائل البريد الإلكتروني، وإطلاق النار في الأحداث.

وتعزل فئات الخدمات المنطق التجاري للإجراءات المتخذة في الطلب عن المتعاملين الذين يتلقون الطلب ويستجيبون له. يجب أن يكون من الممكن استخدام طريقة فئة الخدمة من `PageHandler`أو `APIHandler`أو حتى أمر CLI.

> والخدمات جديدة على التطبيق وليست متاحة بعد لجميع الكيانات. اقرأ عن استراتيجية [إعادة المفاعلة](#refactor-strategy). 
> 
> {:.notice}

## استخدام خدمة

من الممكن الحصول على الخدمة من أي مكان في الطلب.

```php
$contextService = الخدمات: :get('context');
```

يمكن العثور على الخدمات المتاحة في `OJSServiceProvder` و `OMPServiceProvder`.

## خدمات الكيان

عادة ما تقترن فئة `الخدمة` بـ [كيان](./architecture-entities) وتوفر جميع الطرق للحصول عليها، إضافة وتحرير وحذف هذا الكيان.

كل فئة خدمة من فئات الكيانات ستنفذ وصلة أو أكثر تحدد الأساليب المتاحة.

### واجهة EntityReadad

يوفر `EntityReadInterface` طريقة `get()` للحصول على كائن واحد.

```php
$context = الخدمات: :get('context')->get($contextId);
```

ويوفر أيضا عددا من الطرق التي يمكن استخدامها لاسترداد النتائج المصفاة بواحد أو أكثر من البارامترات.

استخدم طريقة `getCount()` لاسترداد عدد من الكائنات المطابقة للمعلمات المحددة.

```php
$numberOfEnabledContexts = الخدمات::get('context')->getCount([
  'isenable' => true,
])؛
```

استخدم طريقة `getIds()` لاسترداد مجموعة من معارف الكائنات.

```php
$enabledContextIds = الخدمات::get('context')->getIds([
  'isEnable' => true,
])؛
```

استخدم طريقة `getMany()` لاسترداد محرر الكائنات.

```php
$contextsIterator = الخدمات::get('context')->getMany([
  'isEnable' => true,
])؛
```

اجتياز معلمات `عد` و `إزاحة` لصفحة النتائج. يوضح المثال أدناه كيفية الحصول على عشرة عناصر بدءاً من الصفحة الثانية من النتائج.

```php
$contextsIterator = الخدمات: :get('context')->getMany([
  'count' => 10,
  'offset' => 10,
])؛
```

`getCount()`و `getIds()` و `getMany()` طرق تقبل جميعها نفس المعلمات. هذه مختلفة لكل [كيان](architecture-entities) ويمكن اكتشافها من خلال قراءة مستندات طريقة `getMany()` فئة الخدمات.

ترجع طريقة `getMany()` `DAOResultIterator` (انظر [Iterators](https://www.php.net/manual/en/class.iterator.php)). يمكن استخدام الترميز مثل مصفوفة في `الحلقات التمهيدية` حلقات:

```php
$contextsIterator = الخدمات::get('context')->getMany(['isEnable' => true]);
$names = []؛
التمهيد ($contextsIterator ك $context) {
    $names[] = $context->getLocalizedData('name')؛
}
```

ومع ذلك، لا يمكن التكرار في `DAOResultIterator` مرتين. سيؤدي هذا إلى خطأ مميت.

```php
$names = [];
$paths = [];
$contextsIterator = الخدمات:get('السياقات')->getMany(['isEnable' => true])؛
الأسبق ($contextsIterator ك $context) {
    $names[] = $context->getLocalizedData('name')؛
}
// / تم تكرير المحرر بالفعل على
// من قبل لذلك سيؤدي هذا إلى خطأ
الترجيح ($contextsIterator ك $context) {
    $paths[] = $context->getData('urlPath')؛
}
```

للتحقق مما إذا لم يتم إرجاع أي نتائج، استخدم `count()` بدلاً من `!فارغة()`.

```php
$contextsIterator = الخدمات::get('سياقات')->getMany(['isEnable' => true]);
if (! فارغة($contextsIterator)) {
    // سيكون هذا صحيحا دائما
}
إذا (عدد($contextsIterator)) {
    // فقط إذا تم العثور على سياق واحد أو أكثر
}
```

لا يمكن استخدام `DAOResultIterator` مع `array_map`أو `array_Filter` أو `array_reduction`.

إذا لزم الأمر، `DAOResultIterator` يمكن تحويله إلى صفيف.

```php
$contextsIterator = خدمات: :get('سياقات')->getMany(['isEnable' => true]);
$contexts = iterator_to_array($contextsIterator);
```

غير أنه ينبغي تجنب ذلك ما لم تكن هناك ضرورة مطلقة. تخزين مجموعة كبيرة من الكائنات في الذاكرة سيبطئ التطبيق. إذا لم تكن متأكدا، اسأل مطورا أقدم في الفريق.

### واجهة EntityWriteInterface

يوفر `EntityWriteInterface` أساليب للتحقق من الكائنات وإضافتها وتحريرها وحذفها.

قبل إضافة أو تحرير كائن، يجب عليك التحقق من صفاته. انظر [المصادقة](./utilities-validation).

```php
$props = ['path' => 'publicknowledge'];
$errors = الخدمات: :get('context')->المصادقة (
  VALIDATE_ACTION_ADD,
  $props,
  التطبيق::get()->getSite()->getSupportedLocales(),
  Application:get()->getSite()->getPrimaryLocale(),
)؛
إذا (! قطعة($errors)) {
  // فشل التحقق من صحة: يتطلب بروب 'name'
}
```

بمجرد التحقق من الخصائص ، يمكن دمجها مع الكائن وحفظها.

تحرير كائن موجود.

```php
$editedContext = الخدمات::get('context')->edit(
  $context,
  $props,
  Application:get()->getrequest()
);
```

لإضافة كائن، استخدم DAO لتمثيل كائن جديد، وحقن الروبوتات، وحفظه في قاعدة البيانات.

```php
$context = تطبيق::get()->getContextDAO()->newDataObject();
$context->_data = $props؛
$newContext = الخدمات: :get('context')->إضافة (
  $context،
  تطبيق:get()->getrequest()
)؛
```

حذف كائن.

```php
الخدمات::get('context')->حذف($context)؛
```

### واجهة EntityPropertyInterface

يوفر `EntityPropertyInterface` أساليب لتحويل كائن ما إلى صفيف ترابكي. يستخدم هذا قبل إعادة البيانات كقاعدة بيانات JSON في REST API و CLI.

استخدم طريقة `getSummaryProperties()` لاسترداد ملخص الكائن.

```php
$contextProps = الخدمات: :get('context')
  ->getSummaryProperties(
    $context,
    ['request' => Application:get()->getrequest()]
)؛
```

استخدم طريقة `getFullProperties()` لاسترداد تمثيل كامل للكائن.

```php
$contextProps = الخدمات: :get('context')
  ->getFullProperties(
    $context,
    ['request' => Application:get()->getrequest()]
)؛
```

سوف تتضمن الخصائص الكاملة في بعض الأحيان تفاصيل عن الكائنات الملحقة. على سبيل المثال، عنصر التقديم سوف يرفق كائنات المؤلف.

يمكنك طلب الخصائص التي تريدها باستخدام طريقة `getProperties()`.

```php
$contextProps = الخدمات::get('context')
  ->getProperties(
    $context,
    ['name', 'path', 'url']
    ['request' => Application:get()->getrequest()]
)؛
```

هذا سوف يعيد صفيفة جمعية.

```
[
    'name' => [
        'en_US' => 'Journal of Public Knowledge'
    ]
  'path' => 'publicledge',
    'url' => 'http://localhost:8000/publicknowledge'
]
```

### أساليب إضافية

ويجوز لكل فئة خدمة أن تتضمن أساليب إضافية حسب الحاجة. على سبيل المثال، يشمل صف `PKPContextService` طريقة لاستعادة جميع الإعدادات الافتراضية للمحليات.

```php
$updatedContext = الخدمات::get('context')
  ->restoreLocaleDefaults(
    $context,
    $request,
    $locale
)؛
```

## الخدمات الأخرى

في حالات نادرة، قد لا تقترن فئة الخدمة `` بـ [كيان](./architecture-entities). على سبيل المثال، يوفر `مخطط الخدمة` أساليب لتجميع خطط الكيانات والعمل معها.

```php
// شغل كائن مع القيم الافتراضية من مخططه
$contextWithDefaults = الخدمات: get('schema')
  ->setDefaults(
    SCHEMA_CONTEXT
    $newContext،
    $supportedLocales،
    $primaryLocale
)؛
```

وقد تكون خدمات أخرى متصلة بكيان ما، ولكنها لا تدعم بعد الوصلات البينية للكيان. راجع استراتيجية [إعادة المفاعل](#refactor-strategy).

## فئات خدمة الكتابة

يجب أن تكون فئة `الخدمة` جيدة:

- **عديم الجنسية**: في كل مرة يتم فيها استدعاء طريقة فئة الخدمة يجب أن تكون مستقلة تماما عن أي عمليات سابقة. لا تقم بإرفاق أشياء للمثيل مع `$this`. وينبغي حقن جميع التبعيات لأسلوب فئة الخدمة كمعامل لتلك الطريقة.
- **سهل الاستخدام**: حاول إخفاء متطلبات قاعدة البيانات المعقدة ومنطق العمل وراء توقيعات طريقة بديهية.
- **إعادة الاستخدام**: تفكير في جميع السيناريوهات التي قد تستخدم فيها طريقة. حاول فصله عن حالة الاستخدام الخاصة بك كلما كان ذلك ممكناً.

## استراتيجية إعادة الإنتاج

الخدمات جديدة على الطلب. وننوي نقل الرمز إلى فئات الخدمة الموجودة حاليا في مناولي الصفحات، والمتعاملين مع المراقبين، والنماذج. والقضية الرئيسية المستخدمة في هذا التغيير هي دعم REST API.

ولهذا العامل ثلاثة أهداف:

1. لفصل منطق العمل عن مكونات واجهة المستخدم وطلب المعالجين. يجب أن نكون قادرين على الحصول على الأشياء وإضافتها وتحريرها من أي مكان في التطبيق.
2. • تعزيز الاستخدام المتسق للروابط والإخطارات. لا ينبغي أن يكون من الممكن نسيان الاتصال بالروابط، أو إرسال إشعارات البريد الإلكتروني، أو إضافة إدخالات السجل عند اتخاذ الإجراءات. وينبغي أن تتضمن فئة الخدمة جميع المهام التي تشكل جزءا من أي إجراء.
3. 1 - تبسيط هيكل الطلب. نأمل أن توفر فئات الخدمة API أكثر بديهية لمطوري الإضافات والشركاء من أطراف ثالثة.

ففصول الخدمة ليست متاحة بعد لجميع الكيانات. سيتم تطويرها مع تحويل المزيد من واجهة المستخدم الخاصة بنا إلى استخدام REST API.

---

تعرف على المزيد حول [كيفية تعريف الكيانات والتعامل معها](./architecture-entities).
