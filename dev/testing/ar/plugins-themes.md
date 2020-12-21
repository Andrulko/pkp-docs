---
title: الإضافات والمواضيع - الاختبار - OJS/OMP
---

# الإضافات والمواضيع

يمكن أن تستخدم الإضافات والمواضيع أجزاء من اختبارات التطبيق لإعداد بيئة الاختبار وتشغيل الاختبارات. هذا يسمح لكل مكون إضافي بتنفيذ [التكامل المستمر](./continuous-integration) اختبار في المستودع الخاص به.

تم تكوين [الصفحات الثابتة](https://github.com/pkp/staticPages/) و [إرسال سريع](https://github.com/pkp/quickSubmit) الإضافات و [مخطوطة](https://github.com/NateWr/defaultManuscript) السمة للاختبار. ملف `.travis.yml` في كل اعدادات المستودع هو اختبارات التكامل. يمكن العثور على الاختبارات التي يتم تشغيلها في كل دليل `cypress/test` الخاص بالمستودع.

يمكن تشغيل اختبارات الإضافات و السمة محليا عن طريق تشغيل الأمر التالي في الدليل الجذري للتطبيق.

```
cd path/to/ojs
npx cypress run --config IntegrationFolder=plugins/generic/staticPages/cypress/tests
```
