---
title: بدء - الوثائق التقنية - OJS<unk> OMP<unk> OPS
---

# بدء العمل

سيصف هذا القسم كيفية تثبيت التطبيق، والمساهمة في التغييرات، والبقاء على علم بآخر التغييرات.

> هذا الدليل يفترض أنك تعرف كيفية تشغيل خادم محلي، والعمل مع التحكم في إصدار git وتشغيل الأدوات من سطر الأوامر. 
> 
> {:.warning}

## المتطلبات التقنية

- PHP 7.0+
- MySQL 4.1+ _or_ PostgreSQL 9.1.5+

## تثبيت

قم بتجميع واستنساخ [OJS](https://github.com/pkp/ojs) أو [OMP](https://github.com/pkp/omp) مستودع على GitHub. (كيفية [شوكة واستنساخ مستودع على GitHub](https://help.github.com/en/articles/fork-a-repo).)

من المحطة الطرفية الخاصة بك، انتقل إلى الدليل الجذر للتطبيق وقم بتشغيل الأمر التالي للتحقق من الوحدات الفرعية:

```
تحديث الوحدة الفرعية git --init --متكرر
```

نسخ ملف التكوين الافتراضي.

```
cp config.TEMPLATE.inc.php config.inc.php
```

افتح ملف `config.inc.php` ، وابحث عن إعدادات قاعدة البيانات ، وتحديثها لتطابق بيانات الاعتماد لخادم SQL الخاص بك.

تثبيت الإعتمادات مع [الملحن](https://getcomposer.org/).

```
المؤلف --working-dir=lib/pkp تحديث
composer --working-dir=plugins/paymethod/paypal تحديث
```

تشغيل الأمر التالي إذا كنت تقوم بتثبيت OJS.

```
تحديث المؤلف --working-dir=plugins/generic/citationStyleLanguage
```

تثبيت الإعتمادات مع [NPM](https://www.npmjs.com/).

```
قم بتثبيت
npm تشغيل البناء
```

قم بتشغيل الأمر التالي لتشغيل التطبيق باستخدام خادم PHP المدمج.

```
php -S localhost:8000
```

قم بتحميل المتصفح الخاص بك وانتقل إلى `http://localhost:8000` لتثبيت التطبيق.

## الفروع

ويمكن العثور على النسخ المنشورة من البرنامج في الفروع في مستودع git. على سبيل المثال، قم بتشغيل الأمر التالي للتحقق من الإصدار 3.1.2 من البرنامج.

```
git الدفع المستقرة-3_1_2
```

## البعيد

للحصول على تغييرات على التطبيق الذي تم إجراؤه بعد شكلك، أضف جهاز `التمهيدي` البعيد.

من أجل OJS:

```
git بعد إضافة upstream git@github.com:pkp/ojs.git
cd lib/pkp
git remote add upstream git@github.com:pkp/pkp-lib. إنها
cd ../ui-libr
git بعد إضافة upstream git@github.com:pkp/ui-library.git
cd ../..
```

ل OMP:

```
git بعد إضافة upstream git@github.com:pkp/omp.git
cd lib/pkp
git remote add upstream git@github.com:pkp/pkp-lib. إنها
cd ../ui-libr
git بعد إضافة upstream git@github.com:pkp/ui-library.git
cd ../..
```

قم بتشغيل الأوامر التالية كلما كنت ترغب في سحب أحدث التغييرات إلى مستودعك.

```
# قم بتحديث التطبيق
git هي الرئيسية
git تسحب البوابة
git push

# قم بتحديث وحدة pkp-lib الفرعية
cd lib/pkp
git master الخروج
git سحب الرئيس الأعلى
git push

# قم بتحديث الوحدة الفرعية للمكتبة ui-Libr
cd. /ui-Libr
git اتقن عملية الدفع
git اتقان سحب إلى الأعلى
git push

cd ../..
```

## التحديثات

عندما تكون قد قمت بسحب التغييرات لأسفل من جهاز التحكم `أعلى` ، قم بتشغيل ما يلي لمزامنة الوحدات الفرعية `lib/pkp` و `lib/ui-libr`.

```
تحديث الوحدة الفرعية git --init --متكرر
```

قد تحتاج إلى تحديث الإعتمادات وإعادة بناء حزمة جافا سكريبت.

```
المؤلف --working-dir=lib/pkp تحديث
npm تثبيت
npm تشغيل البناء
```

في بعض الأحيان يقوم تغيير التعليمات البرمجية بتعديل بنية قاعدة البيانات وسوف تحتاج إلى تشغيل البرنامج النصي للترقية.

```
أدوات php /upgrade.php الترقية
```

## المساهمات

يجب كتابة جميع المساهمات في فرع ودفعها إلى شورك. ثم افتح [طلب سحب](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork) لمستودع PKP.

---

الآن بعد أن كنت تشتغل، تعلم المزيد عن [هندسة التطبيقات](./architecture).
