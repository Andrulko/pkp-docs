# كائن الإضافة

الكائن الاضافي يلخص الاضافات و يقوم عموما بمعظم العمل. في هذه الحالة، بما أن هذه الإضافة ستكون في الفئة العامة، يجب أن يوسع الكائن فئة `Genericplugin`:

**مثال 5-2. كائن الإضافة**

````
<?php 
استيراد ('classes.plugins. نيركبلوجين)؛ 
مثال الصف يمدد إضافة GenericPlugin 
    سجل الدالة ($category, $path) { 
        إذا (الوالد::register($category، $path)) { 
            سجل::register( 
                'قوالب::Manager::Index::ManagementPages', 
                المصفوفة(&$this، 'رد الاتصال') 
            )؛ 
            العودة الصحيحة؛ 
        } 
        إعادة خاطئة؛ 
    } 
    getName() { 
        ReplePlugin'; 
    } 
    الدالة getDisplayName() { 
        Reple Plugin'; 
    } 
    الدالة getDescription() { 
        Re'A وصف لهذه الإضافة'; 
    } 
    استدعاء الدالة ($hookName، $args{ 
        $params =& $args[0]؛ 
        $smarty =& $args[1]؛ 
        $output =& $args[2]؛ 
        $output = '<li>&#187؛ <a href=”http://pkp.sfu.ca”>وصلتي الجديدة</a></li>'; 
        إعادة خاطئة؛ 
    } 
} 
?>
````

وتوضح التعليمات البرمجية أعلاه بعض الأجزاء الأكثر أهمية من الإضافات: دالة `تسجيل` والتسجيل والرد على المكالمات، وإدارة الإضافات.

