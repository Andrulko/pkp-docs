# كشف الأخطاء في الإيداعات من تصدير XML

عندما تقوم بإرسال DOIs الخاص بك عن طريق [Crossref's واجهة](http://doi.crossref.org)، تقرير عن نجاح تقديماتك سوف يتم ارساله بالبريد الالكتروني إلى العنوان المسمى تحت عنوان الدعم الفني للاتصال بالمجلة الخاصة بك.  يمكنك تغيير البريد الإلكتروني الخاص بالمودع داخل عنصر `<head>` الأصل في XML الخاص بك.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<doi_batch xmlns="http://www.crossref.org/schema/4.3.6" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="4.3.6" xmlns:jats="http://www.ncbi.nlm.nih.gov/JATS1" xmlns:ai="http://www.crossref.org/AccessIndicators.xsd" xsi:schemaLocation="http://www.crossref.org/schema/4.3.6 http://www.crossref.org/schema/deposit/crossref4.3.6.xsd">
  <head>
    <doi_batch_id/></doi_batch_id>
    <timestamp/></timestamp>
    <depositor>
      <depositor_name>User Name</depositor_name>
      <email_address>Email for User</email_address>
    </depositor>
    <registrant/></registrant>
  </head>
```

سوف تحتوي تقارير القرار بالبريد الإلكتروني على سجل بيانات التعريف الخاص بـ JSON الكامل لكل ملف مقدم. إليك عينة من العرض الناجح:

```JSON
{"okage-type":"deposit","message-version":"1.0.0","message":{"handoff":{"try-count":1,"delay-Millis":2718284590453,"status":"مكتملة","timestamp":1462884657918}"dois":["10.4138\/atlgeol.2015.017"]","والدي":null,"filename":null",","،"dois":[10.4138\/atlgeol.017",",",",",",";parent":":nullll،",".Tue 10 May 8:57950:50:
```
هذه التقارير ليست سهلة الاستخدام بشكل خاص، ولكن يجب أن تكون قادراً على القراءة من خلال الملف لمشاهدة أي من التقارير التالية:

- "العد الناجح":1
- "failure-count":1

ويمثل الرقم المجاور للعدد عدد عدد الأخطاء في التقديم. في الأسفل, إذا فشل العنصر, سوف تعطَى السبب وراء فشل التقديم. وعلى سبيل المثال:

```JSON
{"الحالة":"failure","related-doi":null,"message":"خطأ: cvc-complex-type.2.4.b: محتوى العنصر 'صفحات' غير مكتمل. واحد من '{\"http:\/\/www.crossref.org\/schema\/4.3.6\":first_page}' متوقع. خطأ: cvc-complex type.2.4.b: محتوى 'صفحات' العنصر غير مكتمل. واحد من '{\"http:\/\/www.crossref.org\/schema\/4.3.6\":first_page}' متوقع.","message-types":[]}]},"test":false,"owner":"tesl","batch-id":"abd48f64-c670-4569-b3d7-e6249927f917"}
```

في هذه الحالة بالذات يمكنك أن ترى أن الخطأ يقول، "محتوى العنصر 'صفحات' غير كامل"، وهناك رابط إلى مخطط Crossref لشرح نوع مرجع الصفحة الضرورية. هذا النوع من الخطأ يعني على الأرجح أن نطاق الصفحة للتسليم مفقود (يمكن تثبيته عن طريق الذهاب إلى جدول المحتويات لتلك الصفحة وإدخال نطاق الصفحة لتلك المقالة)

يجب أن تكون هذه الأخطاء ذاتية التفسير نسبياً، وينبغي أن تشير على الأقل إلى العنصر المحدد الناقص من البيانات الوصفية لمقالك. ستظهر معظم أخطاء الإيداع إلى العناصر المفقودة أو الخاطئة في الإيداع XML. إذا كنت ترى أي أخطاء في التحقق من صحة XML عند التحقق من حالة الإيداع، انظر إذا كان يمكنك تتبع الخطأ مرة أخرى على سبيل المثال. مكون مفقود في إعدادات المجلة أو المكونات الإضافية، على سبيل المثال ISSN.

# التحقق قبل التقديم

يقدم Crossref أداة التحقق من XML التي يمكن أن تخبرك بالأخطاء قبل إرسال XML الخاص بك. تتيح خدمة [التحقق من جودة البيانات الوصفية](http://www.crossref.org/02publishers/parser.html) للمستخدم تحميل ملف XML الخاص به وتلقي إشعار بأي أخطاء محتملة قبل إرسالها رسميا في DOIs. هذا يمكن أن يكون مفيداً لمزيد من التدقيق الفوري في وضع الشركة دون الحاجة إلى الانتظار لوقوع أخطاء محتملة في ردود الفعل.
