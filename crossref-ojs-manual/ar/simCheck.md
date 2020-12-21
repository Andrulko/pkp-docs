---
book: تقاطع ojs-يدوي
version: 3.2
---

# التحقق من الشبه

ويشمل OJS 3-1-2 تقديم الدعم لسلاجيات iThenticate التحقق من خدمة التحقق من تشابه النشاط.

[https://github.com/asmecher/plagiarism](https://github.com/asmecher/plagiarism)

لاستخدام هذه الإضافة، تحتاج إلى التسجيل في حساب iThenticate وشراء الائتمانات.

الخطوة التالية هي تثبيت وتمكين البرنامج المساعد # تسجيل الدخول كمدير أو محرر لليوميات انقر فوق إعدادات > الموقع انقر فوق الإضافات انقر فوق معرض عنصر القائمة الفرعية العثور على البرنامج المساعد المسمى "iThenticate" وانقر فوق العنوان تثبيت البرنامج المساعد بالنقر فوق تثبيت

بعد ذلك، لكي تعمل هذه الإضافة، _يجب إضافة ما يلي إلى ملف config.inc.php الخاص بك_:

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; iThenticate Plugin Settings ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

[ithenticate]

; Enable iThenticate to submit manuscripts after submit step 4
ithenticate = On

; The username to access the API (usually an email address)
username = "user@email.com"

; The password to access the API
password = "password"
```

الآن يمكنك تمكين الإضافة: العودة إلى الإعدادات > الموقع > الإضافات العثور على ملحق iThenticate انقر فوق مربع الاختيار بجانبه لتمكينه

بالإضافة إلى ذلك، يتضمن OJS تلقائيًا رابط التحقق من الشبه كجزء من الإيداع الخاص بك.

لمزيد من المعلومات عن التحقق من الشبهة، يرجى زيارة موقع [Crossref](https://www.crossref.org/education/similarity-check/) و [انظر دليل التحقق من المستخدم](https://www.crossref.org/pdfs/similarity-check-user-guide-aug19.pdf).

للحصول على المساعدة في المشكلة التقنية (مثل رسالة خطأ أو خطأ)، يرجى الاتصال بفريق Turigenn مباشرة على [ccsupport@ithenticate.com](ccsupport@ithenticate.com)
