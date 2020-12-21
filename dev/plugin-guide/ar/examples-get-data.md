---
title: مثال - الحصول على البيانات - دليل الإضافات لOJS و OMP
---

# الحصول على البيانات

قد يحتاج البرنامج المساعد الخاص بك إلى الحصول على بيانات من التطبيق، مثل الرسائل المسلمة والمشكلات والمؤلفين والمستخدمين والملفات. استخدم [فئات الخدمة](/dev/documentation/en/architecture-services) لاسترداد المعلومات.

```php
$submissions = الخدمات::get('submissions')->getMany([
  'contextId' => $context->getId(),
  'عد' => 20،
  'تعيين' =>  التطبيق: :get()->getUser()->getId(),
])؛
```

إذا كانت فئة الخدمة غير موجودة للبيانات التي تريدها، قد تحتاج إلى استخدام [DAO](/dev/documentation/en/architecture-database).

```php
$authorDao = DAOregistry::getDAO('AuthorDAO');
$authors = $authorDao->getBySubmissionId($submissionId)؛
```

تعرف على المزيد حول [الخدمات](/dev/documentation/en/architecture-services)و [الكيانات](/dev/documentation/en/architecture-entities) و [DAOs](/dev/documentation/en/architecture-database) في وثائق المطور [](/dev/documentation/en).

---

عرض المزيد من [الأمثلة](./examples).
