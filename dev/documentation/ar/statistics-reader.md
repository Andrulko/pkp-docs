---
title: إحصاءات القارئ - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# إحصائيات القارئ

يقدم OJS و OMP فئات [الخدمة](architecture-services.md) لمساعدتك على استرداد وحساب الإحصاءات حول التثبيت الخاص بك.

تشير إحصائيات القارئ إلى نشاط المستخدمين الذين يزورون موقع القارئ الخاص بالمجلة أو الصحافة. ويجري تخزين المجاميع اليومية والشهرية للزوار في كل سياق وقسم وصفحة إنزال المقالات ووادي المقالات.

يتم تجميع هذه البيانات يومياً من سجلات الخادم وتخزينها في جدول `قياسات`. يمثل كل صف في الجدول مجموع الزيارات لعنصر واحد (مقالة أو وادي أو مجلة) ليوم واحد أو شهر.

## الحصول على السجلات وحساب المجاميع

احصل على جميع السجلات المتعلقة بصفحة هبوط مقالة لمجلة واحدة خلال الأشهر الثلاثة الأولى من السنة.

```php
$records = الخدمات::get('stats')->getRecords([
    'contextIds=> [1],
    'dateEnd' => '2020-03-31',
    'dateStart' => '2020-01-01',
    'assocTypes' => [ASSOC_TYPE_SUBMISSION]،
])؛
```

أضف السجلات للحصول على العد الإجمالي لجميع الطلبات المقدمة.

```php
$views = array_reduce(
    $records,
    [Services:get('stats'), 'sumMetric'],
    0
)؛
```

`SocType` قد يكون السياق (`ASSOC_TYPE_CONTEXT`)، صفحة هبوط مقالة (`ASSOC_TYPE_SUBMISSION`) أو أودية مقالة (`ASSOC_TYPE_SUBMISSION_FILE`).

احصل على جميع السجلات لودالات PDF لمقالة واحدة.

```php
$records = الخدمات::get('stats')->getRecords([
    'contextIds=> [1],
    'تقديم' => [1]،
    'assocTypes' => [ASSOC_TYPE_SUBMISSION_FILE]،
    'fileTypes' => [STATISTICS_FILE_TYPE_PDF]،
])؛
```

و أضفهم

```php
$views = array_reduce(
    $records,
    [Services:get('stats'), 'sumMetric'],
    0
)؛
```

أو احصل على جميع السجلات لأي من والات المقالة.

```php
$records = الخدمات: :get('stats')->getRecords([
    'contextIds' => [1]،
    'submissionIds' => [1]،
    'assocTypes' => [ASSOC_TYPE_SUBMISSION_FILE]،
])؛
```

قم بتصفيتهم حسب نوع الملف.

```php
$pdfRecords = array_Filter($records، [الخدمات:get('stats')، 'FilterRecordPdf'])؛
$htmlRecords = array_filter($records، [الخدمات:get('stats')، 'FilterRecordHtml'])؛
$otherRecords = array_filter($records، [الخدمات:get('stats')، 'filterRecordOther'])؛
```

وإضافة كل نوع من الملفات.

```php
$pdfViews = array_reduce($pdfRecords، [الخدمات:get('stats')، 'sumMetric'، 0)؛
$htmlViews = array_reduce($htmlRecords، [الخدمات:get('stats')، 'sumMetric'، 0)؛
$otherViews = المصفوفة_reduce($otherRecords، [الخدمات:get('الإحصائيات')، 'sumMetric'، 0)؛
```

طريقة `getRecords()` تقبل عدة حجج لتصفية النتائج. ويشمل الرمز المصدري وثائق أكثر اكتمالا.

## احصل على قائمة من الكائنات مرتبة حسب احصائياتهم الإجمالية

احصل على قائمة بأعلى 10 مقالات من خلال مجموع الزيارات لصفحتها وهبوطها والوديان في مارس 2020.

```php
$topSubmissions = خدمات::get('stats')->getOrderedObjects(
    STATISTICS_DIMENSION_SUBMISSION_ID,
    STATISTICS_ORDER_DESC،
    [
        'سياق` => [1]،
        'dateEnd' => '2020-03-31',
        'dateStart' => '2020-03-01',
        'عد' => 10،
        'خصم' = 0،
    ]
)؛
```

هذا سوف يعيد صفيفة جمعية.

```
[
    ['id' => 213، 'المجموع' => 2314]،
    ['id' => 431، 'المجموع' => 2139]،
    ['id' => 132، 'المجموع' => 2002]،
    ['id' => 321، 'المجموع' => 1987]،
    ['id' => 753، 'المجموع' => 1932]،
    ['id' => 642، 'المجموع' => 1845]،
    ['id' => 243، 'المجموع' => 1653]،
    ['id' => 532، 'المجموع' => 1652]،
    ['id' => 120، 'المجموع' => 1420]،
    ['id' => 193، 'المجموع' => 1201]،
]
```

احصل على قائمة بأعلى 10 مجلات من خلال مجموع الزيارات لأي مقالة مرتبطة بالمجلة.

```php
$topContexts = الخدمات::get('stats')->getOrderedObjects(
    STATISTICS_DIMENSION_CONTEXT_ID,
    STATISTICS_ORDER_DESC,
    [
        'count' => 10,
        'offset' = 0,
    ]
)؛
```

تقبل هذه الطريقة جميع الخصائص نفسها مثل `getRecords()` لتصفية النتائج.

## الحصول على مجموع الزيارات موزعة حسب اليوم أو الشهر

احصل على عدد شهري من الزيارات لجميع صفحات تسجيل المقالات في المجلة.

```php
$timeline = الخدمات::get('stats')->getTimeline(
    STATISTICS_DIMENSION_MONTH,
    [
        'السياق' => [1]،
        'الأنواع المسقطة' = [ASSOC_TYPE_SUBMISSION]،
        'dateEnd' => '2020-12-31',
        'dateStart' => '2020-01-01',
    ]
)؛
```

هذا سوف يعيد صفيفة جمعية.

```
[
    [
        'التاريخ' => '2020-01',
        'تسمية' => 'يناير' 2020',
        'قيمة' => 5313
    ]،
    [
        'التاريخ' => '2020-02',
        'العلامة' => 'فبراير' 2020',
        'قيمة' => 4364,
    ]،
    [
        'التاريخ' => '2020-03',
        'علامة' => 'مارس،20',
        'قيمة' => 6301،
    ]،
...
]
```

احصل على عدد يومي من الزيارات إلى صفحة هبوط أحد المقالات.

```php
$timeline = الخدمات::get('stats')->getTimeline(
    STATISTICS_DIMENSION_DAY،
    [
        'السياق' => [1]،
        'تقديم' => [21]،
        'assocTypes' = [ASSOC_TYPE_SUBMISSION]،
        'dateEnd' => '2020-01-31',
        'dateStart' => '2020-01-01',
    ]
)؛
```

تقبل هذه الطريقة جميع الخصائص نفسها مثل `getRecords()` لتصفية النتائج.
