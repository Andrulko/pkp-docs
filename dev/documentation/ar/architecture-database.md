---
title: قاعدة البيانات - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# قاعدة البيانات

كائن الوصول إلى قاعدة البيانات (`DAO`) هو المسؤول عن تنفيذ استفسارات قاعدة البيانات لقراءة المعلومات وكتابتها من قاعدة البيانات.

> تطبيقات PKP تدعم MySQL و PostgreSQL. 
> 
> {:.notice}

## DAOs

كل `DAO` يقترن بـ [كيان](./architecture-entities) ويحول البيانات بين [`وحدة البيانات`](architecture-entities#dataobject-class) والجداول الموجودة في قاعدة البيانات.

يحتوي `DAORegistry` على مثيل من كل `DAO` في التطبيق.

```php
$authorDao = DAOregistry::getDAO('AuthorDAO')؛
```

عندما يكون لـ DAO اسم مختلف في OJS و OMP ، يمكنك استرداده من خلال `التطبيق`.

```php
// احصل على `JournalDAO` أو `PressDAO`
$contextDao = Application::get()->getContextDAO();

// احصل على 'مادةGalleyDAO` أو 'PublicationFormatDAO`
$representationDao = Application::get()->getRepresentationDAO();

// احصل على `SectionDAO` أو `SeriesDAO`
$sectionDao = Application::get()->getSectionDAO();
```

## الحصول على السجلات

استخدم طريقة `الاسترداد()` للحصول على شيء من قاعدة البيانات.

```php
$reviewRoundDao = DAOregistry::getDAO('ReviewRoundDAO');
$result = $reviewRoundDao->الاسترداد(
  'حدد * من الاستعراض _rounds WHERE review_round_id = ؟ ،
  [$reviewRoundId]
)؛
إذا ($result->RecordCount()) {
  $tableRow = $result->GetRowAssoc(false)؛
}
```

`DAO`s لديها طريقة `_fromRow()` لتحويل الصف المعاد إلى `DataObobjec` الصف.

```php
$reviewRoundDao = DAOregistry::getDAO('ReviewRoundDAO');
$result = $reviewRoundDao->الاسترداد(
  'حدد * من الاستعراض _rounds WHERE review_round_id = ؟ ،
  [$reviewRoundId]
)؛
إذا كان ($result->RecordCount()) {
  $reviewRound = $reviewRoundDao->_fromRow($result->GetRowAssoc(false))؛
}
```

معظم `DAO`s لديها طريقة مساعدة للحصول على `DataObobjec` بواسطة المعرف الشخصي.

```php
$reviewRound = DAOregistry::getDAO('ReviewRoundDAO')->getById($reviewRoundId)؛
```

استخدم طريقة `الاسترداد()` للحصول على مجموعة من الصفوف من قاعدة البيانات.

```php
$reviewRoundDao = DAOregistry::getDAO('ReviewRoundDAO');
$result = $reviewRoundDao->الاسترداد(
  'حدد * من الاستعلامات',
  []،
  DBRange($count، $pageNumber)
)؛
$resultFactory = DAOResultFactory($result، $reviewRoundDao، '_fromRow')؛
```

قم بتغيير `مصنع DAOResultFactory` للوصول إلى كل نتيجة في المجموعة.

```php
بينما ($reviewRound = $resultFactory->التالي()) {
  تردد 'جولة المراجعة: ' . $reviewRound->getData('round');
}
```

أو تحويل `DAOResultFactory` إلى مجموعة من الأشياء.

```php
$reviewRounds = $resultFactory->toArray();
```

للاستفسارات المعقدة، استخدم [QueryBuilder](#querybuilder).

## إدراج وتحديث السجلات

استخدم طريقة `التحديث()` لإدراج أو تحديث السجلات.

```php
// أغلق جميع الاستفسارات لتقديم معين
$queryDao = DAOregistry::getDAO('QueryDAO');
$queryDao->تحديث(
  'استفسارات محدثة
    أغلقت المجموعة = 1
    لماذا سوك_نوع = ؟
      & assoc_id = ?',
  [
    ASSOC_TYPE_SUBMISSION,
    $submissionId,
  ]
)؛
```

يحتوي معظم `DAO`s على أساليب المساعد لإدخال أو تحديث أو حذف السجلات عند اجتياز `بيانات`.

```php
$reviewRoundDao->insertObject($reviewRound);
$reviewRoundDao->تحديثات الموضوع ($reviewRound);
$reviewRoundDao->حذف:$reviewRound)؛
```

يمكنك أيضا حذف السجلات بواسطة معرف الكائن.

```php
$reviewRoundDao->حذف ById((int) $reviewRoundId)؛
```

## QueryBuilder

يجب استخدام منشئ الاستعلامات لبناء استفسارات معقدة. يوسع منشئي الاستعلامات [منشئ الاستعلام Laravel](https://laravel.com/docs/5.5/queries) ويوفر واجهة برمجة التطبيقات التعبيرية لجلب سجلات [الكيان](./architecture-entities).

على سبيل المثال، `SubmissionQueryBuilder` يمكن استخدامها لاسترداد العروض المسلمة استناداً إلى عدة معلمات فلتر.

```php
$qb = جديد \APP\Services\QueryBuilders\SubmissionQueryBuilder;
$qb->FilterByContext($contextId)
  ->assignedTo($userId)
  ->orderBy('title')؛
