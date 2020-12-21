---
title: الترخيص - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# التصريح

يجب على كل `معالج` تحديد السياسات لمنع الوصول غير المصرح به. يتم تطبيق هذه السياسات في طريقة `الإذن`

```php
لوحة تحكم الصف يمدد المعالج {
    /**
     * @copydoc PKPHandler::authorize()
     */
    تفويض الوظيفة العامة($request, &$args $roleAssignments) {

        استيراد ('lib. kp.classes.Security التأثير. KPSiteAccessPolicy');
        $this->إضافة سياسة(PKPSiteAccessPolicy($request, null, $roleAssignments))؛

        عودة الوالد::إذن$request، $args، $roleAssignments)؛
    }
}
```

يمكن تطبيق أكثر من `سياسة`

```php
الفئة موضوع يمدد المعالج {
    /**
     * @copydoc PKPHandler::authorize()
     */
    تفويض الوظيفة العامة($request, &$args $roleAssignments) {

        استيراد ('lib. kp.classes.security.authorization. ontextRequiredPolicy');
        $this->إضافة سياسة(السياق الجديد مطلوب($request))؛

        الاستيراد('فئات'. ecurity.authoration. jsJournalMustPublishPolicy');
        $this->addPolicy(New OjsJournalMustPublishPolicy($request))؛

        عودة الوالد::إذن($request، $args، $roleAssignments)؛
    }
}
```

`السياسة`s يمكن تجميعها في `مجموعة سياسات`. استخدم `COMBINING_PERMIT_OVERRIDES` عندما تريد السماح بالوصول إذا مرت أي من السياسات.

```php
يعمل عامل الطبقة على تمديد المعالج {
    /**
     * @copydoc PKPHandler::authorize()
     */
    إذن الوظيفة العامة($request, &$args $roleAssignmentsconstruction@@

        $submissionAccessPolicySet = سياسة جديدة (COMBINNG_PERMIT_OVERRIDES)؛

        / طلب أن يكونوا المؤلف...
        استيراد ('lib.pkp.classes.security.authorization.internal.SubmissionAuthorPolicy');
        $submissionAccessPolicySet->addPolicy(SubmissionAuthorPolicy($request));

        // ... أو أن يكون قد تم تعيينهم للطلب.
        استيراد ('lib.pkp.classes.security.authorization.internal. الوصول إلى WorkflowStageRequiredPolicy');
        $submissionAccessPolicySet->إضافة سياسة(UsercessibleWorkStgeRequiredPolicy($request));

        $this->سياسة إضافية($submissionAccessPolicySet)؛

        عودة الوالد::إذن$request، $args، $roleAssignments)؛
    }
}
```

استخدم `COMBINING_DENY_OVERRIDES` عندما تريد منع الوصول إذا فشل أي من السياسات.

```php
فصل QueryHandler يمدد المعالج {
    /**
     * @copydoc PKPHandler::authorize()
     */
    تفويض الوظيفة العامة($request, &$args $roleAssignmentsconstruction@@

        $assistantAccessPolicySet = سياسة جديدة (COMBINING_DENY_OVERRIDES)؛

        // يتطلب أن يكون لهم دور المساعد...
        استيراد ('lib.pkp.classes.security.authorization.RoleBasedHandlerOperationPolicy');
        $assistantAccessPolicySet->addPolicy(RoleBasedHandlerOperationPolicy($request, ROLE_ID_ASSISTANT, $roleAssignments[ROLE_ID_ASSISTANT]));

        // ... وأنهم يعينون في هذه المرحلة من سير العمل.
        استيراد ('lib.pkp.classes.security.authorization. سياسة ueryWorkflowgeAccess');
        $assistantAccessPolicySet->إضافات سياسية(QueryworkflowstageAccessPolicy($request, $args، $roleAssignments، 'تقديم' ، $stageId))؛

        $this->سياسة إضافية($assistantAccessPolicySet)؛

        العودة الوالد::إذن$request، $args، $roleAssignments)؛
    }
}
```

قم بإنشاء فئة `السياسة مجموعة` الخاصة بك لتحديد القواعد القابلة لإعادة الاستخدام.

```php
class ExamplePolicy extends PolicySet {
    public function __construct($request, $args, $roleAssignments, ...) {
        parent::__construct($request);

        $this->addPolicy(...);
        $this->addPolicy(...);

        $policySet = new PolicySet(...);
        $policySet->addPolicy(...);
        $policySet->addPolicy(...);
        $this->addPolicy($policySet);
    }
}

class ExampleHandler extends Handler {
    public function authorize($request, &$args, $roleAssignments) {
        $this->addPolicy(new ExamplePolicy($request, $args, $roleAssignments, ...));
        return parent::authorize($request, $args, $roleAssignments);
    }
}
```

