---
title: المعالجون - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# Handlers

كل طلب يتم توجيهه إلى `معالج`، وهو مسؤول عن الإذن بالطلب، وجلب البيانات وتنسيق الاستجابة.

لا يمكن إعادة استخدام الرمز داخل `المعالج` لذلك `المعالج`s يجب أن لا ينفذ هذه الإجراءات بنفسه. وبدلا من ذلك، ينبغي لها أن تنسق بين الفئات الأخرى لتلبية الطلب.

`المعالج`s **لا تأذن بالطلب** ولا ينبغي استخدامه بدون [سياسات التفويض المناسبة](./architecture-authorization).

> **نصيحة:** `المعالج`s يؤدي دور `مراقب`ثانية في بنية التطبيق MVC (Model-View-Controller). 
> 
> {:.tip}

## Page Handlers

يتلقى معالجو الصفحات `الحصول على` طلبات و إرجاع `إخراج HTML`. يجب أن يحدد معالج الصفحة طريقة لكل جزء يدعمه.

```php
الاستيراد('classes.handler). لاندر)؛
الفئة الاصليةHandler يوسع المعالج {
    /**
     * عرض قائمة المحتويات للمشكلة الحالية
     */
    تيار الدالة العامة (الأصطفاف $args, طلب $request) {
        إرجاع '<html>. .</html>';
    }
}
```

تعرف على المزيد حول [عناوين الصفحات والمسارات والوقفات](./architecture-routes#page-routes).

### فهرس الصفحة

يمكن لجهات معالجة الصفحات تحديد `فهرس` كوب للتعامل مع عناوين URL التي لا تحتوي على قسم.

```php
الاستيراد('classes.handler). لاندر)؛
الفئة المصدرة يوسع المعالج {
    /**
     * عرض قائمة بجميع المشكلات
     */
    فهرس الدالة العامة (الأصطفاف $args، طلب $request) {
        إرجاع '<html>. .</html>';
    }
}
```

يجب على جهاز التوجيه أن يعلن عن `فهرس` op:

```php
تبديل ($op) {
    حالة 'index':
        define('HANDLER_CLASS', 'IssueHandler');
        الاستيراد ('pages.issue.IssueHandler');
        break;
}
```

### حجج الصفحة

سيتم تمرير أي شظايا URL التي يتم إضافتها بعد الأسفل إلى طريقة `المعالج`في `$args`.

![الشكل البياني الذي يشير إلى أجزاء عنوان URL لمعالجي الصفحات](../img/url-route-page.png)

```php
قسم معالجة المشكلة يمدد المعالج {
    عرض الوظيفة العامة (الأصطفاف $args، الطلب $request) {
        $issueId = isset($args[0]) ? (int) $args[0] : لاغي؛
        إرجاع '<html>...</html>';
    }
}
```

إرجاع خطأ `404` عندما تطلب حجرات الصفحة كيانا غير موجود.

```php
قسم معالجة المشكلة يمدد المعالج {
 عرض الوظيفة العامة (الأصطفاف $args، الطلب $request) {
     $issueId = isset($args[0]) ? (int) $args[0] : لاغي؛
     إذا لم يتم العثور على مشكلة */) {
         $this->getDispatcher()->handle404();

     العودة '<html>. .</html>';
 }
}
```

### الاستجابات

مرجع معالج الصفحة رمز HTML باستخدام `مدير القالب`.

```php
قسم معالجة المشكلة يمدد المعالج {
    تيار الدالة العامة (الأصطفاف $args، طلب $request{
        $templateMgr = مدير القالب::getManager($request)؛
        إرجاع $templateMgr->عرض ('/path/to/template). pl');
    }
}
```

تستخدم القوالب مكتبة قالب [Smarty](https://www.smarty.net/) (v3).

## API Handlers

يستخدم عاملو API إطار [Slim API](http://www.slimframework.com/) و إرجاع `JSON`. يتم توجيه الطلبات إلى نقطة نهاية الإتصالات المحددة في وحدة بناء `المعالج`.

```bash
$ curl https://example.org/publicknowledge/api/v1/submitted
```

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
الفئة PKPSubmissionsHandler يمتد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [
            'GET' => [
                [
                    'pattern' => 'submissions',
                    'المعالج' => [$this، 'getmany']،
                ]،
            ]،
        ]؛
    }
    الوظيفة العامة getMany($slimRequest، $response، $args) {
        العودة $response->مع Json([...]، 200)؛
    }
}
```

### متغيرات المسار

يمكن تحديد المتغيرات المسماة في مسار URL التي هي جزء من نقطة النهاية.

```bash
$ curl https://example.org/publicknowledge/api/v1/submissions/1
```

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
الفئة PKPSubmissionsHandler يمتد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [
            'GET' => [
                [
                    'نمط' => 'تقديم/{submissionId}'،
                    'المعالج' => [$this، احصل على]،
                ]،
            ]،
        ]؛
    }
    الوظيفة العامة تحصل عليها ($slimRequest، $response، $args{
        $submissionId = (int) $args['submissionId']؛
        العودة $response->مع Json([...], 200)؛
    }
}
```

### خلايا الاستفسار

يمكن الوصول إلى معلمات الاستعلام في عنوان URL من خلال الكائن `$slimRequest`.

```bash
$ curl https://example.org/publicknowledge/api/v1/submissions?searchPhrase=barnes
```

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
الفئة PKPSubmissionsHandler يمتد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [
            'GET' => [
                [
                    'pattern' => 'submissions',
                    'المعالج' => صفيفة($this, 'getmany')،
                ]،
            ]،
        ]؛
    }
    الوظيفة العامة getMany($slimRequest، $response، $args) {
        $params = $slimRequest->getQueryParams(); // ['بحث فراسي' => 'بارنس']
        العودة $response->مع Json([...]، 200)؛
    }
}
```

### طلب الجسم

`POST` و `PUT` طلبات تتضمن بيانات في متن الطلب، التي يمكن الوصول إليها مع `$slimRequest->getParsedBody()`.

```bash
$ curl https://example.org/publicknowledge/api/v1/submissions/1 \
  -d '{"contactEmail": "editor@example.org"}' \
  -H "content-Type: application/json" \
  -X PUT
