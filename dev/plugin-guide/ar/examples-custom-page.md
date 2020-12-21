---
title: مثال - إضافة صفحة مخصصة - دليل الإضافات لOJS و OMP
---

# إضافة صفحة مخصصة

قد ترغب في أن تضيف الإضافة الخاصة بك صفحة جديدة إلى التطبيق. قد يكون هذا صفحة إعدادات منفصلة أو لوحة تحكم تحرير على الخلفية، أو صفحة عامة جديدة على موقع الويب الخاص بالقارئ.

يمكن للملحق العام أن يفعل ذلك عن طريق الاتصال بدورة حياة الطلب وتحميل [الخاص به معالج Pageler](/dev/documentation/en/architecture-handlers).

> يجب عليك أن تفهم [طلب دورة الحياة](/dev/documentation/en/architecture-request) وأن تكون على دراية بهيكل التطبيق [](/dev/documentation/en/architecture)وخاصة [المعالجين](/dev/documentation/en/architecture-handlers)قبل المتابعة. 
> 
> {:.notice}

المثال أدناه يظهر طلب لصفحة مخصصة.

```
http://example.org/publicknowledge/tutorialexample
```

```php
البرنامج التعليمي للمثالب الإضافي يمدد برنامج Genericplugin {
    سجل الدالة العامة ($category، $path، $mainContextId = فارغ
        $success = الوالد::register($category, $path، $mainContextId)؛
        إذا ($success && $this->getEnabled()) {
            Hookregistry::register('LoadHandler', مصفوفة ($this، 'setPageHandler'))؛
        }
        العودة $success؛
  }
    وظيفة عامة setPageHandler($hookName، $params{
        $page = $params[0]؛
        if ($page === 'البرنامج التعليمي') {
            $this->import ('TutorialexamplePluginHandler')؛
            معرف('HANDLER_CLASS', 'tutorialexamplePluginHandler');
            العودة الصحيحة؛

        إعادة خاطئة؛

}
```

```php
الاستيراد('classes.handler). لاندر)؛
فهرس دالة الطبقة التعليمية،ExtorialexamplePluginHandler امتد المعالج {
    فهرس الدالة العامة($args, $request) {
        $plugin = pluginregistry::getPlugin('Generic', 'tutorialexampleplugin');
    $templateMgr = مدير قالب:getManager($request)؛
    العودة $templateMgr->العرض ($plugin->getTemplateResource('مثال). pl'));
  }
}
```

يمكن أن يكون `البرنامج التعليمي` أكثر من نقطة واحدة ودعم جميع قدرات `المعالج العادي`.

> اقرأ عن [إطار التفويض](/dev/documentation/en/architecture-authorization) للحفاظ على أمان صفحاتك الخاصة. 
> 
> {:.warning}

---

عرض المزيد من [الأمثلة](./examples).