حدد سياسات متميزة لكل طريق في `المعالج` عن طريق التحقق من العملية المطلوبة.

```php
لوحة تحكم الصف يمدد المعالج {
    تفويض الوظيفة العامة($request، &$args $roleAssignments) {

        $this->إضافة سياسة(... ;

        $requestedOp = $request->getRouter()->getrequestedOp($request)؛
        if ($requestedOp === 'adminStatistics') {
            $this->addPolicy(. .);
        }

        إعادة الوالد::authorize($request, $argsو $roleAssignments)؛
    }
}
```

تحقق من اسم المسار عند استخدام `APIHandler`.

```php
معالج الصف يمدد APIHandler {
    /**
     * copydoc PKPHandler::authorize()
     */
    تفويض الوظيفة العامة($request, &$args $roleAssignments) {

        $this->إضافة سياسة(... ;

        $routeName = $this->getSlimrequest()->getAttribute('route');
        if ($routeName === 'get') {
            $this->إضافة سياسة(. .);
        }

        إعادة الوالد::authorize($request, $argsو $roleAssignments)؛
    }
}
```

## الإذن بواسطة دور المستخدم

سيحدد `معالج الصفحات` الأدوار التي يمكن الوصول إلى عملياتها وتطبيق `سياسة RoleBasedHandlerOperation`.

```php
مثال الصف يمدد المعالج {

    الدالة العامة __construct() {
        الأصل :construct();

        $this->إضافة تعيين(
            [ROLE_ID_AUTHOR]،
            [الإحصاءات]
        )؛

        $this->addroleAssignment(
            [ROLE_ID_ADMIN, ROLE_ID_MANAGER]
            ['الصحفيين']
        )؛

        $this->addleRoleAssignment(
            [ROLE_ID_ADMIN],
            [إحصائيات المدينة]
        )؛
    }

    إذن الوظيفة العامة ($request، &$args $roleAssignments) {
        استيراد ('lib. kp.classes.security.authorization. olicySet');
        $rolePolicy = سياسة جديدة (COMBINING_PERMIT_OVERRIDES)؛

        الاستيراد ('lib. kp.classes.security.authorization. سياسة OleBasedHandlerOperation')؛
        preach($roleAssignments ك $role => $operations) {
            $rolePolicy->إضافة سياسة(RoleBasedHandlerOperationPolicy($request, $roleو $operations))؛
        }
        $this->سياسة إضافية($rolePolicy)؛

        العودة الوالد::إذن($request، $args، $roleAssignments)؛
    }
}
```

`APIHandler` سيفعل نفس الشيء عند تحديد مساره.

```php
يمدد برنامج تقديم العروض الصف APIHandler {

    وظيفة عامة __construct() {
        $this->_endpoint = [
            'GET' => [
                [
                    'نمط' => 'تقديم/{id}'،
                    'المعالج' => [$this، احصل على]،
                    'أدوار' => [ROLE_ID_MANAGER، ROLE_ID_AUTHOR]،
                ]،
                [
                    'نمط' => 'تقديم/{id}/stats',
                    'المعالج' => [$this، 'getStats']،
                    'أدوار' => [ROLE_ID_MANAGER]،
                ]،
            ]،
        ]؛
    }

    إذن الوظيفة العامة ($request، &$args $roleAssignments) {
        استيراد ('lib. kp.classes.security.authorization. olicySet');
        $rolePolicy = سياسة جديدة (COMBINING_PERMIT_OVERRIDES)؛

        الاستيراد('lib. kp.classes.security.authorization. سياسة OleBasedHandlerOperation')؛
        preach($roleAssignments as $role => $operations) {
            $rolePolicy->إضافة سياسة(RoleBasedHandlerOperationPolicy($request, $role، $operations))؛
        }
        $this->إضافة السياسة($rolePolicy)؛

        العودة الوالد::إذن$request، $args، $roleAssignments)؛
    }
}
```

## الإذن عن طريق تعيين التسليم

عند الإذن بالوصول إلى التقديم، يجب عليك التحقق من الأدوار التي يعينها المستخدم _لهذا التقديم_.

