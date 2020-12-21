# كائنات & فصول

الإضافات في OJS 2.x موجهة إلى الكائن. ويوسع كل مكون إضافي فئة تحدد وظائف فئته ويكون مسؤولا عن تنفيذها.

**الجدول 5-1 الإضافات**

| الفئة          | فئة بدائية                                                          |
| -------------- | ------------------------------------------------------------------- |
| `generic`      | `GenericPlugin (classes/plugins/GenericPlugin.inc.php)`             |
| `importexport` | `استيراد ExportPlugin (classes/plugins/ImportExportPlugin.inc.php`) |
| `المصادقة`     | `AuthPlugin (classes/plugins/AuthPlugin.inc.php)`                   |
| `البوابات`     | `إضافة بوابة (classes/plugins/GatewayPlugin.inc.php)`               |

كل فئة أساسية تحتوي على وصف للوظائف التي يجب أن تنفذها الإضافات في تلك الفئة.

تتم إدارة الإضافات بواسطة فئة `pluginRegistry` (يتم تنفيذها في `classes/plugins/Pluginregistry.inc.php`). يمكنهم تسجيل الروابط باستخدام صف `Hookregis` (تم تنفيذه في `classes/plugins/Hookregistry.inc.php`).

