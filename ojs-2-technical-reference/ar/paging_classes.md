# فصول حشو

عدة فصول تسهل عرض قوائم العناصر في الصفحات مثل الوثائق المقدمة:

- `إيتمتيرتور`
- `ArrayItemIterator`
- `DAOResultFactory`
- `DBRowIterator`
- `VirtualAryIterator`

صف `ItemIterator` هو محرر مجرد، يتم توفير تطبيقات محددة له من قبل الفئات الأخرى. يجب معاملة جميع فئات DAO الفرعية العائدة من إيتيتيراتور كما لو أنها كانت عائدة.

ويمثل كل محرر ”صفحة“ واحدة من النتائج. على سبيل المثال، عند جلب قائمة من التقديمات من `قسم التحرير`، يمكن توفير مجموعة من أرقام الصف المطلوبة؛ يحتوي `أيتيرتور` المعاد (تحديدا `ArrayIterator`) على معلومات حول هذا النطاق.

`ArrayItemIterator` و `VirtualAryIterator` يقدم الدعم للتكرار من خلال مصفوفات PHP ؛ في حالة `VirtualAryIterator`، يجب فقط توريد إدخالات الصفحة المطلوبة، بينما `ArrayItemIterator` سوف يأخذ مجموعة النتائج بأكملها كمعلمة ويكرر من خلال تلك المدخلات فقط في الصفحة الحالية.

`DAOResultFactory`، أكثر الفئات الفرعية استخداما وتفضيلا `ItemIterator` ، يعتني بالأشياء النموذجية المثالية المناظرة للنتائج باستخدام طريقة موفرة من طراز DAO وطريقة للتمرد.

`DBRowIterator` هو `ItemIterator` تغليف حول بنية نتائج ADODB.
