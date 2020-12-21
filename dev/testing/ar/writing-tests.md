---
title: اختبارات الكتابة - الاختبار - OJS/OMP
---

# اختبارات الكتابة

يجب كتابة الاختبارات كلما تغيرت وظيفة التطبيق. وقد يحدث هذا عندما تضاف ميزة جديدة أو عندما يتم توسيع أو إعادة النظر في ميزة قائمة ولا تغطي الاختبارات الحالية جميع حالات الاستخدام.

وكثيراً ما يكون من المناسب إضافة أحد الاختبارات القائمة بدلاً من إنشاء اختبار جديد. يمكن العثور على هذه الاختبارات في `cypress/test` و `lib/pkp/cypress/test`.

> إذا كنت تكتب اختبارا للتحقق من جزء معين من سير العمل التحريري، فيجب وضعه في `cypress/tests/data`. إذا كنت تكتب اختبار لشيء آخر، مثل الإحصاءات أو إعدادات المجلة، فيجب أن توضع في `cypress/tests/integration`. 
> 
> {:.notice}

اقرأ وثائق Cypress لتعلم كيفية كتابة اختبار [الأول](https://docs.cypress.io/guides/getting-started/writing-your-first-test.html)الخاص بك، [تنظيم الاختبارات](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests.html#Test-Structure)، و [تتفاعل مع الأزرار والحقول](https://docs.cypress.io/guides/core-concepts/interacting-with-elements.html#Actionability).

## الأوامر

توفر الأوامر المخصصة طريقة لمشاركة رمز الاختبار عبر التطبيقات وأداء التفاعلات الروتينية. على سبيل المثال، يوجد أمر لتسجيل الدخول.

```js
cy.login('admin', 'admin');
```

وتسجيل الخروج.

```js
cy.logout();
```

التسجيل كمستخدم جديد.

```js
cy.register({
    'username': 'ccorino',
    'givenName': 'Carlo',
    'familyName': 'Corino',
    'Association': 'University of Bologna',
    'country': 'إيطاليا'
});
```

أو إنشاء مستخدم جديد من منطقة المسؤول.

```js
cy.login('admin', 'admin');
cy. reateUser({
    'username': 'skumar',
    'givenName': 'Sabine',
    'familyName': 'Kumar',
    'البلد': 'سنغافورة'،
    'الانتساب ': 'الجامعة الوطنية لسنغافورة',
    'دوريات': ['Proofreader']
})؛
```

قراءة جميع الأوامر في ملف `lib/pkp/cypress/support/commands.js`.

---

تعلم كيفية [أخطاء اختبار التصحيح](./debug).