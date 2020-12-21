# التذييل ألف: إنشاء صندوق رملي محمي OJS 3 مرشد مع Git

وتصف الوثيقة التالية تدفقاً عاماً للعمل من أجlkkl;kل إنشاء صندوق رملي ذي أساس غيت لمجلة إنتاج غير مجهزة حالياً. ويقدم تعليمات بشأن كيفية الحد من الوصول العرضي إلى البريد الإلكتروني الصادر، وما إلى ذلك. YMV. قم بالتكيف مع بيئتك؛ استخدم على مسؤوليتك الخاصة.

## إعداد بيئة Git

README هنا: [https://github.com/pkp/ojs](https://github.com/pkp/ojs) لديه تعليمات حول التثبيت من git. وما نفعله هو كما يلي:

1. إنشاء مستخدم أو قاعدة بيانات MySQL أو PostgreSQL OJS. الأمر الذي نستخدمه هو كما يلي: قد يكون مختلفاً بالنسبة لك اعتماداً على بيئتك، والوصول إلى الجذر، إلخ:

   **MySQL**
   ```
   mysql -u root -e "أنشئ DATABASE `ojs-sandbox` DFAUUTF8; GRANT All on `ojs-sandbox`.* to `ojs'@localhost IDENTIFIED by 'ojs'" -p
   ```
   **PostgreSQL**
   ```
   psql -h localhost -U postgres -d postgres -c "إنشاء إستخدام متوقع مع إستخدام مِنْقْدِيْ مِنْمِنْ مِنْبَيَسِرِسِلِس مِنْسْرِلِسِلِسِلِسِلِسِلِسِلِسِلِِنِِِنْسِلِِِِِِِِِنْسِتِيْرِيْنِنِنِيْسِيْسِيْسِنِيْسِنِيْسِيْسِيْسِيْسْسِيْرِيْلِيْسِيْسْسْسِيْسِيْ تثني على "مدير الموقع"؛
   إنشاء نظام بيانات ojs-sandbox OWNER ojs;" -W
   ```

2. اخرج الفرع المستقر من GitHub. سيكون المسار محدداً لتثبيت Apache الخاص بك، ويمكنك تحديث الفرع إلى أحدث فرع مستقر:

   ```
   cd <httpd-docs-folder>
   BRANCH='stable-3_2_1'
   git clone -b $BRANCH --single-branch https://github.com/pkp/ojs.git ./
   git branch --unset-upstream $BRANCH
   chmod -R 755 *
   ```

3. احصل على مكتبة PKP المقابلة و سحب فرع ثابت من GitHub، مع التأكد من أن الفرع يطابق نفس الفرع المشار إليه أعلاه:

   ```
   تحديث الوحدة الفرعية git --init --متكرر
   ```

4. تثبيت الملحن:

   ```
   cd ../..
   php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
   php -r "if (hash_file('sha384', 'composer-setup. hp') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer corrupt'; unlink('composer-setup. hp'); } echo PHP_EOL;
   php composer-setup.php
   php -r "unlink('composer-setup.php');"
   ```

5. تثبيت تبعيات الملحن:

   ```
   cd lib/pkp
   php ../../../composer.phar --no-dev المثبت
   cd ../../plugins/paymethod/paypal
   php ../../../../composer.phar --no-dev المثبت
   cd ../../../../plugins/generic/citationStyleLanguage
   php ../../../../composer.phar --no-dev المثبت
   ```

6. تثبيت Node.js التبعيات \(NOTE: npm يجب تثبيته على الخادم\):

   ```
   cd ../../..
   قم بتثبيت
   npm تشغيل البناء
   ```

7. إنشاء ملف تكوين جديد:

   ```
   cd ../../..
   cp config.TEMPLATE.inc.php config.inc.php
   chmod 600 config.inc.php
   ```

وفي هذه المرحلة، ينبغي أن يكون لديك نظام وقاعدة بيانات جاهزين تماما للدائرة الثالثة للقانون.

## **إزالة أي احتمال للمهام المجدولة من أن يتم تشغيلها في خادم التجهيز**

حذف البرنامج المساعد Acron \(البرنامج المساعد Acron يمكنه تشغيل المهام المجدولة التي سيتم تشغيلها دون الاعتماد على وظيفة كرون\):

   ```
   rm -rf plugins/generic/acron
   rm -rf lib/pkp/plugins/generic/acron
   ```

يجب إعادة تثبيت هذه الإضافة بعد الذهاب إلى الإنتاج، الذي، إذا كنت تقوم بتشغيل الأشياء عبر git، يمكنك القيام بما يلي:

   ```
   git دفع الإضافات/العامة/أكرون
   cd lib/pkp
   git الخروج الإضافات / العامة/الأوكرون
   ```

## النسخ الاحتياطي لملفات التقديم والجمهور وقواعد البيانات ونسخها

يتم تنفيذ هذه الأوامر عند تثبيت الإنتاج، وهي أوامر النسخ الاحتياطي/الأرشيف النموذجية.

البيانات:

* **MySQL**: نحن عادة نستخدم mysqldump لإعداد نسخة من قاعدة البيانات:
   ```
   mysqldump db\_name --opt --default-character-set=utf8 --result-file=~/client\_db.sql -u db\_user -p
   ```
* **PostgreSQL**: نحن عادة نستخدم [pg_dumpall](https://www.postgresql.org/docs/current/backup-dump.html#BACKUP-DUMP-ALL) لإعداد نسخة من قاعدة البيانات والبيانات على نطاق المجموعة (مثل تعريف المستخدمين):
   ```
   pg_dumpall -U postgres -h localhost -d postgres > ~/client_db.sql
   ```

ملفات التقديم: يمكنك العثور على الدليل الصحيح في ملف OJS config.inc.php ، ابحث عن معلمة "files\_dir". وعادة ما نضغط هذا الأمر لتيسير نقل:

   ```
   cd <submission files dir>
   tar -cvzf ~/files.tar.gz ./
   ```

الملفات العامة: يمكن أن يشمل ذلك أشياء مثل صور الغلاف وما إلى ذلك، ويوجد في دليل نظام OJS في الدليل الفرعي "العام/":

   ```
   cd <ojs-system-dir>/public
   tar -cvzf ~/public.tar.gz ./
   ```

نقل الملفات إلى خادم التجهيز: نحن عادة نستخدم `scp` أو `rsync`. يجب على أنظمتك أن تعرف ما الذي تستخدمه هنا، ولكن بالنسبة لنا عادةً ما يكون شيئاً مماثلا:

  ```
  rsync -avz client\_db.sql username@stagingserver.org:/~
  rsync -avz public.tar.gz username@stagingserver.org:/~
  rsync -avz files.tar.gz username@stagingserver.org:/~
  ```

## تثبيت ملفات التقديم والجمهور وقواعد البيانات إلى المواقع الصحيحة

تثبيت قاعدة البيانات (قد يختلف هذا حسب اسم المستخدم واسم قاعدة البيانات وكلمة المرور التي حددتها سابقاً):

* **MySQL**
   ```
   mysql -u ojs-sandbox -p ojs-sandbox < ~/client\_db.sql
   ```
* **PostgreSQL**
   ```
   psql -U postgres -h localhost -f ~/client_db.sql postgres
   ```

تثبيت ملفات التقديم:

   ```
   tar -xvf ~/files.tar.gz <files directory>
   ```

تثبيت الملفات العامة:

   ```
   tar xvf ~/public.tar.gz <ojs-folder>/public/
   ```

تحرير ملف `config.inc.php` وتغيير قاعدة البيانات و files_dir.

   ```
   vi config.inc.php
   ```

وعند هذه النقطة، ينبغي أن تكون جميع الملفات وجداول DB ذات الصلة موجودة، وينبغي أن يشير ملف التكوين إلى تلك المواقع.

## الحصول على جميع رسائل البريد الإلكتروني في النظام بحيث لا يرسل النظام البريد الإلكتروني عن طريق الخطأ

إذا كنت تقوم بتشغيل صندوق الرمل على الخادم الخاص به، قد ترغب في النظر في تعطيل أي وظيفة من وظائف البريد الإلكتروني على الخادم. ولكن سيعمل ما يلي أيضا (من حيث أن أي رسائل البريد الإلكتروني المرسلة سترسل إلى عناوين البريد الإلكتروني غير المنتجة).

يمكنك تعيين عناوين البريد الإلكتروني الخاصة بك إلى عنوان [البريد](https://www.mailinator.com/) ، مما يعني أن رسائل البريد الإلكتروني سيتم إرسالها إلى صندوق الوارد العام الذي يمكن الوصول إليه (هـ). . username@mailinator.com)، أو استخدم عنوان بريد إلكتروني مزيف. يمكنك أيضا تعيين رسائل البريد الإلكتروني استنادا إلى أدوار محددة للمستخدم. سوف تحتاج أولاً إلى الوصول إلى قاعدة البيانات الخاصة بك:

* **MySQL**
   ```
   mysql -u ojs -pojs ojs-sandbox
   ```
* **PostgreSQL**
   ```
   psql -h localhost -U ojs -d 'ojs-sandbox'
   ```

لتعيين جميع عناوين البريد الإلكتروني للمستخدم على username@mailinator.com:

   ```
   تحديث المستخدمين تعيين البريد الإلكتروني =CONCAT\(username,'@mailinator.com’\);
   ```

لتعيين جميع رسائل البريد الإلكتروني المتصلة بالتقديم، مثل رسائل المساهمين، إلى test@example.com:

   ```
   تحديث المؤلفين تعيين البريد الإلكتروني = 'test@example.com'
   ```

## (اختياري) إضافة حماية لكلمة المرور للموقع بحيث لا يتم الدخول إليه بطريق الخطأ أو الزحف أو الخ.

نحن نفعل ذلك لجميع صناديق الرمل عن طريق إضافة .htaccess و .htpasswd إلى جذر الويب الخاص بالصندوق الرملي سوف يعرف أنظمتك كيف تفعل ذلك.

## تشغيل الترقية

من صندوق الرمل يشغل جذر الويب هذا الأمر:

   ```
   أدوات php /upgrade.php الترقية
   ```

في هذه المرحلة، إذا اكتمل الترقية، يجب أن يكون لديك ترقية رمل نظيفة ومحمية تعمل بنظام OJS 3 يمكنك إدارتها عن طريق git.
