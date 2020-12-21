---
title: مثال - الحصول على البيانات من القالب - دليل الإضافات لOJS و OMP
---

# الحصول على البيانات من القالب

عندما تتخطى [قالب](./templates#override-templates)، قد تحتاج إلى الحصول على البيانات التي تم تعيينها بالفعل للقالب. على سبيل المثال، ضع في الاعتبار قالب قضية واحدة أدناه.

```html
<div class="issue">
  <p>نُشرت: {$issue->getPublished()}</p>
...
</div>
```

تتجاوز الإضافة الخاصة بك هذا القالب لأنه يريد إظهار معرف فريد مع جميع المشاكل. قالب الملحق الخاص بك يبدو هكذا.

```html
<div class="issue">
  <p>نُشرت: {$issue->getPublished()}</p>
  <p>الداخلية المعرف: {$issueInternalId}</p>
...
</div>
```

ومع ذلك، تحتاج أولاً إلى استرداد `issueInternalId` من إعدادات الملحق لعرض المعرف. في المثال أدناه تقوم الإضافة بما يلي.

1. اربط بالمكالمة التي تقوم بتحميل قالب `صفحات/issue.tpl`.
2. احصل على كائن `المشكلة` من متغيرات القالب.
3. استخدم معرف المشكلة للحصول على الإعداد الصحيح للملحقة.
4. تعيين `issueInternalId` للاستخدام في قالب الملحق المخصص.

```php
فصل InternalIssueIdePlugin يمدد GenericPlugin {

    سجل الوظائف العامة ($category، $path، $mainContextId = فارغ
        $success = الوالد::register($category, $path، $mainContextId)؛
        إذا ($success && $this->getEnabled()) {

      // 1. اربط قبل عرض القالب...
      Hookregistry::register('TemplateManager::display',array(&$this، 'addIssueInternalId'))؛
        }
        إرجاع $success؛
  }

  اضافات الوظيفة العامة IssueInternalId($hookName, $args{
    $templateMgr = $args[0]؛
    $template = $args[1]؛
    $contextId = التطبيق: :get()->getrequest()->getContext()->getId();

    // 1. ...فقط عندما يكون قالب المشكلة.
    إذا ($template !== 'frontend/pages/issue.tpl') {
      العودة؛
    }

    // 2. احصل على كائن "المشكلة" من متغيرات القالب المعينة.
    $issue = $templateMgr->getTemplateVars('issue');

    // 3. احصل على إعداد البرنامج المساعد المطابق.
    $internalIssueId = $this->getSetting($contextId, 'issueInternalId' . $issue->getId());

    // 4. تعيين معرف المشكلة الداخلية للاستخدام في القالب. (Automatic Translation)
    $templateMgr->تعيين ('internalIssueId', $internalIssueId);
  }
}
```

---

عرض المزيد من [الأمثلة](./examples).
