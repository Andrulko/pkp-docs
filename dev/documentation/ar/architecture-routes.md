---
title: المسارات - التوثيق الفني - OJS<unk> OMP<unk> OPS
---

# المسارات

يتم تعيين كل طلب إلى صفحة أو API أو وحدة تحكم `معالج` بناء على عنوان URL.

## طرق الصفحة

يظهر الرسم البياني أدناه عنوان URL لـ [معالج الصفحات](architecture-handlers#page-handlers).

![الشكل البياني الذي يشير إلى أجزاء عنوان URL لمعالجي الصفحات](../img/url-route-page.png)

سيبحث جهاز التوجيه عن ملف في `/pages/issue/index.php` أو `/lib/pkp/pages/issue/index.php`، الذي يحمل المعالج الصحيح.

```php
تبديل ($op) {
    حالة 'عرض':
        تعريف ('HANDLER_CLASS', 'IssueHandler');
        استيراد ('pages.issue.IssueHandler');
        break;
}
```

يتم عادة إدارة جميع الصفحات من قبل نفس `المعالج`. غير أنه من الممكن توجيه كل باب إلى معالج مختلف.

```php
تبديل ($op) {
    حالة 'عرض':
        تعريف('HANDLER_CLASS', 'IssueHandler');
        استيراد('صفحات). سوق. SsueHandler');
        استراحة؛
    قضية 'أرشيف':
        تعريف 'HANDLER_CLASS', 'ArchiveHandler');
        استيراد('صفحات'. ssue.ArchiveHandler');
        استراحة؛
}
```

هذا غير ممكن لطرق API أو التحكم.

## طرق API

يظهر الرسم البياني أدناه عنوان URL لـ [معالج API](architecture-handlers#api-handlers).

![الشكل البياني الذي يشير إلى أجزاء عنوان URL لمعالجات API](../img/url-route-api.png)

سيبحث جهاز التوجيه عن ملف في `/api/v1/submissions/index.php`، الذي يقوم بتحميل المعالج الصحيح.

```php
الاستيراد('api.v1.submissions.SubmissionsHandler');
إرجاع طلبات جديدة ();
```

جهاز التوجيه **لن** يجد ملف في `/lib/pkp/api/v1/submissions/index.php`.

## طرق التحكم

يظهر الرسم البياني أدناه عنوان URL لمعالج [وحدة تحكم](architecture-handlers#controller-handlers).

![الرسم البياني الذي يشير إلى أجزاء عنوان URL لمعامل التحكم](../img/url-route-controller.png)

سيقوم جهاز التوجيه بالبحث عن `معالج` وتحميله في `/controlllers/grid/issues/BackIssueGridHandler.inc.php`.

عناوين URL للتحكم مستمدة من `المعالج` اسم الصف الدراسي. تم إسقاط لاحقة `المعالج` وتحول الاسم المتبقي من `PascalCase` إلى `kebab-case`.

# كتابة عناوين URL

لا تقم أبدا بكتابة مسار URL يدوياً لأنه يمكن تشغيل التطبيق دون تمكين توجيه الرابط. عند تشغيل خيار التكوين `disable_path_info` ، سيستخدم مسار URL معلمات الاستعلام.

```
http://example.org/?journal=publicknowledge&page=issue&op=view&path[]=1
```

يجب دائما إنشاء عناوين URL بواسطة طريقة `Router` `url`. يمكنك استرداد `Router` المناسب من `طلب` الكائن.

```php
$url = $request->getRouter()->url($request, null, 'issue', 'view', 1);
```

*الكائن `طلب` سيكون متاحا من `المعالج`. انظر [المعالجين](./architecture-handlers).*

سوف يعيد كائن `طلب` دائما نوع `Router` الذي يطابق المسار الحالي وينشئ عناوين URL لذلك النوع. في معالج الصفحة سوف يعيد `PageRouter`.

```php
$pageUrl = $request->getRouter()->url($request, null, 'issue', 'view', 1);
```

في معالج API سوف يعيد `APIRouter`.

```php
$apiUrl = $request->getRouter()->url($request, null, 'issues/1');
```

في معالج مراقب سوف يعيد `PKPComponentRouter`.

```php
$controllerUrl = $request->getRouter()->url($request, null, 'grid.issues.IssueGridHandler', 'editIssue', [1]);
```

إذا كنت بحاجة إلى الحصول على عنوان URL لجهاز توجيه مختلف، استخدم `المرسل`.

```php
$pageUrl = $request->getDispatcher()->url($request, ROUTE_PAGE, 'issue', 'عرض', 1);
$apiUrl = $request->getDispatcher()->url($request, ROUTE_API, $context->getPath(), 'issues/1');
$controllerUrl = $request->getDispatcher()->url($request, ROUTE_COMPONENT, null, 'grid. ssues.IssueGridHandler', 'editIssue', [1]);
```

---

تعرف على [كيف يستجيب المعالجون للطلب](./architecture-handlers).
