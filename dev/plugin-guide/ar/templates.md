---
title: قوالب - دليل الإضافات لOJS و OMP
---

# قوالب

الإضافات لديها حق الوصول إلى نفس نظام القالب كالتطبيق الرئيسي. استخدم هذا عندما تحتاج إلى عرض أو تشغيل كود HTML في الإضافة.

جميع قوالب الإضافات موجودة في `قوالب` الدليل الفرعي.

```
ojs
│
├─┬ plugins
│ │
│ └─┬ generic
│   │
│   └─┬ tutorialExample
│     │
│     ├─┬ templates
│     │ ├── example.tpl
│     │ └── settings.tpl
│     ├── index.php
│     └── TutorialExamplePlugin.inc.php
│     └── version.xml
```

طريقة `getTemplateResource()` متاحة لكل إضافة. استخدمه لتحميل قالب في دليل قالب الإضافة.

```php
$templateMgr = TemplateManager::getManager($request);
$templateMgr->Display($this->getTemplateResource('example.tpl'));
```

يمكن تداخل القوالب في الدلائل الفرعية.

```
ojs
<unk>
<unk> <unk> <unk> <unk> <unk> <unk> plugins
<unk> <unk>
<unk> <unk> <unk> <unk> <unk> <unk> generic
<unk> <unk>
<unk> <unk> <unk> <unk> <unk> tutorialexample
<unk> <unk> <unk> <unk>
<unk> <unk> <unk> <unk> <unk> <unk> <unk> templates
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> م.مثال. pl
<unk> <unk> <unk> <unk> <unk> <unk> إعدادات
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> ', index. ل
<unk> <unk> <unk> <unk> <unk> ', index. hp
<unk> <unk> <unk> <unk> <unk> ', TutorialExamplePlugin.inc.php
<unk> <unk> <unk> <unk> <unk> ', version.xml
```
```php
$templateMgr = TemplateManager::getManager($request);
$templateMgr->عرض($this->getTemplateResource('settings/index.tpl'))؛
```

## تجاوز القوالب

بشكل افتراضي، سيتم تجاوز ملف قالب في ملحق قالب يطابق مسار ملف قالب في التطبيق. يمكنك منح هذه القدرة لأي إضافة.

> تعرف على المزيد حول [تجاوز قالب](/pkp-theming-guide/en/html-smarty). 
> 
> {:.notice}

إضافة رابط أثناء التسجيل للسماح لقوالب الملحق لتجاوز القوالب في التطبيق.

```php
الاستيراد('lib.pkp.classes.plugins. نيركبلوجين)؛
class TemplateOverrideExamplePlugin يمدد سجل GenericPlugin {
    الدالة العامة ($category, $path، $mainContextId = NULL) construction@@
        $success = الوالد::register($category، $path)؛
        إذا ($success && $this->getEnabled()) {
            Hookregistry::register('TemplateResource::getFilename', مصفوفة ($this, '_overridePluginTemplates'))؛
        }
        العودة $success؛
    }
}
```

أي قالب يطابق المسار واسم الملف لقالب التطبيق سوف يتجاوزه. في المثال أدناه ، تتجاوز الإضافة قالب التطبيق `common/footer.tpl`.

```
ojs
<unk>
<unk> <unk> <unk> <unk> <unk> <unk> plugins
<unk> <unk> <unk> <unk> <unk> generic
<unk> <unk> <unk> <unk> <unk> templateOverrideالمثال
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> templates
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> الشائعة
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> مذيل. pl
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> - ...
├─┬ templates
│ └─┬ common
│   └── footer.tpl
```

يمكن لأي ملحق يمكن أن يتجاوز قوالب التطبيق أن يتجاوز أيضا قوالب ملحق آخر. في المثال أدناه ، يتجاوز البرنامج المساعد قالب الكتلة الخاص بالبرنامج المساعد `MakeSubmission`.

```
ojs
│
├─┬ plugins
│ ├─┬ blocks
│ │ └─┬ makeSubmission
│ │   ├─┬ templates
│ │   │ └── block.tpl
│ │   └── ..
│ └─┬ generic
│   └─┬ templateOverrideExample
│     ├─┬ templates
│     │ └─┬ plugins
│     │   └─┬ blocks
│     │     └─┬ makeSubmission
│     │       └─┬ templates
│     │         └── block.tpl
│     └── ..
```

---

تعلم كيفية [إضافة إعدادات](./settings) إلى البرنامج المساعد الخاص بك.