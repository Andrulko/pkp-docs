---
title: مثال - إضافة الأنماط والنصوص البرمجية - دليل الإضافات لOJS و OMP
---

# إضافة أنماط ونصوص برمجية

قد يحتاج البرنامج المساعد الخاص بك إلى كود CSS إضافي أو JavaScript لتشغيله. `مدير القالب` يتضمن وظائف المساعد لتحميل البرامج النصية والأنماتيك.

```php
$templateMgr = TemplateManager::getManager($request);
$templateMgr->addStyleSheet('tutorialexampleStyles', 'http://example.com/my-css.css');
$templateMgr->addJavaScript('tutorialexampleScript', 'http://example.com/my-script.js')؛
```

عادة ما تكون النصوص النصية والأنماط في دليل الإضافة. استخدم `base_url` للحصول على عنوان URL إلى دليل جذر البرنامج الإضافي.

```php
$request = تطبيق::get()->getrequest();
$url = $request->getBaseUrl() . '/' . $this->getPluginPath() . '/css/my-css.css';
$templateMgr = TemplateManager::getManager($request);
$templateMgr->addStyleSheet('tutorialexampleStyles', $url);
```

يجب تحميل البرامج النصية والأنماط في طريقة `تسجيل البرنامج المساعد`.

```php
البرنامج التعليمي للأستاذية الإضافية يمدد برنامج Genericplugin {
    سجل الدالة العامة($category، $path، $mainContextId = NULL) {
    $success = الوالد::register($category، $path)؛
        إذا ($success && $this->getEnabled()) {
      $request = Application::get()->getrequest();
      $url = $request->getBaseUrl() . '/' . $this->getPluginPath() . '/css/my-css.css';
      $templateMgr = TemplateManager::getManager($request);
      $templateMgr->addStyleSheet('tutorialexampleStyles', $url);
    }
        Red $success;
  }
}
```

بشكل افتراضي، يتم تحميل البرامج النصية والأنماط على موقع الويب الخاص بالقارئ. اجتياز وسيطة `سياق` لتحميلها في الخلفية التحريرية.

```php
$templateMgr->إضافةStyleSheet(
  'دروس تعليمية،
  $url,
  ['سياق' => 'backend']
);
```

يمكنك أن تمر أكثر من سياق واحد لتحميلهم في مكانين.


```php
$templateMgr->إضافةStyleSheet(
  'دروس تعليمية،
  $url,
  ['سياق' => ['backend', 'frontend']
);
```

يجب أن تحترم الإضافات إعداد التكوين `enable_cdn`. عندما يتم إيقاف هذا، يجب على الإضافات _عدم_ تحميل أي برامج نصية أو أنماط من موقع الويب لطرف ثالث.

```php
إذا (Config::getVar('general', 'enable_cdn')) {
  $url = 'https://example.com/remote-css.css';
} آخر
  $url = $request->getBaseUrl() '/' . $this->getPluginPath() . '/css/local-css.css';
}
$templateMgr->addStyleSheet('tutorialexampleStyles', $url);
```

---

عرض المزيد من [الأمثلة](./examples).
