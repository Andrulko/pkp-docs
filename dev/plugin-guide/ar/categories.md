---
title: فئات الإضافات - دليل الإضافات لOJS و OMP
---

# فئات الإضافات

تحدد فئة البرنامج المساعد متى يتم تحميلها وبأي طريقة يمكنها تعديل التطبيق. على سبيل المثال، يمكن لملحق [](#blocks) أن يضيف كتلة من المحتوى إلى الشريط الجانبي في الموقع الخاص بالقارئ. لكنه لا يستطيع فعل أي شيء آخر ولن يتم تحميله على الخلفية.

كل إضافة يجب أن توسع واحدة من فئات الفئة الإضافية الموجودة في OJS و OMP. في [بدء](./getting-started) البرنامج التعليمي، قام البرنامج المساعد النموذجي بتوسيع `البرنامج الفرعي الخاص بـ` الفصول الدراسية.

```php
الاستيراد('lib.pkp.classes.plugins.GenericPlugin');
فصل البرنامج التعليمي - Exugin يمد GenericPlugin {
...
}
```

إضافة كتلة سوف تمدد صف `BlockPlugin`.

```php
استيراد('lib.pkp.classes.plugins.BlockPlugin');
فصل TutorialBlockPlugin يمد BlockPlugin {
...
}
```

كل فئة من فئات الإضافات توفر طرق يجب تنفيذها. على سبيل المثال [تقرير](#reports) البرنامج المساعد يوسع `تقرير البرنامج المساعد` وينفذ `تقرير البرنامج الإضافي::display()` طريقة لتسليم ملف CSV مع محتويات التقرير.

```php
الاستيراد('lib.pkp.classes.plugins. eportplugin');
استعراض الصف التقريري, البرنامج المساعد يمدد التقرير المساعد
    وظيفة عامة ($args, $request) {
    رأس ('نوع المحتوى: نص/قيم مفصولة بفاصلة')؛
        العنوان ('محتوى القرار: المرفق؛ filename=reviews. sv');
    $fp = fopen('php://output', 'wt');
        fputcsv($fp، [/* تفاصيل المراجعة في التقرير */])؛
        مغلقة($fp);
  }
}
```

تعرف على كل فئة أدناه.

## كتل

حظر الإضافات يوفر المحتوى الذي يمكن عرضه في الشريط الجانبي في أي صفحة. تحتاج إلى ملف نموذجي.

```
ojs
│
├─┬ plugins
│ │
│ └─┬ blocks
│   │
│   └─┬ madeBy
│     │
│     ├─┬ templates
│     │ └── block.tpl
│     ├── index.php
│     └── MadeByPlugin.inc.php
│     └── version.xml
```

يجب أن يتضمن ملف القالب جميع HTML للكتلة الخاصة بك.

```html
<div class="pkp_block block_madeBy">
  صنع مع ❤ من قبل مشروع المعرفة العامة
</div>
```

أضف طريقة `getContents()` لنقل البيانات إلى القالب.

```php
الاستيراد('lib.pkp.classes.plugins. قفل الإضافة')؛
صف MadeByPlugin يمدد BlockPlugin {
  الدالة العامة getContents($templateMgr, $request = null) {
    $templateMgr->مهمة ('madeByText', 'صنع مع ❤ من قبل مشروع المعرفة العامة');
    إرجاع الوالد::getContents($templateMgr، $request)؛
  }
}
```

```html
<div class="pkp_block block_madeBy">
  {$madeByText}
</div>
```

حظر الإضافات يمكن أن تستخدم أي كود HTML. ومع ذلك، إذا كنت تريد أن تمزج الكتلة مع الكتل الأخرى التي يوفرها PKP، استخدم العلامة التالية.

```html
<div class="pkp_block">
    <span class="title"><! - أضف عنوان الكتلة الخاصة بك هنا --></span>
    <div class="content">
    <! - أضف المحتوى الرئيسي للكتلة هنا -->
    </div>
</div>
```

## استيراد/تصدير

وتوفر إضافات الاستيراد/التصدير أدوات للحصول على البيانات من وإلى مكتب خدمات الرقابة الداخلية ومكتب إدارة الممتلكات. يمكن استخدامها عندما تنتقل بين تطبيقنا ومنصة أخرى لهجرة المستخدمين، والإرسالات، ومشاكل الظهر والمزيد.

> قم بتنزيل [مثال استيراد/تصدير ملحق](https://github.com/pkp/exampleImportExport). 
> 
> {:.notice}

يمكن تشغيل كل إضافة استيراد / تصدير على سطر الأوامر.

```
$ أدوات php / importExport.php مثال: ImportExportPlugin استيراد filename.csv
```

```php
الاستيراد('lib.pkp.classes.plugins. mportExportPlugin')؛
class مثال: ExportExportPlugin يمتد إلى ImportExportExportPlugin {
  /**
     * @copydoc ImportExportPlugin::usage()
     */
    Public functionage($scriptName) {
    صدى "الاستخدام: ". $scriptName . " " . $this->getName() . " [command]\n";
    صدى "الأوامر:\n";
    صدى استيراد [filename]";
    صدى " تصدير [filename]";
  }

    /**
     * @copydoc ImportExportplugin::executeCLI()
     */
    وظيفة عامة منفذة CLI($scriptName، &$argsconstruction@@
    $command = المصفوفة_shift($args)؛
    $filename = المصفوفة_shift($args)؛

    if ($command === 'import') {
      $data = file_get_contents($filename)؛
      /* الآن استيراد البيانات */

    } في مكان آخر ($command == 'للتصدير') {
      $fp = fopen($filename, 'مملة')؛
      fputcsv($fp، [/* تصدير مجموعة بيانات */])؛
      مغلق ($fp)؛
    }
  }
}
```

كل إضافة استيراد/تصدير لها صفحة خاصة بها تحت قائمة الأدوات > الاستيراد/التصدير. ويمكن استخدام ذلك لعرض خيارات الاستيراد والتصدير وتوفير واجهة المستخدم لتوليد الصادرات.

```php
الاستيراد('lib.pkp.classes.plugins. mportExportPlugin')؛
class مثال: ExportExportPlugin يمتد إلى ImportExportExportPlugin {
    /**
     * @copydoc ImportExportPlugin::register()
     */
    Public function display($args, $request) {
        الوالد::display($args، $request)؛

        // استخدم المسار لتحديد الإجراء الذي يجب اتخاذه
//
        $path = المصفوفة_shift($args)؛
        تبديل ($path) {

            // تسليم ملف CSV لتحميل
            حالة 'صدّر:
                رأس ('نوع المحتوى: النص/قيم مفصولة بفاصلة')؛
                العنوان ('محتوى القرار: المرفق؛ filename=example-'. date('Ymd') . '.csv');
        $fp = fopen('php://output', 'wt');
        fputcsv($fp، [/* تصدير مجموعة بيانات */])؛
        إغلاق($fp)؛
                استراحة؛

      // عندما لا يطلب أي مسار، عرض صفحة مع
      // خيارات التصدير واستمارة لطرد مسار
      // 'تصدير الجميع'.
            الافتراضي:
                $templateMgr = TemplateManager::getManager($request);
                $templateMgr->Display($this->getTemplateResource('export.tpl'));
        }
    }
}
```

استخدم الدالة الذكية `{plugin_url ...}` في القالب لإرسال نموذج إلى أحد مسارات الاستيراد أو التصدير.

```html
<form method="POST" action="{plugin_url path="exportAll"}">
  <button type="submit">تصدير الكل</button>
</form>
```

## التقارير

الاضافات التبليغ توفر الوصول بنقرة واحدة إلى تحميل ملف CSV. ويمكن أن يتضمن التقرير تفاصيل عن إحصاءات استخدام المقالات، أو المستعرضين أو أي شيء تريده.

التبليغ عن الاضافات تمديد فئة `تقرير الاضافات` وتنفيذ `طريقة العرض ()`.

```php
الاستيراد('lib.pkp.classes.plugins. eportplugin');
فئة مواد التقرير الموسعة يمدد التقرير الإضافي
  وظيفة عامة ($args, $request) {

    // احصل على جميع العروض (أو 5، 00 إذا كان هناك أكثر من ذلك)
    $submissions = الخدمات:get('submissions')->getMany([
      'count' => 5000,
      'سياق' => $request->getContext()->getId(),
    ])؛

    // إرجاع ملف CSV
    رأس ('المحتوى: النص/قيم مفصولة بفاصلة')؛
        العنوان ('محتوى القرار: المرفق؛ filename=articles-'. date('Ymd') . '.csv');
        $fp = fopen('php://output', 'wt');
    fputcsv($fp، ['ID', 'Title'])؛
    التمهيد ($submissions ك $submission) {
      fputcsv($fp, [$submission->getId(), $submission->getlocalizedTitle()])؛
    }
        مغلق ($fp)؛
  }
}
```

عادةً ما يتم إنشاء التقارير بتنسيق CSV، ولكن يمكن لإضافة التقرير الخاص بك إرجاع أي تنسيق ملف قابل للتنزيل.

## السمات

تتحكم الموضوعات في تصميم وتصميم مجلة أو موقع صحفي. اقرأ [دليل القالب](/pkp-theming-guide/en) لتعلم كيفية بناء السمات الخاصة بك.

## Generic

يتم تحميل الإضافات العامة مع كل طلب. إنهم يرتبطون بالتطبيق في وقت مبكر من [طلب دورة الحياة](/dev/documentation/en/architecture-request) ويمكن استخدامها لتعديل كل شيء تقريبا.

تستخدم الإضافات العامة [روابط](/dev/documentation/en/utilities-hooks) للتدخل في التطبيق. يجب إضافة الروابط في طريقة `سجل التسجيل` للملحقة.

```php
الاستيراد('lib.pkp.classes.plugins. نيركبلوجين)؛
مثال الصف يمدد البرنامج المساعد GenericPlugin {

    سجل الدالة العامة ($category, $path، $mainContextId = NULL) construction@@
        $success = الوالد::register($category، $path)؛
        إذا ($success && $this->getEnabled()) {
            Hookregistry::register('مثال::hookName', المصفوف($this، 'doSomething'))؛
        }
        العودة $success؛
  }

  وظيفة عامة في شيء ما ($hookName، $args) {
    /// افعل شيئا...
  }
}
```

> تحقق دائمًا مما إذا كان المكون الإضافي مفعّل قبل تسجيل الرابط. خلاف ذلك، سيتم تشغيل الملحق الخاص بك حتى عندما يكون قد تم تعطيله. 
> 
> {:.warning}

الإضافات العامة قوية جداً ويمكنها استخدام أي رابط في التطبيق. انظر إلى [أمثلة](./examples) للأفكار وتعلم عن [الروابط الأكثر شيوعاً](/dev/documentation/en/utilities-hooks#common-hooks).

## اخرى

هناك فئات إضافية أخرى متاحة لا تستخدم في كثير من الأحيان. أفضل طريقة للتعرف عليها هي قراءة شفرة المصدر لإحدى الإضافات الموجودة. وتشمل هذه الفئات ما يلي:

- `مصادقة` الإضافات تسمح لك بتفويض ومزامنة حسابات المستخدم مع مصدر ثالث.
- `البوابات` الإضافات تسمح لك بإضافة عنوان URL جديد والرد على الطلبات لهذا الرابط.
- `بيانات التعريف` تنفذ الإضافات وصفا لتنسيق البيانات الوصفية.
- `oaiMetadataFormats` الإضافات تضيف تنسيق البيانات الوصفية إلى النقطة النهائية للتطبيق.
- `طريقة الدفع` الاضافات تسمح لك بتنفيذ مناولة الدفع الخاصة بك عند استخدام رسوم الاشتراك والمقال.
- `pubIds` الاضافات تسمح لك بإضافة دعم لمعرفات النشر مثل DOIs.

---

تعلم كيفية [ترجمة الإضافة الخاصة بك](./translation) بحيث يمكن استخدامها من قبل العديد من المجلات.