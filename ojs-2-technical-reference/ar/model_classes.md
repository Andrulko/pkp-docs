# فئات النموذج

والفئات النموذجية هي فئات PHP المسؤولة فقط عن تمثيل كيانات قواعد البيانات في الذاكرة. على سبيل المثال، جدول `المقالات` يخزن معلومات المقالات في قاعدة البيانات؛ هناك فئة نموذجية مقابلة تسمى `مقال` (انظر `الصفوف/المادة/المادة. nc.php`) وفصل DAO المسمى `مادة داو` (انظر القسم المسمى [عناصر الوصول إلى البيانات](http://pkp.sfu.ca/ojs/docs/technicalreference/2.1/classReferenceDataAccessObjects.html) [DAOs]).

والأساليب التي توفرها الفئات النموذجية تكاد تكون حصرية في طرق الحصول على المعلومات وتحديدها لاسترجاعها وتخزينها، مثل طرق `getTitle()` و `setTitle($title)` لـ `مقالة`. الطبقات النموذجية ليست مسؤولة عن تخزين قواعد البيانات أو تحديثها؛ ويتم ذلك من جانب فئة DAO المرتبطة بها.

جميع فئات الموديل توسع فئة `DataObject`.
