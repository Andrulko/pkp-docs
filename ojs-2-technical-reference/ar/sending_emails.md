# إرسال البريد الإلكتروني

يتم تخزين قوالب البريد الإلكتروني لكل لغة محلية في ملف XML يسمى `dbscripts/xml/data/locale/[localeName]/email_templates_data.xml`. كل بريد إلكتروني لديه معرف (يسمى email_key في ملف XML) مثل `SUBMISSION_ACK`. يستخدم هذا المعرف في رمز PHP لاسترداد قالب بريد إلكتروني معين، بما في ذلك نص الجسم والموضوع.

يسترجع الرمز التالي ويرسل البريد الإلكتروني `SUBMISSION_ACK` ، الذي يتم إرساله إلى المؤلفين على سبيل الإقرار عند إكمال التقديم. (هذه الكتلة تفترض أن معرف المقالة الحالي مخزن في `$articleId`.)

**مثال 3-1. مثال رمز لإرسال `SUBMISSION_ACK` بريد إلكتروني**

````
// جلب كائن المقالة باستخدام مقالة DAO.
$articleDao = &DAOregistry::getDAO('ArticleDAO');
$article = &$articleDao->getArticle($articleId);

/ قم بتحميل الفئة المطلوبة من قالب المادة
('البريد). rticleMailTemplate');

// استرداد قالب البريد الإلكتروني بالاسم.
$mail = &قالب مادة جديدة ($article، 'SUBMISSION_ACK')؛

إذا كان ($mail->مفعّل ()) {
// احصل على كائن المستخدم الحالي وقم بتعيينه كمستلم لهذه الرسالة.
$user = &طلب::getUser();
$mail->addipient($user->getEmail(),
    $user->getFullName());

// احصل على كائن المجلة الحالية.
$journal = &طلب::getJournal();

/ هذا القالب يحتوي على أسماء متغيرات النموذج {$variableName} الذي يحتاج إلى
// يجب استبداله بالقيم المناسبة. لاحظ أنه في حين أن بناء الجملة مماثل
// للصيغة المستخدمة من قبل قوالب Smarty فإن قوالب البريد الإلكتروني ليست قوالب Smarty . فقط
/ / استبدال المتغير المباشر مدعوم.
$mail->تعيين بارامس(المصفوفة(
    'authorName' => $user->getFullName(),
    'اسم المستخدم المؤلف' => $user->getUsername(),
    'editorialContactSignature' => $journal->getSetting('contactName').
        "\n" . $journal->getTitle(),
    'submissionUrl' => request:getPageUrl() . 
        '/author/submission/' . $article->getArticleId()
));

$mail->send();
}

````

