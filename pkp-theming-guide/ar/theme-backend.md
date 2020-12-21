# موضوع الخلفية التحريرية

تعديل مظهر خلفية التحرير في OJS 3.0+ أو OMP 1. + أصعب بكثير، وتنطوي على خطر أكبر لكسر التطبيق. يجب ألا يتم تصميم خلفية التحرير إلا إذا كنت مطورا ذا خبرة وتفهم بوضوح المفاهيم الأخرى الموصوفة في هذا الدليل.

وعلى الرغم من أنه ليس موثقا توثيقا جيدا، فإن المواضيع يمكن أن تضخ قوالبها وأنماطها في الخلفية بنفس السهولة التي تضمنها الأمام. أي قوالب تحت `قوالب` يمكن الكتابة فوقها. ويمكنك إضافة ورقات أنماط إلى الخلفية من خلال تمرير وسيطة `سياقات` إلى `نمط الإضافات`.

```php
    الدوال العامة() {
        $this->إضافة Style('my-custom-style', 'styles/index.less', ary( 'سياقات' => 'backend' );
}
```

ورقة النمط الرئيسية لخلفية التحرير تسمى `pkpLib`. يمكنك تعديل هذه الأنماط بتمرير المتغيرات الخاصة بك.

```php
    دالة عامة init() {
        $this->modifyStyle('pkpLib', array('addLess' => array('styles/index.less')));
}
```

وننصحك بإجراء اختبار شامل لأي تغييرات تقوم بها. وخلفية التحرير هي تطبيق كبير ومعقد. يمكن أن يكون لتغيير النمط أو البرنامج النصي تأثيرات غير مقصودة يصعب تعقبها دون معرفة شاملة للنظام.

والموضوع ليس أفضل مكان لتوسيع نطاق وظيفة النظام. هناك إضافة API أوسع نطاقاً وهو مناسب لتمديد التطبيق.

نوصي بأن تتمسك بتعديلات بسيطة على الألوان لتكييف خلفية التحرير مع علامتك التجارية في كل ما عدا الظروف الاستثنائية.
