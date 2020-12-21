---
title: الترجمة - دليل الإضافات لOJS و OMP
---

# الترجمة

يجب أن تدعم الإضافات أكثر من لغة واحدة. هذا يسمح لهم بالعمل إذا قمت بتشغيل OJS أو OMP بأكثر من لغة واحدة. أو إذا كنت ترغب في مشاركة البرنامج المساعد الخاص بك بحيث يمكن للآخرين استخدامه.

تتم إدارة الترجمات بإضافة ملفات محلية لكل لغة تدعمها. ويبين المثال الوارد أدناه أين يتم تخزين الملفات المحلية بالانكليزية (الولايات المتحدة) والفرنسية (كندا).

```
ojs
<unk>
<unk> <unk> <unk> <unk> <unk> plugins
<unk> <unk>
<unk> <unk> <unk> <unk> <unk> <unk> generic
<unk> <unk>
<unk> <unk> <unk> <unk> <unk> tutorialexample
<unk> <unk> <unk>
<unk> <unk> <unk> <unk> <unk> <unk> <unk> locale
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> en_US
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> - locale. o
<unk> <unk> <unk> <unk> <unk> <unk> <unk> fr_CA
<unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> <unk> )-locale. o
<unk> <unk> <unk> <unk> <unk> <unk> ', index. hp
<unk> <unk> <unk> <unk> ', TutorialExamplePlugin.inc.php
<unk> <unk> <unk> <unk> ', version.xml
```

الملف المحلي يحدد اللغة وأي رسائل ينبغي ترجمتها.

```po
msgid "plugins.generic.tutorialexample.name"
msgstr "مثال تعليمي"

msgid "plugins.generic. utorialexample.description"
msgstr "هذا البرنامج المساعد هو مثال تم إنشاؤه لدروس حول كيفية إنشاء إضافة".
```

ثم استخدم الدالة `__()` للحصول على رسالة في الملحق الخاص بك.

```php
الاستيراد('lib.pkp.classes.plugins.GenericPlugin');
فصل البرنامج التعليمي - Exugin يمد GenericPlugin {

  الدالة العامة getDisplayName() {
        العودة __('plugins. eneric.tutorialexample. اللعبة)؛
    }

    الوظيفة العامة getDescription() {
        العودة __('الإضافات. eneric.tutorialexample.description');
    }
}
```

استخدم الدالة الذكية `{translate ...}` للحصول على الرسائل المحلية في القوالب الخاصة بك.

```php
<h1>{ترجمة key="plugins.generic.tutorialexample.name"}</h1>
```

أي إضافة تضاف إلى معرض الإضافات يجب أن تدعم الترجمة، حتى وإن كانت تتضمن فقط ملف لغة واحدة. غالبا ما يقوم مجتمعنا النشط من المترجمين بتوفير ترجمة بعد أن تكون قد أفرجت عن الإضافة.

---

تعلم كيفية [استخدام القوالب وتجاوزها](./templates) في الملحق الخاص بك.
