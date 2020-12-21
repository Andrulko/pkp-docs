---
title: نسخ النشر - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# إصدارات النشر

وتحافظ على التغييرات التي تطبق على المنشور بعد نشره في نسخ مختلفة. ولكل نسخة عنوانها الخاص بها والبيانات الفوقية والمساهمين والودان.

عند العمل مع التقديم، يجب توخي الحذر للتأكد من أنك تعمل مع الإصدار الصحيح. عادة ما يكون هذا هو أحدث إصدار منشور، ولكن هذا قد لا يكون هو الحال في سير أعمال التحرير أو في السيناريوهات التي يجب فيها تناول جميع النسخ.

## النشر الحالي

يتم تخزين تفاصيل المنشور `المقدم`في `عناصر النشر` ويمكن استرجاعها عن طريق الوصول إلى المنشور الحالي.

```php
// احصل على عنوان الإصدار الحالي
$title = $submission
    ->getcurrentPublication()
    ->getLocalizedFullTitle();
```

ويشير المنشور الحالي إلى أحدث نسخة منشورة. إذا لم يتم نشر التقديم بعد، فإن المنشور الحالي سيكون أحدث إصدار تم إنشاؤه.

## التغييرات بعد النشر

لا يمكن تحرير المنشور بعد نشره. لإجراء تغييرات، يجب إنشاء نسخة جديدة وتحريرها ونشرها.

```php
// إنشاء إصدار جديد
$newPublication = الخدمات: :get('publication')->الإصدار
    $submission->getcurrentPublication(),
    $request
)؛

// تحرير الإصدار الجديد
$newPublication = الخدمات:get('publication')->edit(
    $newPublication,
    ['datePublished' => '2020-01-15']،
    $request
)؛

// نشر النسخة الجديدة
$newPublication = الخدمات:get('publication')->publish(
    $newPublication
)؛
```

وتشمل فئة خدمات النشر عددا من الطرق الإضافية للمساعدة في النشر وإصدار العروض.

- `PKPPublication::version()` سينشئ نسخة جديدة من منشور موجود.
- `PKPPublication::validatePublish()` سيقوم بفحص ما قبل النشر للتأكد من أن النشر جاهز للنشر.
- `PKPPublication::publish()` سيقوم بنشر منشور، وتحديث الحالة، وإنشاء إدخالات السجل المناسبة.
- `PKPPublication::unpublish()` سوف يلغي نشر المنشور.

## العمل مع الإصدارات

احصل على أحدث منشور تم إنشاؤه عندما تريد استرداد أحدث إصدار بغض النظر عما إذا كان منشورا أو غير منشور.

```php
$latestPublication = $submission->getLatestPublication();
```

احصل على جميع إصدارات الإرسال التي تم نشرها.

```php
$publishedPublications = $submission->getPublishedPublications();
```

احصل على جميع إصدارات التقديم.

```php
$publications = $submission->getData('publications');
```

## تحديد الإصدارات

عند عرض قائمة من إصدارات الإرسال في واجهة المستخدم، يجب أن يتم تحديدها بواسطة خصائصهم `datepublished` و `الإصدار` الخاص بهم.

```php
الطبقة ($submission->getData('publications') ك $publication) {
    صدى __('تقديم'. ersionIdentity', [
        'datePublished' => $publication->getData('datePublished'),
        'الإصدار' => $publication->getData('version'),
    ])؛

// ينتج ما يلي:
//2019-11-13 (1)
// 2020-02-03 (2)
// 2020-05-16 (3)
```

## خواص التقديم

تم إهمال طرق المصراع والطرق في كائن `التقديم` التي تحصل على أو تعيين البيانات المرفقة بـ `النشر`. لا ينبغي استخدام الرمز التالي.

```php
// مهملة. لا تستخدم
$title = $submission->getLocalizedFullTitle();
```

استخدم التعليمة البرمجية التالية بدلاً من ذلك.

```php
$title = $submission
    ->getcurrentPublication()
    ->getLocalizedFullTitle();
```