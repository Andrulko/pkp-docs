# نقل البيانات إلى قوالب
يحاول التطبيق تمرير جميع البيانات المفيدة إلى قالب قبل تحميله. قد ترغب في الوصول إلى شيء غير متوفر خارج الصندوق.

سيصف هذا القسم كيفية الربط مع التطبيق قبل تحميل القالب، من أجل توفير بيانات إضافية إلى قالب.

وتتطلب هذه التقنيات فهما لهيكل PHP ولهندسة التطبيق. هذا الدليل سيوفر فقط الرمز الأساسي المطلوب. قد تحتاج إلى مزيد من البحث في وثائق التطبيق لفهم عينات التعليمات البرمجية هنا.

## نقل البيانات إلى كل قالب
قبل عرض قالب، سيطلق حدثًا، `TemplateManager::View`، التي يمكنك ربطها بها لتمرير بيانات إضافية إلى القالب قبل تحميله.

المثال التالي سيجعل متغير ذكي جديد، `{$myCustomData}`، متاح للاستخدام في جميع القوالب الخاصة بك.

```php
فصل DocsThemePlugin يمدد موضوع البرنامج المساعد {
    /**
     * تهيئة الموضوع
     */
    الدالة العامة init() {
        Hookregistry::register ('TemplateManager:::display', مصفوفة ($this، 'تحميل قالب البيانات'))؛
    }

    /**
     * أُطلقت عند تسمية رابط `TemplateManager::display'.
     *
     * * سلسلة @param $hookname
     * @param array $args [$templateMgr، $template، $sendContentType، $charset، $output]
     */
    الدالة العامة loadTemplateData($hookName, $args) {

        // استرداد مدير القالب
        $templateMgr = $args[0]؛

        // إرفاق جزء مخصص من البيانات إلى مدير القالب
        $myCustomData = 'هذه هي بياناتي المخصصة. قد يكون أي متغير PHP.';
        $templateMgr->تعيين ('myCustomData', $myCustomData);
    }
}
```

ربما تريد عرض آخر إعلان لك في تذييل موقعك، لذا تريد أن تكون البيانات متاحة لكل قالب. المثال التالي يضيف متغير ذكي جديد، `{$announcements}`إلى كل قالب.

```php
فصل DocsThemePlugin يمدد موضوع البرنامج المساعد {
    /**
     * تهيئة الموضوع
     */
    الدالة العامة init() {
        Hookregistry::register ('TemplateManager:::display', مصفوفة ($this، 'تحميل قالب البيانات'))؛
    }

    /**
     * أُطلقت عند تسمية رابط `TemplateManager::display'.
     *
     * * سلسلة @param $hookname
     * @param array $args [$templateMgr، $template، $sendContentType، $charset، $output]
     */
    الدالة العامة loadTemplateData($hookName, $args) {

        // استرداد مدير القالب
        $templateMgr = $args[0]؛

        // إرفاق آخر 3 إعلانات إذا تم تمكينها لهذه اليومية
        $request = تطبيق::getrequest();
        $journal = $request->getJournal();
        if ($journal && $journal->getSetting('enableAnnouncements') {
            $announcementDao = DAOregistry::getDAO('AnnouncementDAO');
            $announcements =& $announcementDao->getNumAnnouncementsNotExpiredByAssocId(ASSOC_TYPE_JOURNAL)، $journal->getId(), 3)؛
            $templateMgr->تعيين ('الإعلانات'، $announcements->toArray())؛
        }
    }
}
```

## نقل البيانات إلى قالب واحد
ولكن قد لا ترغب في جعل هذه البيانات متاحة لكل قالب. ربما تريد فقط عرضها على قالب `article.tpl` الخاص بك.

يمكننا التحقق من `$template` الذي يتم استدعاؤه قبل أن نقرر إرفاق الإعلانات.

```php
فصل DocsThemePlugin يمدد موضوع البرنامج المساعد {
    /**
     * تهيئة الموضوع
     */
    الدالة العامة init() {
        Hookregistry::register ('TemplateManager:::display', مصفوفة ($this، 'تحميل قالب البيانات'))؛
    }

    /**
     * أُطلقت عند تسمية رابط `TemplateManager::display'.
     *
     * * سلسلة @param $hookname
     * @param array $args [$templateMgr، $template، $sendContentType، $charset، $output]
     */
    الدالة العامة loadTemplateData($hookName, $args) {

        // استرداد مدير القالب واسم ملف القالب
        $templateMgr = $args[0]؛
        $template = $args[1]؛

        // لا تفعل أي شيء إذا لم نقم بتحميل القالب الصحيح
        إذا ($template ! 'الواجهة/الصفحات/المقالة. pl') {
            العودة؛
        }

        // إرفاق آخر 3 إعلانات إذا تم تمكينها لهذه اليومية
        $request = التطبيق::getrequest();
        $journal = $request->getJournal();
        if ($journal && $journal->getSetting('enableAnnouncements')) {
            $announcementDao = DAOregistry::getDAO('AnnouncementDAO')؛
            $announcements =& $announcementDao->getNumAnnouncementsNotExpiredByAssocId(ASSOC_TYPE_JOURNAL)، $journal->getId(), 3)؛
            $templateMgr->تعيين ('الإعلانات'، $announcements->toArray())؛
        }

}
```

**من المهم ملاحظة** أن بعض القوالب فقط يتم استدعاؤها مباشرة مع هذا الرابط. هذه هي قوالب المستوى الأعلى الموجودة تحت `/frontend/pages/<template_name>.tpl`. ستجد أن ملفات القالب هذه تحمل قوالب فرعية إضافية. غير أن هذه الأمور لا تمر عبر الموصوف. يمكنك فقط الربط في مكالمة القالب الأساسي لكل صفحة من تحميل الصفحات.