```php
قسم SubmissionFileHandler يمدد المعالج {

    إذن الوظيفة العامة($request, &$args, $roleAssignments) {
        // المستخدمين يتم تعيينهم إلى مراحل محددة من التسليم
        // سير العمل. تحقق من الوصول إلى المنصة، وليس التقديم.
        // في هذا المثال ، يتم تقديم معرف المرحلة كاستعلام
        // معلمة مع الطلب.
        $stageId = $request->getUserVar('stageId');

        // يجب إرسال معرف التقديم كاستفسار
        // معلمة. أخبر السياسة عن المعلمة التي تريد التحقق منها عن
        // معرف التقديم. في هذا المثال، نفترض عنوان URL
        // المستخدم للطلب المشمول؟ ubmissionId=1
        $queryParam = 'تقديم' ؛

        استيراد ('lib. kp.classes.security.authorization. سياسةOrkflowgeStageAccess');
        $this->الإدمان على البوليسيا (سياسة جديدة لمرحلة العمل)$request, $args، $roleAssignments، $queryParam، $stageId)؛

        العودة الوالد::إذن$request، $args، $roleAssignments)؛
    }
}
```

يجب تطبيق ذلك كلما أذنت بالوصول إلى أي كائن من عناصر سير العمل في الطلب المقدم. ويمكن للمحررين أن يؤدوا واجبا مضاعفا بوصفهم مراجعين ومؤلفين، وفي مثل هذه الظروف لا ينبغي أن تتاح لهم إمكانية الوصول إلى جميع تفاصيل تدفق العمل.

## العناصر المصرح بها

تعمل السياسات عن طريق التحقق من وجود الأشياء المطلوبة وأن المستخدم الحالي لديه إذن للوصول إليها. يمكن تخزين هذه الكائنات عند اكتمال الترخيص واسترجاعه لاحقا عند الاستجابة للطلب.

قم بتخزين كائن مصرح به عندما تقوم `سياسة` باسترجاعه من قاعدة البيانات وتمكنت من اجتياز `قواعد السياسة`

```php
QueryRequiredPolicy يمتد نطاق السياسة الخاصة بالدالة العامة
    dataObject() Effect() {

        // احصل على الاستعلام المطلوب وأكد أنه موجود
        إذا (!$query{
            إعادة AUTHORIZATION_DENY;
        }

        // قم بتخزين الكائن المأذون به
        $this->addauthorizedContextObject(ASSOC_TYPE_QUERY، $query)؛

        إعادة AUTHORIZATION_PERMIT؛
    }

```

استرداد كائن مصرح به في `المعالج`.

```php
مثال الصف يمدد المعالج {

    إذن الوظيفة العامة(... {
        // QueryRequiredPolicy يخزن الاستعلام المطلوب
        // كعنصر مصرح به
        $this->إضافة سياسة(QueryRequiredPolicy(... )؛
        إعادة الوالد::authorize(... ;
    }

    قراءة الاستعلام للوظيفة العامة(... {
        // استرداد عنصر الاستعلام المصرح به
        $query = $this->getAuthorizedContextObject(ASSOC_TYPE_QUERY)؛

...
    }
}
```

يمكنك الوصول إلى أدوار المستخدم الحالي كلما تم استدعاء `RoleBasedHandlerOperationPolicy`.

```php
مثال الصف يمدد المعالج {

    إذن الوظيفة العامة(... {
        $this->إضافة سياسات(RoleBasedHandlerOperationPolicy(. .)))؛
        إعادة الوالد::authorize(. .);
    }

    إعادة كتابة الوظيفة العامة(... {
        $userRoles = $this->getAuthorizedContextObject(ASSOC_TYPE_USER_ROLES)؛
...
    }
}
```

يمكنك الوصول إلى الدور المعين للمستخدم الحالي في التقديم الحالي عند استدعاء `WorkflowStageAccessPolicy`.

```php
مثال الصف يمدد المعالج {

    إذن الوظيفة العامة(... {
        $this->إضافة سياسة(WorkflowstageAccessPolicy(. .)))؛
        إعادة الوالد::authorize(... ;
    }

    وظيفة عامة قراءة Query(. .) {
        $currentSubmission = $this->getAuthorizedContextObject(ASSOC_TYPE_SUBMISSION)؛
        $assignedRoles = $this->getauthorizedContextObject(ASSOC_TYPE_ACCESSIBLE_WORKFLOW_STAGES)؛
...
    }
}
```

---

الآن بعد أن تم الإذن للمستخدم، تعلم كيف يستخدم [فئات الخدمة لتلبية الطلب](./architecture-services).