```

بمجرد تكوينها، استخدم منشئ الاستعلامات لإنشاء سلسلة الاستعلام وروابط المعلمة ليتم تمريرها إلى `DAO`.

```php
$qo = $qb->getQuery();
$submissionDao = DAOregistry:getDAO('SubmissionDAO');
$result = $submissionDao->استرداد$qo->toSql(), $qo->getBindings())؛
```

استخدم طريقة `getCount()` للحصول على عدد من الصفوف المتطابقة.

```php
$count = $qb->تعيين تو($userId)->getCount();
```

استخدم طريقة `getIds()` للحصول على مجموعة من معارف الكائنات.

```php
$assignedIds = $qb->assignedTo($userId)->getIds();
```

في معظم الحالات، سيساعد `QueryBuilder` في تحقيق طرق مطابقة `EntityReadadInterface` [](architecture-services#entityreadinterface) من فئة الخدمات.

يمكن أيضا استخدام `QueryBuilder` مع [أساليب الاستعلام في لارافيل](https://laravel.com/docs/5.5/queries).

```php
$qb = جديد \APP\Services\QueryBuilders\UserQueryBuilder();
$qb->FilterByContext($contextId)؛

// الحصول على جميع رسائل البريد الإلكتروني المطابقة
$emails = $qb->getQuery()->pluck('u. رسالة');

// احصل على أول نتيجة مطابقة
$user = $qb->getQuery()->أولاً();

// احصل على آخر مستخدم مسجل
$user = $qb->getQuery()->max('u. ate_تسجيل')؛
```

## SchemaDAOs

إذا تم تعريف كيان ما باستخدام [مخطط](./architecture-entities#schemas)، يجب أن يقوم `DAO` بتوسيع فئة `SchemaDAO`. `SchemaDAO` ينفذ `insertObject()`, `updateObject()`, `deleteobject()`و `_fromRow()` طرق مبنية على المخطط.

## إرشادات الاستخدام

`DAO` قد تطبق أساليب إضافية لإجراء التحديثات بالجملة أو تقلل بطريقة أخرى من استفسارات SQL المكثفة. على سبيل المثال، سيزيل ما يلي جميع تعاريف المهام من جميع المشكلات.

```php
DAOregistry:getDAO('IssueDAO')->deleteAllPubIds($contextId, 'doi');
```

طريقة `DAO` مثل هذا يجب تغليفها بواسطة [خدمة](./architecture-services) التي تؤدي الإجراء حتى يمكن إرسال الإخطارات، يمكن الاتصال بالروابط، ويمكن تنفيذ المهام ذات الصلة.

عند تحديد ما إذا كان سيتم كتابة مثل هذه الطريقة أم لا، فكر في مزايا الأداء لطريقة `DAO` المخصصة في مقابل الجوانب السلبية التالية:

- فهو لن يطلق الرابط الذي يُطلق عادة عند قراءة كيان ما أو إضافته أو تحديثه. يترك مطوري الإضافات "خارج الحلقة".
- وسيتعين الحفاظ عليها بشكل مستقل. ومن المحتمل أن يتم بصورة أكثر انتظاما اختبار طرق قاعدة البيانات الأكثر شيوعا في القراءة والكتابة والحذف.
- يجب أن يتم مزامنته يدوياً مع التغييرات في ملفات مخطط الكيان.

## هيكل الجدول

معظم [الكيانات](./architecture-entities) في التطبيق ممثلة في قاعدة البيانات بجدولين. على سبيل المثال، جدول `المجلات` يحتوي على صف لكل مجلة.

```
mysql> describe journals;
+----------------+-------------+------+-----+---------+----------------+
| Field          | Type        | Null | Key | Default | Extra          |
+----------------+-------------+------+-----+---------+----------------+
| journal_id     | bigint(20)  | NO   | PRI | NULL    | auto_increment |
| path           | varchar(32) | NO   | UNI | NULL    |                |
| seq            | double      | NO   |     | 0       |                |
| primary_locale | varchar(14) | NO   |     | NULL    |                |
| enabled        | tinyint(4)  | NO   |     | 1       |                |
+----------------+-------------+------+-----+---------+----------------+

```

يتم تخزين جميع البيانات الإضافية، بما في ذلك البيانات متعددة اللغات، في جدول `journal_setting`.

```
mysql> describe journal_settings;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| journal_id    | bigint(20)   | NO   | PRI | NULL    |       |
| locale        | varchar(14)  | NO   | PRI |         |       |
| setting_name  | varchar(255) | NO   | PRI | NULL    |       |
| setting_value | text         | YES  |     | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
```

على سبيل المثال، يتم تخزين اسم المجلة الذي يظهر باللغتين الإنجليزية والفرنسية الكندية في صفين في جدول `journal_setting`.

```
mysql> اختر * من journal_settingwhere setting_name="name";
+--------+--------+------------+--------------------------------------------+
journal_id <unk> locale <unk> setting_name <unk> setting_value <unk>
+----------+------------------------------------------------------------------------+
<unk> 1 <unk> en_US <unk> name <unk> Journal of Public Knowledge <unk>
<unk> 1 <unk> fr_CA <unk> name <unk> Journal de la connaissance du public <unk>
+--------------------------------------------------------------------------------------------------+----------
```

يتم تسلسل الخصائص في [مخطط الكيان](./architecture-entities#schemas) التي هي مصفوفة أو كائن عندما يتم تخزينها في جدول الإعدادات.

```
mysql> اختر * من journal_settingwhere setting_name="supportedLocales";
+----------+----------+----------------+--------------------------+
journal_id <unk> locale <unk> setting_name <unk> setting_value <unk>
+----------+----------------+------------------------------------------------------------+
<unk> 1 <unk> <unk> <unk> <unk> <unk> <unk> supporttedLocales <unk> a:1:{i:1؛ :5:"en_US";} <unk>
+----------+--------+----------------------+----------+
```

البيانات المسلسلة لا يمكن بحثها بكفاءة، لذلك لا ينبغي أبدا أن تتضمن البيانات التي تريد الاستعلام عنها.

---

تعرف على المزيد حول [نظام الإضافات](./architecture-plugins).
