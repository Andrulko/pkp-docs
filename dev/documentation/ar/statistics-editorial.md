---
title: إحصاءات التحرير - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# إحصائيات التحرير

وتشير إحصاءات التحرير إلى النشاط التحريري لمجلة أو صحافة. يساعدك تحرير إحصائيات [خدمة](architecture-services.md) في حساب البيانات المقدمة المتلقاة والمقبولة والمنشورة، وطول المدة التي يجب على المؤلفين الانتظار لاتخاذ قرارات التحرير.

احصل على عدد من العروض المتلقاة من صحيفة واحدة.

```php
$received = الخدمات: :get('editorialStats')
    ->countSubmissionsreceieived([
        'contextIds' => [1]
])؛
```

احصل على عدد من العروض التي تلقتها صحيفة واحدة في كانون الثاني/يناير 2020.

```php
$received = خدمات: :get('editorialStats')
    ->countSubmissionsreceieived([
        'contextIds' = [1],
        'dateStart' => '2020-01-01',
        'dateEnd' => '2020-01-31',
])؛
```

احصل على عدد من التقديمات المقبولة من صحيفة واحدة.

```php
$accepted = الخدمات::get('editorialStats')
    ->countByDecisions(
        SUBMISSION_EDITOR_DECISION_ACCEPT ،
        [
            'contextIds' = [1]،
        ]
)؛
```

مرر واحدا أو أكثر من `SUBMISSION_EDITOR_DECISION_` ثابتا لحساب العروض التي تم رفض أو رفض المكتب بعد مراجعة الأقران.

> لا تستخدم `countSubmissionsreceieived()` و `countByDecisions()` لحساب معدلات القبول والرفض. وقد يكون الطلب قد ورد ولكنه لم يقبل أو يرفض بعد، وكثيرا ما تتخذ القرارات بعد مرور أكثر من سنة على تقديمه. 
> 
> {:.warning}

Use `countByDecisionsForSubmittedDate()` to calculate acceptance and rejection rates.

```php
$args = ['سياقات' => [1]];
$accepted = $this->countByDecisionsForSubmitteddate(SUBMISSION_EDITOR_DECISION_ACCEPT, $args)؛
$declined = $this->countByDecisionsForSubmitteddate([SUBMISSION_EDITOR_DECISION_INITIAL_DECLINE، SUBMISSION_EDITOR_DECLINE]، $args)؛
$total = $accepted + $declined؛

$acceptanceRate = $accepted / $total؛
$rejectionRate = $declined / $total؛
```

احصل على عدد الأيام التي استغرقها كل طلب مقبول للتوصل إلى قراره النهائي.

```php
$acceptDays = $this->getDaysToDecisions
    [
        SUBMISSION_EDITOR_DECISION_SEND_TO_PRODUCTION,
        SUBMISSION_EDITOR_DECISION_ACCEPT
    ]،
    ['contextIds' => [1]]
)؛
```

حساب المتوسط.

```php
$average = المصفوفة_sum($acceptDays) / العد ($acceptDays)؛
```

أو حساب معدل القبول الذي يسمح لك بالإبلاغ عن إحصائيات أكثر فائدة للمؤلفين.

```php
// 80% من العروض المقبولة تتلقى هذا القرار خلال
// <$rate> عدد الأيام.
$rate = $this->حساب DaysToDecisionRate($acceptDays، 0.8)؛
```

يتضمن فصل `PKPStatsEditorialService` طرق حساب التقديمات حسب الحالة أو مرحلة سير العمل.

اقرأ كتلة الدوك لكل طريقة لفهم كيفية حساب الإحصاءات بوضوح. على وجه الخصوص، يتم تطبيق حجج `dateStart` و `dateEnd` بشكل مختلف لكل طريقة.
