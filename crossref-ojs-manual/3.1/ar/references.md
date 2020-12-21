---
book: تقاطع ojs-يدوي
version: 3.1
---

# الربط المرجعي والإيداع

وابتداء من OJS 3.1.2، من الممكن تمكين مرجع يربط المكون الإضافي بـ Crossref. ستستخدم الإضافة API Crossref للتحقق من مراجع النص العادي وتحديد مواقع DOI المحتملة للمقالات. ستتيح الإضافة أيضا عرض القوائم المرجعية على صفحة هبوط المقالة في OJS.

[https://github.com/pkp/crossrefReferenceLinking](https://github.com/pkp/crossrefReferenceLinking)
> سيؤدي هذا البرنامج المساعد تلقائياً إلى إضافة مراجع المقالات المستخرجة إلى تسجيل DOI مع Crossref. سيتم التحقق تلقائيًا من إمكانية العثور على أي مقاييس محددة للمراجع المقدمة. بعد ذلك بوقت قصير، يمكن للمستخدم استخدام المكون الإضافي للتحقق من هذه المؤسسات التي تم العثور عليها، إما تلقائياً أو يدوياً في علامة التبويب "المراجع" للبيانات الوصفية المقدمة. وإذا تغيرت المراجع المتعلقة بالمقالات بمجرد تسجيلها، فسيتعين تحديث المادة المذكورة مع المراجع الجديدة. ثم يجب إعادة التحقق من المراجع التي تم العثور عليها .
> 
> يتطلب هذا البرنامج المساعد أن يتم تعيين Cssref DOIs إلى مقالات، مراجع المقالات سيتم إدخالها واستخراجها بشكل منفصل، وكذلك المادة التي تودع في كراسيف من داخل مكتب المدعي العام. يستخدم إعدادات تصدير / تسجيل Crossref: بيانات اعتماد Crossref (اسم المستخدم وكلمة المرور)، الإعداد لإيداع DOI التلقائي (هنا للتحقق من المراجع التلقائية)، وكذلك الإعداد لوضع الاختبار.

## تثبيت و تمكين البرنامج المساعد

1. انتقل إلى المستخدم **لوحة التحكم**.
2. انقر فوق إعدادات ****.
3. انقر فوق **إضافات**.
4. انقر فوق عنصر القائمة الفرعية **معرض الإضافات**.
5. ابحث عن البرنامج المساعد المسمى "Crossref Reference plking plugin" وانقر على العنوان.
6. تثبيت الملحق بالنقر فوق "تثبيت".
7. بمجرد الحصول على إشعار بأن الإضافة مثبتة، انقر فوق عنصر القائمة الفرعية **الإضافات**.
8. حدد موقع المكون الإضافي الرابط بين مرجع Crossref وانقر على مربع الاختيار الأزرق على اليمين لتمكينه.