# قائمة الروابط

وتصف القائمة التالية جميع الروابط المدمجة في الجريدة الرسمية ابتداء من الإصدار 2-1. أوامر قبل أسماء المتغيرات (على سبيل المثال). `&$sourceFile`يشير إلى أن المعلمة قد تم تمريرها إلى مرجع الاتصال بالرابط في مصفوفة المعلمات عن طريق المرجع ويمكن تعديلها عن طريق الاتصال بالرابط. يتم تحديد تأثير قيمة إرجاع الاتصال بالرابط حيثما ينطبق ذلك؛ بالإضافة إلى هذا، سوف تحدد دائما قيمة إرجاع الاتصال الرابط ما إذا كان سيتم تخطي ردود المكالمات الأخرى المسجلة على نفس الرابط.

**الجدول 5-2 قائمة الروابط**

<table spaces-before="0" line-breaks-before="2">
  <tr>
    <th>
      الاسم
    </th>
    
    <th>
      البارامترات
    </th>
    
    <th>
      الوصف
    </th>
  </tr>
  
  <tr>
    <td>
      <code>حامل</code>
    </td>
    
    <td>
      <code>&$page</code>, <code>&$op</code>, <code>&$sourceFile</code>
    </td>
    
    <td>
      ينادي بها مؤشر <code>الرئيسي لـ OJS. hp</code>{.filename} سكريبت بعد الصفحة (<code>&$page</code>)، عملية (<code>&$op</code>)، و ملف كود المعالج (<code>&$sourceFile</code>) تم تحديد أسماء ، ولكن قبل <code>$sourceFile</code> تم تحميله. يمكن استخدامه لاعتراض طلبات المتصفح للتعامل مع المكون الإضافي. العودة <code>الحقيقية</code> من رد الاتصال سوف تمنع OJS من تحميل المواد المعالج في <code>$sourceFile</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ArticleEmailLogDAO::&lt;unk> _returnLogEntryFromRow</code>
    </td>
    
    <td>
      <code>&$entry</code>, <code>&$row</code>
    </td>
    
    <td>
      يُسمى بعد <code>مادة البريد الإلكتروني لوغداو</code> يبني <code>إدخال مادة</code> (<code>&$entry</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الإدخال إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ArticleEventLogDAO::&lt;unk> _returnLogEntryFromRow</code>
    </td>
    
    <td>
      <code>&$entry</code>, <code>&$row</code>
    </td>
    
    <td>
      يُسمى بعد <code>المادةEventLogDAO</code> يبني <code>إدخالًا للمادة</code> (<code>&$entry</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الإدخال إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ArticleCommentDAO::​_returnArticleCommentFromRow</code>
    </td>
    
    <td>
      <code>&$article</code>تعليق، <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>المادة التعليق</code> يبني <code>تعليق المادة</code> (<code>&$articleComment</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يعاد التعليق إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مادة داو:&lt;unk> _returArticleFromRow</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>المادة</code> يبني <code>مقالة</code> (<code>&$article</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال المادة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المادة FileDAO:&lt;unk> _returArticleFileFromRow</code>
    </td>
    
    <td>
      <code>&$articleFile</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>المادة</code> يبني <code>ملف المادة</code> (<code>&$articleFile</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة ملف المقالة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مادة غاليداو:&lt;unk> _returnGalleyFromRow</code>
    </td>
    
    <td>
      <code>&$galley</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>ماكلي غاليداو</code> يبني <code>ماكلي غالي</code> (<code>&$galley</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال الوادي إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ArticleNoteDAO::​_returnArticleNoteFromRow</code>
    </td>
    
    <td>
      <code>&$articleNote</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>المادة NoteDAO</code> يبني <code>ملاحظة المادة</code> (<code>&$articleNote</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الإدخال إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مؤلف DAO::&lt;unk> _returnAuthorFromRow</code>
    </td>
    
    <td>
      <code>&$author</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>AuthorDAO</code> يبني <code>مؤلف</code> (<code>&$author</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال صاحب البلاغ إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>SuppFileDAO::&lt;unk> _returSuppFileFromRow</code>
    </td>
    
    <td>
      <code>&$suppFile</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>SuppFileDAO</code> يبني <code>ملف دعم</code> (<code>&$suppFile</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الملف التكميلي إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>نشر ArticleDAO::&lt;unk> _returnPublishedArticleFromRow</code>
    </td>
    
    <td>
      <code>&$publishedArticle</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>نشر المادة</code> يقوم ببناء <code>مقالة منشورة</code> (<code>&$publishedArticle</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال المقالة المنشورة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>التعليق DAO:&lt;unk> _return CommentFromRow</code>
    </td>
    
    <td>
      <code>&$comment</code>, <code>&$row</code>, <code>&$childLevels</code>
    </td>
    
    <td>
      يسمى بعد <code>تعليق DAO</code> يبني <code>تعليق</code> (<code>&$comment</code>) من صف قاعدة البيانات (<code>&$row</code>)، قبل جلب <code>&$childLevels</code> تعليقات الطفل وإعادة التعليق إلى وظيفة الاتصال. العودة <code>true</code> ستمنع OJS من جلب أي تعليقات فرعية.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> إعادة توجيه</code>
    </td>
    
    <td>
      <code>&$url</code>
    </td>
    
    <td>
      يُسمى قبل <code>طلب::&lt;unk> إعادة توجيه</code> تقوم بإعادة توجيه إلى <code>&$url</code>. العودة <code>true</code> ستمنع OJS من القيام بإعادة التوجيه بعد الانتهاء من الرابط. يمكن استخدامها لاعتراض وإعادة كتابة التوجيهات.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getBaseUrl</code>
    </td>
    
    <td>
      <code>&$baseUrl</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getBaseUrl</code> بعد تحديد عنوان URL الأساسي ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getBasePالمسار</code>
    </td>
    
    <td>
      <code>&$basePath</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getBasePالمسار</code> بعد تحديد المسار الأساسي ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getIndexUrl</code>
    </td>
    
    <td>
      <code>&$indexUrl</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getIndexUrl</code> بعد تحديد رابط الفهرس ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getCompleteUrl</code>
    </td>
    
    <td>
      <code>&$completeUrl</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getCompleteUrl</code> بعد تحديد عنوان URL الكامل ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getrequestUrl</code>
    </td>
    
    <td>
      <code>&$requestUrl</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getrequestUrl</code> بعد تحديد عنوان URL الطلب ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getQueryString</code>
    </td>
    
    <td>
      <code>&$queryString</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getQueryString</code> بعد تحديد سلسلة الاستعلام ولكن قبل إعادتها إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getrequestPالمسار</code>
    </td>
    
    <td>
      <code>&$requestPath</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getrequestPath</code> بعد تحديد مسار الطلب ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getServerHhost</code>
    </td>
    
    <td>
      <code>&$serverHost</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getServerHost</code> بعد تحديد مضيف الخادم ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب: &lt;unk> بروتوكول</code>
    </td>
    
    <td>
      <code>&$protocol</code>
    </td>
    
    <td>
      سُجلت المرة الأولى <code>طلب::&lt;unk> getProtocol</code> بعد أن تم تحديد البروتوكول (<code>± p</code> أو <code>± ps</code>) ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getRemoteAddr</code>
    </td>
    
    <td>
      <code>&$remoteAddr</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getRemoteAddr</code> بعد تحديد العنوان البعيد ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getRemotedomain</code>
    </td>
    
    <td>
      <code>&$remoteDomain</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getRemotedomain</code> بعد تحديد النطاق البعيد ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getUseragent</code>
    </td>
    
    <td>
      <code>&$userAgent</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getUserوكيل</code> بعد تحديد وكيل المستخدم ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الطلب::&lt;unk> getrequestedJournalPالمسار</code>
    </td>
    
    <td>
      <code>&$journal</code>
    </td>
    
    <td>
      تم قبول أول مرة <code>طلب::&lt;unk> getrequestedJournalPath</code> بعد تحديد مسار المجلة المطلوبة ولكن قبل إعادته إلى المتصل. يتم استخدام هذه القيمة لجميع المكالمات اللاحقة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>[Anything]DAO::&lt;unk> البناء</code>
    </td>
    
    <td>
      <code>&$dataSource</code>
    </td>
    
    <td>
      يُسمى كلما تم استدعاء بناء DAO مع <code>&$dataSource</code> المحدد. يجب استخدام هذا الرابط فقط مع PHP &gt;= 4.3.0.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>[Anything]DAO::&lt;unk> [أي دالة تستدعي DAO::&lt;unk> استرداد]</code>
    </td>
    
    <td>
      <code>&$sql</code>, <code>&$params</code>, <code>&$value</code>
    </td>
    
    <td>
      أي وظيفة DAO تتصل DAO::<unk> الاسترجاع ستتسبب في تشغيل الرابط. يمكن تعديل بيان SQL في <code>&$sql</code> وكذلك معلمات ADODB في <code>&$params</code>. إذا كان المقصود من رد الاتصال بالربط أن يحل محل وظيفة هذا المكالمة بالكامل، <code>&$value</code> يجب أن تتلقى النتيجة المقصودة من المكالمة الاسترجاعية ويجب أن يعود الرابط <code>true</code>. يجب استخدام هذا الرابط فقط مع PHP &gt;= 4.3.0.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>[Anything]DAO::&lt;unk> [أي دالة تستدعي DAO::&lt;unk> استرداد ذاكرة التخزين المؤقت]</code>
    </td>
    
    <td>
      <code>&$sql</code>, <code>&$params</code>, <code>&$secsToCache</code>, <code>&$value</code>
    </td>
    
    <td>
      أي وظيفة DAO تتصل <code>DAO::&lt;unk> استرداد ذاكرة التخزين المؤقت</code> ستتسبب في تشغيل الرابط. يمكن تعديل عبارة SQL في <code>&$sql</code> ، كما يمكن معلمات ADODB في <code>&$params</code> و قيمة الثواني إلى ذاكرة التخزين المؤقت في <code>&$secsToCache</code>. إذا كان المقصود من رد الاتصال بالربط أن يحل محل وظيفة هذا المكالمة بالكامل، <code>&$value</code> يجب أن تتلقى النتيجة المقصودة من المكالمة الاسترجاعية ويجب أن يعود الرابط <code>true</code>. يجب استخدام هذا الرابط فقط مع PHP &gt;= 4.3.0.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>[Anything]DAO::&lt;unk> [أي دالة تستدعي DAO::&lt;unk> الاسترجاع]</code>
    </td>
    
    <td>
      <code>&$sql</code>, <code>&$params</code>, <code>&$numRows</code>, <code>&$offset</code>, <code>&$value</code>
    </td>
    
    <td>
      أي وظيفة DAO تتصل <code>DAO::&lt;unk> استرداد ذاكرة التخزين المؤقت</code> ستتسبب في تشغيل الرابط. يمكن تعديل عبارة SQL في <code>&$sql</code> ، كما يمكن معلمات ADODB في <code>&$params</code>، و طلب جلب و الحد المحدد في <code>&$offset</code> و <code>&$numRows</code>. إذا كان المقصود من رد الاتصال بالربط أن يحل محل وظيفة هذا المكالمة بالكامل، <code>&$value</code> يجب أن تتلقى النتيجة المقصودة من المكالمة الاسترجاعية ويجب أن يعود الرابط <code>true</code>. يجب استخدام هذا الرابط فقط مع PHP &gt;= 4.3.0.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>[Anything]DAO::&lt;unk> [أي دالة تستدعي DAO::&lt;unk> استرداد الترادج]</code>
    </td>
    
    <td>
      <code>&$sql</code>, <code>&$params</code>, <code>&$dbResultRange</code>, <code>&$value</code>
    </td>
    
    <td>
      أي وظيفة DAO تتصل <code>DAO::&lt;unk> retrieveRange</code> ستتسبب في تشغيل الرابط. يمكن تعديل عبارة SQL في <code>&$sql</code> ، كما يمكن معلمات ADODB في <code>&$params</code> ومعلومات النطاق في <code>&$dbResultRange</code>. إذا كان المقصود من رد الاتصال بالربط أن يحل محل وظيفة هذا المكالمة بالكامل، <code>&$value</code> يجب أن تتلقى النتيجة المقصودة من المكالمة الاسترجاعية ويجب أن يعود الرابط <code>true</code>. يجب استخدام هذا الرابط فقط مع PHP &gt;= 4.3.0.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>[Anything]DAO::&lt;unk> [أي دالة تدعى DAO::&lt;unk> تحديث]</code>
    </td>
    
    <td>
      <code>&$sql</code>, <code>&$params</code>, <code>&$value</code>
    </td>
    
    <td>
      أي وظيفة DAO تستدعي <code>DAO::&lt;unk> تحديث</code> ستتسبب في تشغيل الرابط. يمكن تعديل بيان SQL في <code>&$sql</code> وكذلك معلمات ADODB في <code>&$params</code>. إذا كان المقصود من رد الاتصال بالربط أن يحل محل وظيفة هذا المكالمة بالكامل، <code>&$value</code> يجب أن تتلقى النتيجة المقصودة من المكالمة الاسترجاعية ويجب أن يعود الرابط <code>true</code>. يجب استخدام هذا الرابط فقط مع PHP &gt;= 4.3.0.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مؤقت FileDAO:&lt;unk> _returTemporaryFileFromRow</code>
    </td>
    
    <td>
      <code>&$temporaryFile</code>, <code>&$row</code>
    </td>
    
    <td>
      يُدعى بعد أن يقوم مؤقتو بإنشاء ملف مؤقت (<code>&$temporaryFile</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الملف المؤقت إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>Locale::​_cacheMiss</code>
    </td>
    
    <td>
      <code>&$id</code>, <code>&$locale</code>, <code>&$value</code>
    </td>
    
    <td>
      يُسمى إذا تعذر العثور على مفتاح محلي في ذاكرة التخزين المؤقت المحلية. <code>&$id</code> هو المفتاح للسلسلة المحلية المفقودة، <code>&$locale</code> هو الاسم المحلي (مثل <code>en_US</code>). إذا كان هذا الرابط سيوفر النتيجة لهذا المخبئ مفقود، يجب تخزين القيمة في <code>&$value</code> ويجب أن يعود الرابط إلى <code>true</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تثبيت:&lt;unk> مثبت</code>
    </td>
    
    <td>
      <code>&$installer</code>, <code>&$descriptor</code>, <code>&$params</code>
    </td>
    
    <td>
      يُسمى عندما يكون المثبت مثالياً مع مسار التوصيف في <code>&$descriptor</code> والمعلمات في <code>&$params</code>. إذا عاد الرابط صحيح، فلن يتم القيام بالتهيئة المعتادة لـ <code>Installer</code> سمات.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المثبت::&lt;unk> تدمير</code>
    </td>
    
    <td>
      <code>&$installer</code>
    </td>
    
    <td>
      يتم تشغيلها عند استدعاء طريقة تنظيف المثبت.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المثبت::&lt;unk> سابقة التثبيت</code>
    </td>
    
    <td>
      <code>&$installer</code>, <code>&$result</code>
    </td>
    
    <td>
      يسمى بعد اكتمال مهام ما قبل تثبيت المثبت ولكن قبل أن يتم إرجاع نتيجة النجاح / الفشل في <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المثبت::&lt;unk> تثبيت</code>
    </td>
    
    <td>
      <code>&$installer</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمى عندما يتم إكمال مهام ما بعد التثبيت ولكن قبل أن يتم إرجاع النجاح/الفشل في <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المثبت::&lt;unk> parseInstaller</code>
    </td>
    
    <td>
      <code>&$installer</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمى بعد أن أكمل المثبت تحليل مجموعة مهمة التثبيت ولكن قبل أن يتم إرجاع نتيجة النجاح / الفشل في <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المثبت::&lt;unk> executeInstaller</code>
    </td>
    
    <td>
      <code>&$installer</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمى بعد تنفيذ المثبت ولكن قبل أن يتم إرجاع النجاح/<unk> نتيجة الفشل في <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المثبت::&lt;unk> تحديث الإصدار</code>
    </td>
    
    <td>
      <code>&$installer</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمى بعد أن قام المثبت بتحديث معلومات إصدار النظام ولكن قبل أن يتم إرجاع النجاح/الفشل في <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>إجراءات المشكلة:&lt;unk> الاشتراك مطلوب</code>
    </td>
    
    <td>
      <code>&$journal</code>, <code>&$issue</code>, <code>&$result</code>
    </td>
    
    <td>
      الاتصال به بعد أن حدد OJS ما إذا كان الاشتراك مطلوبا لمشاهدة <code>&$issue</code> في <code>&$journal</code> ولكن قبل إعادة القيمة الصحيحة/<unk> الخاطئة <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات::&lt;unk> مشترك</code>
    </td>
    
    <td>
      <code>&$journal</code>, <code>&$result</code>
    </td>
    
    <td>
      الاتصال بعد أن حدد OJS ما إذا كان المستخدم الحالي مشترك في <code>&$journal</code>، قبل إعادة القيمة الصحيحة/<unk> الخاطئة <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات::&lt;unk> مشترك</code>
    </td>
    
    <td>
      <code>&$journal</code>, <code>&$result</code>
    </td>
    
    <td>
      الاتصال بعد أن حدد OJS ما إذا كان المستخدم الحالي يأتي من نطاق مشترك في <code>&$journal</code>، قبل إعادة القيمة الصحيحة/<unk> الخاطئة <code>&$result</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>IssueDAO::&lt;unk> _returnIssueFromRow</code>
    </td>
    
    <td>
      <code>&amp;$issue</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>IssueDAO</code> يبني <code>مشكلة</code> (<code>&$issue</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة المسألة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>IssueDAO::&lt;unk> _returPublishedIssueFromRow</code>
    </td>
    
    <td>
      <code>&$issue</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>IssueDAO</code> يبني <code>مشكلة منشورة</code> (<code>&$issue</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال العدد المنشور إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>اليومية::&lt;unk> _returnJournalFromRow</code>
    </td>
    
    <td>
      <code>&$journal</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>JournalDAO</code> يبني <code>Journal</code> (<code>&$journal</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن تعاد الصحيفة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم DAO::&lt;unk> _returnSectionFromRow</code>
    </td>
    
    <td>
      <code>&$section</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>قسم DAO</code> يبني <code>قسم</code> (<code>&$section</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة القسم إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>البريد الإلكتروني TemplateDAO::&lt;unk> _returnBaseEmailTemplateFromRow</code>
    </td>
    
    <td>
      <code>&$emailTemplate</code>, <code>&$row</code>
    </td>
    
    <td>
      الاتصال بعد <code>البريد الإلكتروني TemplateDAO</code> يبني <code>BaseEmailTemplate</code> (<code>&$emailTemplate</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل تمرير قالب البريد الإلكتروني الأساسي إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>البريد الإلكتروني TemplateDAO::&lt;unk> _returnLocaleEmailTemplateFromRow</code>
    </td>
    
    <td>
      <code>&$emailTemplate</code>, <code>&$row</code>
    </td>
    
    <td>
      الاتصال بعد <code>البريد الإلكتروني TemplateDAO</code> يبني <code>مترجما محليا</code> (<code>&$emailTemplate</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يتم تمرير قالب البريد الإلكتروني المترجم إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>البريد الإلكتروني TemplateDAO::&lt;unk> _returEmailTemplateFromRow</code>
    </td>
    
    <td>
      <code>&$emailTemplate</code>, <code>&$row</code>
    </td>
    
    <td>
      الاتصال بعد <code>البريد الإلكتروني TemplateDAO</code> يبني <code>البريد الإلكتروني قالب</code> (<code>&$emailTemplate</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يتم إعادة قالب البريد الإلكتروني إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>البريد الإلكتروني:&lt;unk> إرسال</code>
    </td>
    
    <td>
      <code>&$mail</code>، <code>&$recipients</code>، <code>&$subject</code>، <code>&$mail</code>الجسم، <code>&$headers</code>، <code>&$additionalParameters</code>
    </td>
    
    <td>
      تم الاتصال مباشرة قبل إرسال بريد إلكتروني مع المعلمات المحددة. إذا كان رد الاتصال هذا هو للتعامل مع إرسال البريد الإلكتروني بنفسه، فيجب أن يعود رد الاتصال <code>true</code> وسيتم تخطي وظيفة إرسال OJS.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>RTDAO::&lt;unk> _returJournalRTFromRow</code>
    </td>
    
    <td>
      <code>&$rt</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>RTDAO</code> يبني أدوات القراءة <code>RT</code> (<code>&$rt</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال عنصر أدوات القراءة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>RTDAO::&lt;unk> _retursionFromRow</code>
    </td>
    
    <td>
      <code>&$version</code>, <code>&$row</code>
    </td>
    
    <td>
      الاتصال بعد <code>RTDAO</code> يبني أدوات القراءة <code>الإصدار</code> (<code>&$version</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يتم تمرير كائن إصدار أدوات القراءة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>RTDAO::​_returnSearchFromRow</code>
    </td>
    
    <td>
      <code>&$search</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>RTDAO</code> يبني أدوات القراءة <code>البحث</code> (<code>&$search</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يعاد كائن البحث عن أدوات القراءة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>RTDAO:&lt;unk> _returtextFromRow</code>
    </td>
    
    <td>
      <code>&$context</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>RTDAO</code> يبني أدوات القراءة <code>السياق</code> (<code>&$context</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يعاد كائن سياق أدوات القراءة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>AccessKeyDAO::​_returnAccessKeyFromRow</code>
    </td>
    
    <td>
      <code>&$accessKey</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد الوصول إلى كيداو يبني كائن <code>الوصول</code> (<code>&$accessKey</code>) من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال مفتاح الوصول إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>RoleDAO::&lt;unk> _returleFromRow</code>
    </td>
    
    <td>
      <code>&$role</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>RoleDAO</code> يبني <code>دور</code> (<code>&$role</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يعاد الدور إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>SiteDAO::​_returnSiteFromRow</code>
    </td>
    
    <td>
      <code>&$site</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>SiteDAO</code> يبني <code>موقع</code> (<code>&$site</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يعاد الموقع إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>VersionDAO::&lt;unk> _returnVersionFromRow</code>
    </td>
    
    <td>
      <code>&$version</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>VersionDAO</code> يبني <code>نسخة</code> (<code>&$version</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الإصدار إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>إجراءات التصريح:&lt;unk> حذف المادة ملف</code>
    </td>
    
    <td>
      <code>&$articleFile</code>, <code>&$authorRevisions</code>
    </td>
    
    <td>
      يُسمى قبل حذف OJS ملف مقالة المؤلف <code>&$articleFile</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> uploadRevisedversion</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل رفع OJS نسخة منقحة من <code>&$authorSubmission</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> اكتمل تحرير النسخة</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>, <code>&$email</code>
    </td>
    
    <td>
      الاتصال عندما يكمل المؤلف خطوة تحرير النسخ قبل أن يرسل OJS البريد الإلكتروني <code>&$email</code>، إذا تم تفعيله، ويعلّم خطوة تحرير النسخ كما اكتمل.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> copyeditUnderway</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>
    </td>
    
    <td>
      يُسمَح به عندما يشير المؤلف إلى أن خطوة تحرير النسخ الخاصة به جارية، قبل أن يرفع OJS علامة على التاريخ الجاري.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> تحميل نسخة</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>, <code>&$copyEditStage</code>
    </td>
    
    <td>
      يُسمى عندما يرفع المؤلف ملفا لـ <code>&$authorSubmission</code> على <code>&$copyEditStage</code> قبل أن يقبل OJS تحميل الملف.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> viewLayoutComments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب المؤلف تعليقات تخطيط المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات:&lt;unk> بعد تخطيط التعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول الكاتب نشر تعليق تخطيط على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> viewitorDecisionments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب المؤلف تعليقات قرار المحرر على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> البريد الإلكتروني تحرير تعليق</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>, <code>&$email</code>
    </td>
    
    <td>
      يُسمى قبل أن يرسل OJS تعليقات قرار المحرر للمقال <code>&$authorSubmission</code> في رسالة البريد الإلكتروني <code>&$email</code>. يجب استخدام هذا الرابط فقط على OJS &gt; 2.1.0-1.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> viewcopyeditcomments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمى عندما يطلب المؤلف تعليقات تحرير النسخة للمقال <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات:&lt;unk> تعليق postCopyeditment</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول المؤلف نشر تعليق تحرير نسخ على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المصادقة على الإجراءات:&lt;unk> المشاهدة</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب المؤلف تعليقات التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات:&lt;unk> تعليق التدقيق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمَح به المؤلف عندما يحاول نشر تعليق التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات:&lt;unk> تنزيل ملف AuthorFile</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$fileId</code>, <code>&$revision</code>, <code>&$canDownload</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمَح به عندما يرغب المؤلف في تحميل ملف مقالة (<code>&$article</code>، <code>&$fileId</code>، <code>&$revision</code>بعد أن يقرر مكتب العدل والمساواة ما إذا كان المؤلف لديه حق الوصول إلى هذا الملف (علم منطقي قابل للتعديل <code>&$canDownload</code>) ولكن قبل أن يبدأ التنزيل نفسه. إذا كان المسجل الرابط يرغب في تجاوز سلوك التحميل الافتراضي لـ OJS، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مقدم العرض:&lt;unk> _returnAuthorSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>AuthorSubmissionDAO</code> يبني <code>AuthorSubmission</code> (<code>&$authorSubmission</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة إرسال المؤلف إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات::&lt;unk> بيانات التعريف</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$role</code>
    </td>
    
    <td>
      يُسمى عندما يرغب مستخدم في الدور المعطى (<code>&$role</code>) في عرض البيانات الوصفية للمقال المعين (<code>&$article</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثيل، وعرض استمارة البيانات الوصفية العادية، يجب أن يعود <code>true</code> من وظيفة رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات:&lt;unk> حفظ البيانات الوصفية</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      موجه قبل أن يقوم OJS بتحديث البيانات الوصفية للمقال المحدد <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من أداء التحديث، فيجب أن يعيد <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات::&lt;unk> تعليمات</code>
    </td>
    
    <td>
      <code>&$type</code>, <code>&$allowed</code>
    </td>
    
    <td>
      متصل قبل عرض OJS التعليمات من النوع المطلوب <code>&$type</code> (<code>نسخة</code>, <code>تخطيط</code>أو <code>إثبات</code>)؛ الأنواع المسموح بها مدرجة في <code>&$allowed</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من عرض التعليمات، فيجب أن يعيد <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات::&lt;unk> تعديل التعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$comment</code>
    </td>
    
    <td>
      يُسمى قبل مثيلات OJS ويعرض نموذج تحرير التعليق الخاص بالمقالة المعينة (<code>&$article</code>) ويعلق (<code>&$comment</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من القيام بذلك، فيجب أن يعيد <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراء::&lt;unk> حفظ التعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$comment</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      الاتصال عندما يحاول المستخدم حفظ تعليق (<code>&$comment</code>) على المقالة (<code>&$article</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من حفظ التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الإجراءات::&lt;unk> حذف التعليق</code>
    </td>
    
    <td>
      <code>&$comment</code>
    </td>
    
    <td>
      الطلب قبل أن يحذف OJS التعليق المقدم. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من حذف التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>copyAssignmentDAO::&lt;unk> _returcopyAssignmentFromRow</code>
    </td>
    
    <td>
      <code>&$copyAssignment</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>copyAssignmentDAO</code> يقوم ببناء <code>CopyAssignment</code> (<code>&$copyAssignment</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل نقل مهمة تحرير النسخ إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ::&lt;unk> اكتمال النسخ</code>
    </td>
    
    <td>
      <code>&$copyeditorSubmission</code>, <code>&$editAssignments</code>, <code>&$author</code>, <code>&$email</code>
    </td>
    
    <td>
      يتم الاتصال به قبل أن يرسل OJS <code>COPYEDIT_COMPLETE</code> البريد الإلكتروني (إذا تم تفعيله) ويعلّم مرحلة تحرير النسخة الأولية لمحرّر النسخة كما اكتمل.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ:&lt;unk> اكتمال النسخة النهائية</code>
    </td>
    
    <td>
      <code>&$copyeditorSubmission</code>, <code>&$editAssignments</code>, <code>&$email</code>
    </td>
    
    <td>
      تقبل قبل أن يرسل OJS <code>COPYEDIT_FINAL_COMPLETE</code> البريد الإلكتروني (إذا تم تفعيله) ويعلِم مرحلة تحرير النسخة النهائية لمحرّر النسخة كما اكتمل.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ:&lt;unk> copyeditUnderway</code>
    </td>
    
    <td>
      <code>&$copyeditorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل OJS مرحلة تحرير النسخ من أجل التقديم المعطى (<code>&$copyeditorSubmission</code>) كما هو قيد التنفيذ. إذا كان صاحب تسجيل الرابط يرغب في منع OJS من أداء هذا العلم وإدخال السجل المرتبط به، يجب أن يعود <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ:&lt;unk> uploadCopyeditVersion</code>
    </td>
    
    <td>
      <code>&$copyeditorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل رفع OJS نسخة منقحة من <code>&$copyeditorSubmission</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ::&lt;unk> viewLayoutComments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمى عندما يطلب محرر النسخ تعليقات تخطيط المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ:&lt;unk> ما بعد تخطيط التعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      الاتصال عندما يحاول محرر النسخ نشر تعليق تخطيط على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ::&lt;unk> viewcopyeditcomments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب محرر النسخ تحرير تعليقات على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ:&lt;unk> تعليق البريدي</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول محرر النسخ نشر تعليق تحرير نسخ على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال. يجب استخدام هذا الرابط فقط مع OJS &gt; 2.1.0-1.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النشر:&lt;unk> downloadCopyeditorFile</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$fileId</code>, <code>&$revision</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمى عندما يرغب محرر النسخ في تحميل ملف مقالة (<code>&$article</code>، <code>&$fileId</code>، <code>&$revision</code>بعد أن حدد OJS ما إذا كان محرر النسخ له حق الوصول إلى هذا الملف (علم منطقي قابل للتعديل <code>&$canDownload</code>) ولكن قبل بدء التنزيل نفسه. إذا كان المسجل الرابط يرغب في تجاوز سلوك التحميل الافتراضي لـ OJS، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال. يجب استخدام هذا الرابط فقط مع OJS &gt; 2.1.0-1.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير النسخ:&lt;unk> _returnCopyitorSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$copyeditorSubmission</code>, <code>&$row</code>
    </td>
    
    <td>
      يُسمى بعد <code>تحرير الطبع والنشر</code> يبني <code>تقديم تحرير النشر</code> (<code>&$copyeditorSubmission</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة إرسال محرر النسخ إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>EditAssignmentsDAO::​_returnEditAssignmentFromRow</code>
    </td>
    
    <td>
      <code>&$editAssignment</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>EditAssignmentsDAO</code> يبني <code>EditAssignment</code> (<code>&$editAssignment</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل تحرير المهمة يتم إعادتها إلى وظيفة المكالمة. يجب استخدام هذا الرابط فقط مع OJS &gt; 2.1.0-1.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>محرر التحرير:&lt;unk> المحرر</code>
    </td>
    
    <td>
      <code>&$editorSubmission</code>, <code>&$sectionEditor</code>, <code>&$isEditor</code>, <code>&$email</code>
    </td>
    
    <td>
      يُسمى قبل أن يقوم OJS بتعيين المحرر المحدد أو محرر القسم (<code>&$sectionEditor</code>) إلى المقالة (<code>&$editorSubmission</code>) ويرسل (إذا تم تفعيل) البريد الإلكتروني المتوفر <code>&$email</code>. علامة <code>&$sectionEditor</code> عندما تكون صحيحة، تشير إلى أن المستخدم الذي يتم تعيينه هو محرر، وليس محرر قسم. (لم يكن هذا العلم موجودا قبل OJS 2.2 )
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SubmissionDAO::&lt;unk> _returitorSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$editorSubmission</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>محرر التسليم</code> يبني <code>مقدمة التحرير</code> (<code>&$editorSubmission</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة إرسال المحرر إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>LayoutAssignmentDAO::&lt;unk> _returnLayoutAssignmentFromRow</code>
    </td>
    
    <td>
      <code>&$layoutAssignment</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>LayoutAssignmentDAO</code> يبني <code>LayoutAsassignment</code> (<code>&$layoutAssignment</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة تعيين التخطيط إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> حذف:Galley</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$galley</code>
    </td>
    
    <td>
      الدعوة قبل أن يحذف OJS الوادي المحدد (<code>&$galley</code>) للمقال (<code>&$article</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من حذف الوادي، فيجب أن يعود <code>true</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> deleteSuppFile</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$suppFile</code>
    </td>
    
    <td>
      يُسمى قبل حذف OJS الملف التكميلي المحدد (<code>&$suppFile</code>) للمقال (<code>&$article</code>). إذا كان المسجل الرابط يرغب في منع OJS من حذف الملف التكميلي، فيجب أن يعود <code>true</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> completeLayoutEditing</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$layoutAssignment</code>, <code>&$editAssignments</code>, <code>&$email</code>
    </td>
    
    <td>
      يُسمى قبل أن يقوم OJS برسم مهمة تحرير التخطيط (<code>&$layoutAssignment</code>) للمقال (<code>&$submission</code>) ويرسل (إذا تم تفعيل) البريد الإلكتروني المتوفر <code>&$email</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> viewLayoutComments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمى عندما يطلب محرر التخطيط تعليقات تخطيط المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> postتخطيط تعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول محرر التخطيط نشر تعليق تخطيط على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> view Proofreadments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب محرر التخطيط تعليقات التدقيق للمقال <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> تعليق تدقيق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول محرر التخطيط نشر تعليق التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>محرر تخطيط::&lt;unk> تنزيل الملف</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$fileId</code>, <code>&$revision</code>, <code>&$canDownload</code>, <code>&$result</code>
    </td>
    
    <td>
      متصل عندما يرغب محرر التخطيط في تحميل ملف مقالة (<code>&$article</code>، <code>&$fileId</code>، <code>&$revision</code>بعد أن حدد OJS ما إذا كان محرر التخطيط لديه حق الوصول إلى هذا الملف (علم منطقي قابل للتعديل <code>&$canDownload</code>) ولكن قبل بدء التنزيل نفسه. إذا كان المسجل الرابط يرغب في تجاوز سلوك التحميل الافتراضي لـ OJS، يجب أن ينجح في تمرير منفذ إلى <code>&$result</code> وأن يعود <code>صحيح</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تخطيط المحرر:&lt;unk> _returoutitorSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>LayoutitorSubmissionDAO</code> يبني <code>طلب تحرير تخطيط</code> (<code>&$submission</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة تقديم الطلب إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofAssignmentDAO::​_returnProofAssignmentFromRow</code>
    </td>
    
    <td>
      <code>&$proofAssignment</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>ProofAssignmentDAO</code> يبني <code>ProofAssignment</code> (<code>&$proofAssignment</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة تصحيح التجارب المطبعية إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderAction::&lt;unk> selectProofreader</code>
    </td>
    
    <td>
      <code>&$userId</code>, <code>&$article</code>, <code>&$proofAssignment</code>
    </td>
    
    <td>
      يُسمى قبل أن يحدد OJS المستخدم الذي تم توريده (<code>&$userId</code>) كمصحح للمقال (<code>&$article</code>) مع مهمة الإثبات المحددة (<code>&$proofAssignment</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من أداء إجراءاته المعتادة، فيجب أن يعيد <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>التدقيق الإجرائي:&lt;unk> قائمة الانتظار</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$proofAssignment</code>
    </td>
    
    <td>
      يُسمَى عندما يقوم المدقّق بالواجب المعين (<code>&$proofAssignment</code>) بإنتظار المقالة المورّدة للجدولة (<code>&$article</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من أداء إجراءاته المعتادة، فيجب أن يعيد <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderAction::&lt;unk> proofreadEmail</code>
    </td>
    
    <td>
      <code>&$proofAssignment</code>, <code>&$email</code>, <code>&$mail</code>Type
    </td>
    
    <td>
      Called before OJS sends a proofreader email of the specified <code>&$mail</code>Type (e.g. <code>PROOFREAD_LAYOUT_COMPLETE</code>) and flags the appropriate dates given the supplied <code>&$proofAssignment</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderAction:&lt;unk> authorProofreadingUnderway</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$proofAssignment</code>
    </td>
    
    <td>
      يُسمى قبل OJS مهمة التدقيق المطبعي (<code>&$proofAssignment</code>) كقيد الإعداد للمقال <code>&$submission</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من وضع علامة على الواجب كقيد التنفيذ، فيجب أن يعود <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderAction::&lt;unk> proofreaderProofreadingUnderway</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$proofAssignment</code>
    </td>
    
    <td>
      يُسمى قبل OJS مهمة التدقيق المطبعي (<code>&$proofAssignment</code>) كقيد الإعداد للمقال <code>&$submission</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من وضع علامة على الواجب كقيد التنفيذ، فيجب أن يعود <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderAction:&lt;unk> layoutEditorProofreadingUnderway</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$proofAssignment</code>
    </td>
    
    <td>
      يُسمى قبل OJS مهمة التدقيق المطبعي لمحرر التخطيط (<code>&$proofAssignment</code>) كقيد الإعداد للمقال <code>&$submission</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من وضع علامة على الواجب كقيد التنفيذ، فيجب أن يعود <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderAction::&lt;unk> تنزيل ProofreaderFile</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$fileId</code>, <code>&$revision</code>, <code>&$canDownload</code>, <code>&$result</code>
    </td>
    
    <td>
      يُسمى عندما يرغب المدقّق في تنزيل ملف مقالة (<code>&$article</code>، <code>&$fileId</code>، <code>&$revision</code>بعد أن حدد OJS ما إذا كان المدقق لديه حق الوصول إلى هذا الملف (علم منطقي قابل للتعديل <code>&$canDownload</code>) ولكن قبل بدء التحميل نفسه. إذا كان المسجل الرابط يرغب في تجاوز سلوك التحميل الافتراضي لـ OJS، يجب أن ينجح في تمرير منفذ إلى <code>&$result</code> وأن يعود <code>صحيح</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تعليقات ProofreaderAction::&lt;unk> المشاهدة</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب المدقق تعليقات التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>التعليق على التدقيق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول المدقّق نشر تعليق التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>التدقيق الإجرائي:&lt;unk> viewLayoutComments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب المدقق تعليقات تخطيط المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>التدقيق الإجرائي:&lt;unk> ما بعد تخطيط التعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      متصل عندما يحاول المدقّق نشر تعليق تخطيط على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ProofreaderSubmissionDAO::&lt;unk> _returnProofreaderSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>ProofreaderSubmissionDAO</code> يبني <code>ProofreaderSubmission</code> (<code>&$submission</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة تقديم الطلب إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ReviewAssignmentDAO::&lt;unk> _return ReviewAssignmentFromRow</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>ReviewAssignmentDAO</code> يبني <code>إعادة تعيين</code> (<code>&$reviewAssignment</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل نقل مهمة المراجعة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات:&lt;unk> تأكيد</code>
    </td>
    
    <td>
      <code>&$reviewerSubmission</code>, <code>&$email</code>, <code>&$decline</code>
    </td>
    
    <td>
      يُسمى قبل تسجيل OJS حالة المستعرض المقبولة/<unk> المرفوضة (<code>&$decline</code>) على <code>&$reviewAssignment</code> و يرسل محرر البريد الإلكتروني <code>&$email</code> (إذا تم تفعيله).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات:&lt;unk> توصية</code>
    </td>
    
    <td>
      <code>&$reviewerSubmission</code>, <code>&$email</code>, <code>&$recommendation</code>
    </td>
    
    <td>
      سُمح قبل أن يسجل OJS توصية المستعرض (<code>&$recommendation</code>) على <code>&$reviewAssignment</code> المورد، ويرسل المحرر البريد الإلكتروني <code>&$email</code> (إذا تم تفعيله).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات:&lt;unk> تحميل مراجعة الملف</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>
    </td>
    
    <td>
      تمت الموافقة قبل أن يقوم OJS بتحديث ملف المراجعة الخاص بـ <code>&$reviewAssignment</code> مع الملف الذي تم تحميله.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات:&lt;unk> حذف المراجعة</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$fileId</code>, <code>&$revision</code>
    </td>
    
    <td>
      الطلب قبل أن يحذف OJS ملف المستعرض الذي تم توفيره (<code>&$reviewAssignment</code>، <code>&$fileId</code>، <code>&$version</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من الحذف، فيجب أن يعود <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات::&lt;unk> مراجعة التعليقات</code>
    </td>
    
    <td>
      <code>&$user</code>, <code>&$article</code>, <code>&$reviewId</code>
    </td>
    
    <td>
      سُمح قبل أن يعرض OJS تعليقات مراجعة النظراء للمراجع (<code>&$user</code>) للمقال المعين (<code>&$article</code>) ومراجعة المعرف (<code>&$reviewId</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من عرض المراجعات، فيجب أن يعود <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات:&lt;unk> تعليق المراجعة</code>
    </td>
    
    <td>
      <code>&$user</code>, <code>&$article</code>, <code>&$reviewId</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      سُمي قبل تسجيل تعليق جديد على معرف المراجعة المعطى (<code>&$reviewId</code>) من قبل المُراجع (<code>&$user</code>) على مقالة (<code>&$article</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق، فيجب أن يعود <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>استعراض الإجراءات:&lt;unk> تنزيلات ReviewerFile</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$fileId</code>, <code>&$revision</code>, <code>&$canDownload</code>, <code>&$result</code>
    </td>
    
    <td>
      متصل عندما يرغب المُراجع في تنزيل ملف مقالة (<code>&$article</code>، <code>&$fileId</code>، <code>&$revision</code>بعد أن حدد OJS ما إذا كان لدى المستعرض حق الوصول إلى هذا الملف (العلم المنطقي القابل للتعديل <code>&$canDownload</code>) ولكن قبل بدء التنزيل نفسه. إذا كان المسجل الرابط يرغب في تجاوز سلوك التحميل الافتراضي لـ OJS، يجب أن ينجح في تمرير منفذ إلى <code>&$result</code> وأن يعود <code>صحيح</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مراجعة الإجراءات:&lt;unk> تعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$comment</code>, <code>&$reviewId</code>
    </td>
    
    <td>
      يُسمى قبل مثيلات OJS ويعرض نموذج تحرير التعليق للمستعرض لمقال معين (<code>&$article</code>) ويعلق (<code>&$comment</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من القيام بذلك، فيجب أن يعيد <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ReviewerSubmissionDAO::&lt;unk> _returnReviewerSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$reviewerSubmission</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>ReviewerSubmissionDAO</code> يبني <code>استعراض التقديم</code> (<code>&$reviewerSubmission</code>DAO) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل نقل مهمة المراجعة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تفويض الإجراءات::&lt;unk> designateReviewversion</code>
    </td>
    
    <td>
      <code>&$authorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل أن يحدد OJS الملف الأصلي كإصدار مراجعة للمقال المحدد (<code>&$authorSubmission</code>). لمنع OJS من أداء هذه المهمة، يجب أن يعود مسجل الرابط <code>الحقيقي</code> من وظيفة رد الاتصال. قبل OJS 2.1.1، كان هذا الرابط يسمى <code>قسم التحرير:&lt;unk> designateReviewVersion</code> و أخذ <code>قسم تحرير التقديم</code> كمعلوم.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> قسم التغيير</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$sectionId</code>
    </td>
    
    <td>
      يُسمى قبل أن يقوم OJS بتغيير قسم الإرسال (<code>&$sectionEditorSubmission</code>) إلى القسم مع معرف القسم المعين (<code>&$sectionId</code>). لمنع OJS من أداء هذه المهمة، يجب أن يعود مسجل الرابط <code>الحقيقي</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> قرار تسجيل</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$editorDecision</code>
    </td>
    
    <td>
      الطلب قبل تسجيل OJS قرار (<code>&$editorDecision</code>) لتقديم طلب (<code>&$sectionEditorSubmission</code>). لمنع OJS من أداء هذه المهمة، يجب أن يعود مسجل الرابط <code>الحقيقي</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير:&lt;unk> AdaddReviewer</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$reviewerId</code>
    </td>
    
    <td>
      سُمح به قبل أن ينشئ OJS مهمة مراجعة جديدة للمستعرض المحدد (<code>&$reviewerId</code>) عند تقديم طلب (<code>&$sectionEditorSubmission</code>). لمنع OJS من أداء هذه المهمة، يجب أن يعود مسجل الرابط <code>الحقيقي</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> مراجعة</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$reviewAssignment</code>
    </td>
    
    <td>
      يُدعى قبل أن يمسح OJS مراجعة (<code>&$reviewAssignment</code>) على تقديم (<code>&$sectionEditorSubmission</code>). لمنع OJS من أداء هذه المهمة، يجب أن يعود مسجل الرابط <code>الحقيقي</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> إخطار المستعرض</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$reviewAssignment</code>, <code>&$email</code>
    </td>
    
    <td>
      يُسمى قبل أن يرفع OJS إشعار المستعرض مع مراجعة معلقة (<code>&$reviewAssignment</code>) على طلب مقدم (<code>&$sectionEditorSubmission</code>)، إرسال طلب المستعرض المرتبط بالبريد الإلكتروني <code>&$email</code> (إذا تم تفعيل).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> إلغاء المراجعة</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$reviewAssignment</code>, <code>&$email</code>
    </td>
    
    <td>
      يُسمى قبل أن يلغي OJS مراجعة (<code>&$reviewAssignment</code>) عند تقديم طلب (<code>&$sectionEditorSubmission</code>)، إرسال البريد الإلكتروني للإلغاء المرتبط به (<code>&$email</code>) إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم::&lt;unk> تذكير المستعرض</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$reviewAssignment</code>, <code>&$email</code>
    </td>
    
    <td>
      سُمح به قبل أن يذكّر OJS أحد المراجعين بمهمة مراجعة معلقة (<code>&$reviewAssignment</code>) عند تقديم طلب (<code>&$sectionEditorSubmission</code>)، إرسال رسالة تذكير مرفقة (<code>&$email</code>).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> شكر المستعرض</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$reviewAssignment</code>, <code>&$email</code>
    </td>
    
    <td>
      استدعاء قبل OJS يشكر المستعرض لإكمال مهمة المراجعة الخاصة به (<code>&$reviewAssignment</code>) عند تقديم طلب (<code>&$sectionEditorSubmission</code>)، أيضا إرسال البريد الإلكتروني <code>&$email</code> (إذا تم تفعيلها).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> تقييم المراجعة</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$reviewer</code>, <code>&$quality</code>
    </td>
    
    <td>
      سُمي قبل أن يسجل OJS تقييم جودة (<code>&$quality</code>) للمستعرض (<code>&$reviewer</code>) في مهمة مراجعة (<code>&$reviewAssignment</code>). لمنع OJS من تسجيل التقييم، يجب على مسجل الرابط أن يعود <code>true</code> من رد اتصاله.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> makeReviewerFileViewable</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$articleFile</code>, <code>&$viewable</code>
    </td>
    
    <td>
      يُسمى قبل أن يسجل OJS إعداد جديد للرؤية (<code>&$viewable</code>لملف مراجع (<code>&$articleFile</code>) ينتمي إلى مهمة مراجعة (<code>&$reviewAssignment</code>). لمنع OJS من تسجيل الإعداد الجديد، يجب أن يعود مسجل الرابط <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> setDueDate</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$reviewer</code>, <code>&$dueDate</code>, <code>&$numWeeks</code>
    </td>
    
    <td>
      استدعي قبل أن يحدد OJS تاريخ الاستحقاق على المستعرض (<code>&$reviewer</code>) مهمة المراجعة (<code>&$reviewAssignment</code>) إلى <code>&$dueDate</code>. لمنع OJS من تحديد تاريخ الاستحقاق، يجب على مسجل الرابط أن يعود <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تقديم غير مناسب</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$author</code>, <code>&$email</code>
    </td>
    
    <td>
      طلب قبل أن يسجل OJS مؤلف (<code>&$author</code>) مقدم (<code>&$sectionEditorSubmission</code>) باعتباره غير مناسب، إرسال <code>&$email</code> (إذا تم تفعيل).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> notifyAuthor</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$author</code>, <code>&$email</code>
    </td>
    
    <td>
      تم استدعاؤه قبل أن يرسل OJS رسالة إشعار للمؤلف (<code>&$email</code>) إلى مؤلف (<code>&$author</code>) فيما يتعلق بتقديم طلب (<code>&$sectionEditorSubmission</code>).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> setReviewerRecommendation</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$reviewer</code>, <code>&$recommendation</code>, <code>&$acceptOption</code>
    </td>
    
    <td>
      تم تسجيل توصية المستعرض (<code>&$recommendation</code>) في مهمة مراجعة (<code>&$reviewAssignment</code>) للمراجع <code>&$reviewer</code>. لمنع تسجيل التوصية، يجب على مسجل الرابط أن يعيد <code>true</code> من رد اتصاله بالربط.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> setcopyeditFile</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$fileId</code>, <code>&$revision</code>
    </td>
    
    <td>
      سُمح قبل أن يقوم OJS بتعيين ملف محرر النسخ لتقديم <code>&$sectionEditorSubmission</code> إلى <code>&$fileId</code> مع مراجعة <code>&$revision</code>. لمنع حدوث هذا التغيير، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> إعادة تقديم الملف</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$fileId</code>, <code>&$revision</code>
    </td>
    
    <td>
      يُسمى قبل أن يعيد OJS إرسال ملف (<code>&$fileId</code> و <code>&$revision</code>) ينتمي إلى التقديم <code>&$sectionEditorSubmission</code> للمراجعة. لمنع حدوث هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> selectCopyitor</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$copyeditorId</code>
    </td>
    
    <td>
      سُمح به قبل أن يحدد OJS المستخدم بالمعرف <code>&$copyeditorId</code> كمحرر لتسليم <code>&$sectionEditorSubmission</code>. لمنع حدوث ذلك، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> notifycopyitor</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$copyeditor</code>, <code>&$email</code>
    </td>
    
    <td>
      مقبول قبل أن يقوم OJS بإعلام محرر النسخ <code>&$copyeditor</code> حول مهمة تحرير النسخ الخاصة بهم لتقديمها <code>&$sectionEditorSubmission</code>، إرسال <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> initiateCopyedit</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      مطلوب قبل وضع علامة على بداية مرحلة تحرير تحرير المحرر عند تقديم <code>&$sectionEditorSubmission</code>. لمنع حدوث ذلك، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> شكر نسخة محرر</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$copyeditor</code>, <code>&$email</code>
    </td>
    
    <td>
      طلب قبل OJS شكرا محرر نسخ (<code>&$copyeditor</code>) لمساهمته في التقديم <code>&$sectionEditorSubmission</code>، إرسال البريد الإلكتروني <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> notifyAuthorcopyedit</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$author</code>, <code>&$email</code>
    </td>
    
    <td>
      سُمِح قبل علم OJS بإشعار مؤلف (<code>&$author</code>) بتعيينه تحرير النسخ في تقديم (<code>&$sectionEditorSubmission</code>)، إرسال البريد الإلكتروني <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> شكر نسخة محررة</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$author</code>, <code>&$email</code>
    </td>
    
    <td>
      سُمح قبل سجلات OJS بشكر مؤلف (<code>&$author</code>) لمساهمته في تحرير النسخ إلى <code>&$sectionEditorSubmission</code>، إرسال <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> notifyFinalcopyedit</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$copyeditor</code>, <code>&$email</code>
    </td>
    
    <td>
      سُمح قبل تسجيل OJS بإخطار محرر النسخ (<code>&$copyeditor</code>) بمرحلة التحرير النهائية لتقديمها <code>&$sectionEditorSubmission</code>، إرسال <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> thankFinalcopyedit</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$copyeditor</code>, <code>&$email</code>
    </td>
    
    <td>
      سُجلت قبل سجلات OJS التي شكر محرر نسخ (<code>&$copyeditor</code>) لمساهمته في تحرير الدورة النهائية لتقديمها <code>&$sectionEditorSubmission</code>، إرسال <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير الاصدار:&lt;unk> رفع المراجعة</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل تخزين OJS إصدار مراجعة جديد لتقديم <code>&$sectionEditorSubmission</code>. ولمنع مكتب العدل والمساواة من القيام بذلك، ينبغي لصاحب التسجيل أن يعود حقيقةً من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> رفع تحرير الإصدار</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل تخزين OJS إصدار تعديل جديد لتقديم <code>&$sectionEditorSubmission</code>. ولمنع مكتب العدل والمساواة من القيام بذلك، ينبغي لصاحب التسجيل أن يعود حقيقةً من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> uploadCopyeditVersion</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل أن يقوم OJS بتخزين نسخة جديدة من تحرير النسخ من أجل تقديم <code>&$sectionEditorSubmission</code>. ولمنع مكتب العدل والمساواة من القيام بذلك، ينبغي لصاحب التسجيل أن يعود حقيقةً من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> اكتمال تحرير</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      قبل أن يسجل OJS تاريخ الانتهاء من تحرير النسخ في تقديم (<code>&$sectionEditorSubmission</code>) تم تنفيذه للمحرر (عندما يكون استخدام محرر النسخ معطل). لمنع OJS من تسجيل هذا، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> اكتمال النسخة النهائية</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      قبل أن يسجل OJS تاريخ الانتهاء من مرحلة التحرير النهائية على تقديم (<code>&$sectionEditorSubmission</code>) التي تم تنفيذها للمحرر (عندما يكون استخدام محرري النسخ معطل). لمنع OJS من تسجيل هذا، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير:&lt;unk> أرشيف التقديم</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      الطلب قبل أن يقوم OJS بأرشيف رسالة (<code>&$sectionEditorSubmission</code>). إذا لم يتم تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> إعادة قائمة الانتظار</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>
    </td>
    
    <td>
      يُسمى قبل أن يستعيد OJS تقديما (<code>&$sectionEditorSubmission</code>) من الأرشيف إلى قائمة انتظار نشطة. إذا لم يتم تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تحديث القسم</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$sectionId</code>
    </td>
    
    <td>
      سُمح قبل أن ينقل OJS المقالة <code>&$submission</code> إلى القسم مع المعرف <code>&$sectionId</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> uploadLayoutVersion</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$layoutAssignment</code>
    </td>
    
    <td>
      يُسمى قبل تخزين OJS نسخة تخطيط جديدة من التقديم <code>&$submission</code> مع تعيين التخطيط المعين <code>&$layoutAssignment</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> assignLayoutitor</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$editorId</code>
    </td>
    
    <td>
      سُمح قبل أن يقوم OJS بتعيين محرر التخطيط مع معرف المستخدم <code>&$editorId</code> لتقديم <code>&$submission</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود صاحب تسجيل الإرتباط صحيحاً من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> notifyLayoutitor</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$layoutEditor</code>, <code>&$layoutAssignment</code>, <code>&$email</code>
    </td>
    
    <td>
      سُمي قبل أن يرفع OJS إشعاراً بمحرر التخطيط <code>&$layoutEditor</code> لتقديم <code>&$submission</code>، إرسال البريد الإلكتروني <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير SectionEditorAction::&lt;unk> thankLayoutitor</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$layoutEditor</code>, <code>&$layoutAssignment</code>, <code>&$email</code>
    </td>
    
    <td>
      سُجلت قبل سجلات OJS التي شكرت محرر التخطيط <code>&$layoutEditor</code> على عملهم في التقديم <code>&$submission</code>، إرسال البريد الإلكتروني <code>&$email</code> إذا تم تمكينه.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> حذف المادة الملف</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$fileId</code>, <code>&$revision</code>
    </td>
    
    <td>
      مطلوب قبل أن يحذف OJS صورة وادي مقالة (<code>&$fileId</code>، <code>&$revision</code>) لتقديم <code>&$submission</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود صاحب تسجيل الإرتباط صحيحاً من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> حذف صورة المادة</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$fileId</code>, <code>&$revision</code>
    </td>
    
    <td>
      تم الطلب قبل حذف صورة مقالة (<code>&$fileId</code>، <code>&$revision</code>) لتقديم <code>&$submission</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود صاحب تسجيل الإرتباط صحيحاً من رد المكالمة. (هذا الرابط متاح فقط على OJS 2.1.1 وما بعد).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير الإجراءات:&lt;unk> addSubmissionNote</code>
    </td>
    
    <td>
      <code>&$articleId</code>, <code>&$articleNote</code>
    </td>
    
    <td>
      سُمح به قبل أن يضيف OJS ملاحظة الإرسال (<code>&$articleNote</code>) إلى تقديم مع معرف المقال <code>&$articleId</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير الإجراءات:&lt;unk> إزالةveSubmissionNote</code>
    </td>
    
    <td>
      <code>&$articleId</code>, <code>&$noteId</code>, <code>&$fileId</code>
    </td>
    
    <td>
      الطلب قبل أن يزيل OJS الملاحظة المقدمة (<code>&$noteId</code>) وإذا كانت موجودة، الملف المرتبط (<code>&$fileId</code>) من الإرسال مع معرف المقال <code>&$articleId</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تحديث المذكرة</code>
    </td>
    
    <td>
      <code>&$articleId</code>, <code>&$articleNote</code>
    </td>
    
    <td>
      سُمح به قبل أن يحفظ OJS التغييرات المدخلة على مذكرة الإرسال على المقالة مع معرف <code>&$articleId</code>، تم بالفعل على الكائن <code>&$articleNote</code> ولكن لم يتم الالتزام بقاعدة البيانات. الملف المرفق الجديد، إذا تم تحميله، لم يتم تخزينه بعد. لمنع OJS من تخزين التغييرات، يجب على مسجل الرابط أن يعود <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> مسح AllSubmissionNotes</code>
    </td>
    
    <td>
      <code>&$articleId</code>
    </td>
    
    <td>
      يسمح قبل OJS بإزالة جميع ملاحظات التقديم، وإذا كانت موجودة، الملفات المرتبطة بها من الإرسال مع معرف المقالة <code>&$articleId</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير التعليقات::&lt;unk> viewPeerReviewments</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$reviewId</code>
    </td>
    
    <td>
      سُمح قبل أن يعرض OJS تعليقات مراجعة الأقران للمحرر أو محرر القسم الخاص بالمقالة المعينة (<code>&$article</code>) ومراجعة المعرف (<code>&$reviewId</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من عرض المراجعات، فيجب أن يعود <code>true</code> من رد المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تعليق المراجعة</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$reviewId</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      سُمي قبل تسجيل OJS تعليق جديد على معرف المراجعة المعطى (<code>&$reviewId</code>) من قبل المحرر أو محرر القسم على مقالة (<code>&$article</code>). إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق، فيجب أن يعود <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير التعليقات:&lt;unk> viewitorDecisionments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمى عندما يطلب المحرر أو محرر القسم تعليقات قرار المحرر على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير الإجراءات:&lt;unk> تعليق ما بعد التحرير</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      مطلوب قبل تسجيل OJS تعليق محرر جديد على التقديم <code>&$article</code>. لمنع OJS من القيام بهذا الإجراء، يجب أن يعود رد الاتصال إلى "صواب".
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> البريد الإلكتروني تحرير تعليق</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$send</code>
    </td>
    
    <td>
      يطلب من المؤلف قبل إرسال رسائل بريد إلكتروني إلى OJS التعليق على قرار المحرر على التقديم (<code>&$sectionEditorDecision</code>).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> أعمى indCcReviewsToReview,</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$reviewAssignments</code>, <code>&$email</code>
    </td>
    
    <td>
      تم الاتصال قبل أن يقوم OJS بإرسال الملاحظات (<code>&$reviewAssignments</code>البريد الإلكتروني (<code>&$email</code>) للمراجعين للمقال <code>&$article</code>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القطاع::&lt;unk> viewcopyeditcomments</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمى عندما يطلب المحرر أو محرر القسم تعليقات تحرير نسخ للمقال <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تعليق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول المحرر أو محرر القسم نشر تعليق تحرير نسخ على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم::&lt;unk> viewتخطيط التعليقات</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمى عندما يطلب محرر القسم أو محرر القسم تعليقات التخطيط للمقال <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تعليق ما بعد التخطيط</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول محرر القسم أو محرر القسم نشر تعليق تخطيط على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم::&lt;unk> المشاهدة التعليقات</code>
    </td>
    
    <td>
      <code>&$article</code>
    </td>
    
    <td>
      يُسمَح به عندما يطلب المحرر أو محرر القسم تعليقات التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من التمثال وعرض نموذج التعليق، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير القسم:&lt;unk> تعليق التدقيق</code>
    </td>
    
    <td>
      <code>&$article</code>, <code>&$emailComment</code>
    </td>
    
    <td>
      يُسمى عندما يحاول المحرر أو محرر القسم نشر تعليق التدقيق على المقالة <code>&$article</code>. إذا كان صاحب التسجيل الرابط يرغب في منع OJS من تسجيل التعليق المقدم، فيجب أن يعود <code>true</code> من وظيفة رد الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> تأكيد المراجعة</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$reviewer</code>, <code>&$accept</code>
    </td>
    
    <td>
      يُسمى قبل أن يسجل OJS قبول المحرر أو رفضه لتعيين مراجعة (<code>&$reviewAssignment</code>) نيابة عن مراجع (<code>&$reviewer</code>). لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته. قبل OJS 2.2، كان هذا الرابط يسمى <code>قسم تحرير الإجراءات::&lt;unk> acceptReviewForviewer</code> (بدون معلمة <code>$accept</code>).
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم التحرير::&lt;unk> تحميل استعراض المستعرض</code>
    </td>
    
    <td>
      <code>&$reviewAssignment</code>, <code>&$reviewer</code>
    </td>
    
    <td>
      يُسمى قبل خزن OJS تحميل مراجعة المحرر من أجل مهمة مراجعة (<code>&$reviewAssignment</code>) نيابة عن مراجع (<code>&$reviewer</code>). لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم تحرير SubmissionDAO::&lt;unk> _returSectionitorSubmissionFromRow</code>
    </td>
    
    <td>
      <code>&$sectionEditorSubmission</code>, <code>&$row</code>
    </td>
    
    <td>
      يُسمى بعد <code>قسم تحرير SubmissionDAO</code> يبني <code>قسم تقديم المحرر</code> (<code>&$sectionEditorSubmission</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة تقديم الطلب إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قسم تحرير التقديم DAO::&lt;unk> _returnReviewerUserFromRow</code>
    </td>
    
    <td>
      <code>&$user</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>قسم تحرير التقرير</code> يقوم بإنشاء <code>مستخدم</code> (<code>&$user</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة تقديم الطلب إلى وظيفة المكالمة. ولا يوصى باستخدام هذا الرابط لأنه يمكن إزالته في المستقبل.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>العملة:&lt;unk> _returcyFromRow</code>
    </td>
    
    <td>
      <code>&$currency</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>العملة</code> يبني <code>عملة</code> (<code>&$currency</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل تحويل العملة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الاشتراك DAO::&lt;unk> _returnSubscriptionFromRow</code>
    </td>
    
    <td>
      <code>&$subscription</code>, <code>&$row</code>
    </td>
    
    <td>
      الاتصال به بعد <code>الاشتراك</code> يبني <code>الاشتراك</code> (<code>&$subscription</code>) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة الإشتراك إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>الاشتراك TypeDAO::&lt;unk> _returnSubscriptionTypeFromRow</code>
    </td>
    
    <td>
      <code>&$subscription</code>النوع، <code>&$row</code>
    </td>
    
    <td>
      الاتصال به بعد <code>الاشتراك TypeDAO</code> يبني <code>نوع الاشتراك</code> (<code>&$subscription</code>نوع) عنصر من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل إعادة نوع الاشتراك إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مدير القالب:&lt;unk> عرض</code>
    </td>
    
    <td>
      <code>&$templateMgr</code>, <code>&$template</code>, <code>&$sendContentType</code>, <code>&$charset</code>
    </td>
    
    <td>
      يُسمى قبل مدير القالب (<code>&$templateMgr</code>) يرسل نوع المحتوى مع نوع المحتوى المحدد (<code>&$sendContentType</code>) ومجموعة الحروف (<code>&$charset</code>) ويعرض قالب (<code>&$template</code>). لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود مسجل الرابط <code>true</code> من رد مكالمته.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>المستخدم::&lt;unk> _returnUserFromRow</code>
    </td>
    
    <td>
      <code>&$user</code>, <code>&$row</code>
    </td>
    
    <td>
      الاتصال بعد <code>UserDAO</code> يقوم ببناء <code>مستخدم</code> (<code>&$user</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل أن يعاد المستخدم إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>مجموعة::&lt;unk> _returGroupFromRow</code>
    </td>
    
    <td>
      <code>&$group</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>GroupDAO</code> ينشئ <code>مجموعة</code> (<code>&$group</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال المجموعة إلى وظيفة المكالمة.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>GroupMembershipDAO::&lt;unk> _returerFromRow</code>
    </td>
    
    <td>
      <code>&$membership</code>, <code>&$row</code>
    </td>
    
    <td>
      يسمى بعد <code>GroupMembershipDAO</code> يبني <code>عضوية المجموعة</code> (<code>&$membership</code>) كائن من صف قاعدة البيانات (<code>&$row</code>)، ولكن قبل انتقال عضوية المجموعة إلى وظيفة الاتصال.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> عن::&lt;unk> فهرس::&lt;unk> أشخاص</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرصاص في قسم الأشخاص في صفحة حول الموضوع، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> عن::&lt;unk> فهرس::&lt;unk> السياسات</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرموز في قسم السياسات من صفحة حول الموضوع، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> عن::&lt;unk> فهرس::&lt;unk> التقديمات</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرموز في قسم التقديمات من صفحة حول الموضوع، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> عن::&lt;unk> فهرس::&lt;unk> اخرى</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرصاص في القسم الآخر من صفحة حول الموضوع، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> مشرف::&lt;unk> فهرس::&lt;unk> إدارة الموقع</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرموز في قسم إدارة الموقع في صفحة إدارة الموقع، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> مشرف::&lt;unk> فهرس::&lt;unk> مشرف الوظائف</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرصاص في قسم وظائف المدير في صفحة إدارة الموقع، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>القوالب::&lt;unk> محرر::&lt;unk> فهرس::&lt;unk> التقديمات</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرموز في قسم التقديمات في صفحة المحرر، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> محرر::&lt;unk> فهرس::&lt;unk> مشكلات</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية القائمة المقطوعة في قسم المشكلات في صفحة المحرر، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> المدير::&lt;unk> Index::&lt;unk> ManagementPages</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية القائمة النصية في قسم صفحات الإدارة في صفحة مدير اليومية، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> المدير::&lt;unk> فهرس::&lt;unk> المستخدمين</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية القائمة النصية في قسم المستخدمين في صفحة مدير المجلة، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> المدير::&lt;unk> فهرس::&lt;unk> أدوار</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة الرموز في قسم الأدوار في صفحة مدير اليومية، داخل العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> المستخدم::&lt;unk> Index::&lt;unk> الموقع</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      يُسمى بعد أن يتم عرض رابط إدارة الموقع (إذا كان ذلك منطبقاً) في منزل المستخدم، داخل علامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>قوالب::&lt;unk> المستخدم::&lt;unk> Index::&lt;unk> Journal</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      يُسمى في نهاية القائمة التي تعرض الأدوار لكل يومية في منزل المستخدم، ضمن علامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>القوالب::&lt;unk> المشرف::&lt;unk> فهرس::&lt;unk> حساب</code>
    </td>
    
    <td>
      <code>&$params</code>, <code>&$templateMgr</code>, <code>&$output</code>
    </td>
    
    <td>
      مسموح به في نهاية قائمة النشرات في قسم حسابي في منزل المستخدم، ضمن العلامة &lt;ul class="plain"&gt;...&lt;/ul&gt;
    </td>
  </tr>
  
  <tr>
    <td>
      <code>تحرير تخطيط::&lt;unk> حذف المادة ملف</code>
    </td>
    
    <td>
      <code>&$submission</code>, <code>&$fileId</code>, <code>&$revision</code>
    </td>
    
    <td>
      مطلوب قبل أن يحذف OJS صورة وادي مقالة (<code>&$fileId</code>، <code>&$revision</code>) لتقديم <code>&$submission</code>. لمنع OJS من تنفيذ هذا الإجراء، يجب أن يعود صاحب تسجيل الإرتباط صحيحاً من رد المكالمة. (هذا الرابط متاح فقط على OJS 2.1.1 وما بعد).
    </td>
  </tr>
</table>

