---
book: تقاطع ojs-يدوي
version: 3.1
---

# التحقق من الشبه

ويشمل OJS 3-1-2 تقديم الدعم لسلاجيات iThenticate التحقق من خدمة التحقق من تشابه النشاط.

[https://github.com/asmecher/plagiarism](https://github.com/asmecher/plagiarism)

لكي تعمل هذه الإضافة، _يجب إضافة ما يلي إلى ملف config.inc.php الخاص بك_:

````
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
````

وبالإضافة إلى ذلك، ستقدم عناوين موقع SimCheck الكاملة للنص إلى Crossref كجزء من عملية تقديم الرمز DOI تلقائيا.

## تثبيت و تمكين البرنامج المساعد

1. انتقل إلى المستخدم **لوحة التحكم**.
2. انقر فوق إعدادات ****.
3. انقر فوق **إضافات**.
4. انقر فوق عنصر القائمة الفرعية **معرض الإضافات**.
5. ابحث عن البرنامج المساعد المسمى "iThenticate" وانقر على العنوان.
6. تثبيت الملحق بالنقر فوق "تثبيت".
7. بمجرد الحصول على إشعار بأن الإضافة مثبتة، انقر فوق عنصر القائمة الفرعية **الإضافات**.
8. حدد موقع إضافة iThenticate وانقر فوق مربع الاختيار الأزرق على اليمين لتمكينه.
