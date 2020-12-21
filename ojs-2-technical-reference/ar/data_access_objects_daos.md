# عناصر الوصول للبيانات (DAOs)

يتم استخدام عناصر الوصول إلى البيانات لاسترداد البيانات من قاعدة البيانات في شكل فئات نموذجية، لتحديث قاعدة البيانات إذا أعطيت فئة نموذجية معدلة، أو لحذف صفوف من قاعدة البيانات.

كل فئة نموذجية لها عنصر الوصول إلى البيانات المرتبطة بها. على سبيل المثال، صف `مقال` (`صفوف/مادة/مادة/مادة.inc. (ح)`p) لها صلة بـ DAO تسمى `مادة` (`صفوف/مادة/مادة/مادة/ مادة داو. (nc.php`) المسؤول عن تنفيذ التفاعلات بين الفئة النموذجية ومدخلات قاعدة البيانات الخاصة بها.

جميع DAO توسع فئة `DAO` (`classes/db/DAO.inc.php`). ويتم تنفيذ جميع الاتصالات بين PHP وقاعدة البيانات الخلفية في فصول DAO. وبقدر ما هو منطقي وكفؤ، ينبغي لأي منظمة مساعدة إنمائية رسمية أن تقصر تفاعلها على الجدول أو الجداول التي تعنى بها في المقام الأول.

ولا تكون المساعدة الإنمائية الرسمية، عند استخدامها، مثالية مباشرة على الإطلاق. بدلاً من ذلك، يتم استرجاعها بالاسم باستخدام صف `DAORegistry` ، الذي يحتفظ بالأمثلة على DAO للنظام. وعلى سبيل المثال، لاسترداد مقالة من مقالات المساعدة الإنمائية الرسمية:

`$articleDao = &DAOregistry::getDAO('ArticleDAO');`

ثم لاستخدامه لاسترداد مقالة مع المعرف المخزن في `$articleId`:

`$article = &$articleDao->getArticle($articleId)؛`

لاحظ أن العديد من طرق DAO التي تجلب مجموعة من النتائج سوف ترجع فئات فرعية من فئة `ItemIterator` بدلاً من مصفوفة PHP المعتادة. وهذا ييسر وضع القوائم التي تحتوي على العديد من البنود، ويمكن أن يكون أكثر كفاءة من تحميل جميع النتائج مسبقاً في صفيف. انظر المناقشة المتعلقة بفصول الدعم في قسم فصول الدعم.
