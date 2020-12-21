# CSS/LESS

يستخدم OJS و OMP بناء الجملة [LESS](http://lesscss.org/) لكتابة التعليمات البرمجية التي يتم تجميعها بعد ذلك إلى CSS. LESS عبارة عن بناء سهل الاستخدام يشبه CSS-الذي يسمح لك بكتابة كود CSS مع بعض الخلاصات المفيدة، مثل [متغيرات](http://lesscss.org/features/#variables-feature)و [استيراد الملف](http://lesscss.org/features/#variables-feature-import-statements) و [مزيج](http://lesscss.org/features/#mixins-feature).

وفيما يلي مثال على ملف LESS الذي يستخدم متغير للون الخلفية للرأس والتذييل.

```
@background: أحمر;

.pkp_structure_head,
.pkp_structure_footer {
  background: @background;
}
```

يصبح هذا أكثر فائدة عندما نريد استخدام نفس لون الخلفية كحدود ل `<button>` عناصر.

```
@background: أحمر;

.pkp_structure_head,
.pkp_structure_footer {
  background: @background;
}

زر {
  border-color: @background;
}
```

مع نمو ورقة الأنماط الخاصة بك، سوف ترغب في تقسيم الأنماط الخاصة بك إلى ملفات مختلفة بحيث تكون إدارتها أسهل. يسمح لك LESS باستيراد ملفات منفصلة ومشاركة المتغيرات عبرها.

```
// styles/variable.less
@background: أحمر;
```

```
// styles/structure.less
.pkp_structure_head,
.pkp_structure_footer {
  background: @background;
}
```

```
// styles/forms.less
زر {
  الحدود - الألوان: @background;
}
```

```
// styles/index.less
// الآن يمكننا دمج كل هذه الملفات في ملف واحد.
@import "المتغيرات"
@import "structure"
@import "forms"
```

لذا إذا كنا نتابع هذا التنسيق، فستكون ملحقة الموضوع المخصص لدينا الملفات التالية فيها.

```
styles/index.less
styles/variables.less
نماذج/structure.less
styles/forms.less
```

إذا قررت جريدتك تغيير العلامة من الأحمر إلى الأزرق، تحتاج فقط إلى تحديث سطر واحد في رمز الموضوع الخاص بك:

```
// styles/variable.less
@background: أزرق;
```

قبل أن تظهر الأنماط الخاصة بك، تحتاج إلى التأكد من أنها تم تجميعها وتحميلها مع السمة المخصصة الخاصة بك. يمكن تحقيق ذلك باستخدام طريقة `إضافة نمط` لـ [سمة API](theme-api.md).

```php
الصف الافتراضي plugePlugin يمد موضوع plugin {
  وظيفة عامة init() {
    / / المعلمة الثانية، 'styles/index. يجب أن يشير '،
    / / إلى ملف LESS في الموضوع الخاص بك.
    $this->addStyle('stylesheet', 'styles/index.less');
  }
}
```

سيتم مناقشة [موضوع API](theme-api.md) بمزيد من التفصيل في أقسام لاحقة من هذا الدليل.

_إذا بدا LESS معقدًا جدًا، لا يزال بإمكانك كتابة كود CSS العادي وسوف يعمل نفس الشيء. تحتاج فقط إلى حفظ الملف كملف _`أقل`_ تصبح قوة استخدام LESS بدلاً من CSS أكثر وضوحاً عند استكشاف توسيع المواضيع الحالية مع [سمات الأطفال](child-themes.md).