```

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
الفئة PKPSubmissionsHandler يمدد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [
            'PUT' => [
                [
                    'نمط' => 'تقديم/{submissionId}'،
                    'المعالج' => صفيفة($this, 'تحرير')،
                ]،
            ]،
        ]؛
    }
    تحرير الوظيفة العامة ($slimRequest، $response، $args) {
        $data = $slimRequest->getParsedBody(); // ['contactEmail' => 'editor@example. rg']
...
    }
}
```

### الاستجابات

تم تمرير معالج API كائن `$response` الذي يجب إرجاعه باستخدام طريقة `$request->مع Json()`.

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
صف PKPSubmissionsHandler يمتد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [...]؛
    }
    تحصل على وظيفة عامة ($slimRequest، $response، $args) {
        العودة $response->مع Json([
            'id' => 1،
            'title' => 'مثال تقديم'
        ]، 200)؛
    }
}
```

إرجاع دائما [رمز حالة HTTP الصحيح](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes).

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
صف PKPSubmissionsHandler يمتد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [...]؛
    }
    تحصل على وظيفة عامة ($slimRequest، $response، $args) {
        إذا (/* لم يتم العثور على */) {
            إرجاع $response->مع Json(false, 404)؛
        }
        إذا كان (/* وصول التقديم غير مسموح به */) {
            العودة $response->مع Json(false, 403)؛

        العودة $response->مع Json([
            'id' => 1,
            'title' => 'مثال تقديم'
        ]، 200)؛
    }
}
```

يجب أن تمرير ردود الخطأ من API مفتاح محلي يصف الخطأ.

```php
استيراد ('lib.pkp.classes.handler). PIHandler')؛
صف PKPSubmissionsHandler يمتد APIHandler {
    الوظيفة العامة __construct() {
        $this->_endpoint = [...]؛
    }
    تحصل على وظيفة عامة ($slimRequest، $response، $args) {
        إذا (/* لم يتم العثور على */) {
            العودة $response->withStatus(404)->مع JsonError('api. ubmissions.404.submissionNotFound');
        }
...
    }
}
```

### طلب العناصر

كائن `$slimRequest` هو كائن PSR 7 تم إنشاؤه بواسطة إطار Slim API [](http://www.slimframework.com/). إنه **ليس** مثال على كائن `الطلب الرئيسي للتطبيق` الذي يتم تمريره إلى `معالج آخر`. يمكن الوصول إلى الكائن الرئيسي في التطبيق `طلب` باستخدام `APIHandler::getRequest()`.

```php
يمدد PKPSubmissionsHandler الصف APIHandler {
    وظيفة عامة تحصل عليها ($slimRequest، $response، $args) {
        $request = $this->getrequest();
...
    }
}
```

### Slim Framework

اقرأ [دليل Slim API للاستخدام الإطاري](http://www.slimframework.com/docs/v3/) لمعرفة المزيد حول `$slimRequest` و `$response` الكائنات.

## عامل التحكم (مهمل)

يتلقى معالجو التحكم طلبات من المتحكمين في واجهة المستخدم ويعيدون إخراج `JSON`. وهم يتصرفون كمشغلي الصفحات إلا أنهم يخدمون فرادى عناصر واجهة المستخدم التفاعلية، مثل قائمة الملفات أو المناقشات أو المشاركين.

**معالجو وحدة التحكم مهملون.** يجب بناء ميزات جديدة باستخدام مكونات مكتبة واجهة المستخدم التي تتفاعل مع واجهات API.  غير أنها شائعة في جميع مراحل التطبيق وستظل قيد الاستخدام لبعض الوقت.

تعرف على المزيد حول [عناوين URL للوحدة المتحركة والمسارات والوقفات](./architecture-routes#controller-routes).

### استجابة JSONMessage

استخدم صف `JSONMessage` لتنسيق الاستجابة لمعالجي المتحكم.

```php
الاستيراد('classes.controlllers.grid.issues.IssueGridHandler');
class BackIssueGridHandler يمتد إلى IssueGridHandler {
    وظيفة عامة حذف:$args، $request)
...
        إرجاع JSONMessage(true);
    }
}
```

غالباً ما يقوم عامل التحكم بإرجاع سلسلة HTML في `JSON` حزمة البيانات، والذي سيتم استخدامه من قبل [مراقبو واجهة المستخدم](./frontend#controllers) لتحديث DOM.

```php
الاستيراد('classes.controllers.grid.issues. SsueGridHandler')؛
class BackeGridHandler يمدد IssueGridHandler {
    تحرير الوظيفة العامة IssuitIssue($args، $request)
        $templateMgr = مدير قالب:getManager($request)؛
        إرجاع JSONMessage(true, $templateMgr->display('/path/to/template. pl'));
    }
}
```

---

تعلم [كيفية مصادقة المستخدم](./architecture-authentication).
