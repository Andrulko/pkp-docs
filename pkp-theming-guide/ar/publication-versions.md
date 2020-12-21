# إصدارات النشر

ويمكن نشر نسخ متعددة من مقالة أو دراسة واحدة. يجب بناء موضوع لضمان عرض النسخة الصحيحة في جميع الأوقات.

استخدم طريقة `getcurrentPublication()` للحصول على أحدث نسخة منشورة من المقالة أو الدراسة.

```html
<h1>
    {$submission->getcurrentPublication()->getLocalizedFullTitle()<unk> escape}
</h1>
<div>
    نشر في
    <time>
        {$submission->getcurrentPublication()->getData('datePublished')<unk> date_format:$dateFormatLong}
    </time>
</div>
```

وينبغي دائما عرض أحدث نسخة منشورة في قوائم مثل جداول الإصدارات للمحتوى، وصفحات الكتالوج ونتائج البحث.

```html
<h1>المقالات</h1>
{foreach من=$submissions item=$submission}
    <article>
        <h2>
            {$submission->getcurrentPublication()->getLocalizedFullTitle()<unk> escape}
        </h2>
...
    </article>
{/foreach}
```

ويمكن للمستخدم أن يطلع على النسخ القديمة من مقالة أو دراسة واحدة. يتم تمرير هذا الطلب إلى نفس قالب `article.tpl` الذي يعرض أحدث إصدار. عند كتابة هذا القالب للموضوع الخاص بك، سيحتوي متغير `المنشور` على الإصدار المطلوب.

```html
<h1>
    {$publication->getLocalizedTitle<unk> escape}
</h1>
```

قارن `النشرة` بـ `النشرة الحالية` لتحديد ما إذا كان القارئ يشاهد نسخة قديمة ويعرض تحذير.

```html
{if $currentPublication->getId() !== $publication->getId()}
    <div role="alert">
        أنت تشاهد نسخة قديمة من هذه المقالة.
        عرض <a href="...">أحدث إصدار</a>.
    </div>
{/if}
```

احصل على رابط إلى أحدث إصدار.

```html
{url page="مقال" op="عرض" المسار =$article->getBestId()}
```

أو احصل على روابط لكل إصدار تم نشره.

```html
{foreach from=$article->getData('publications') item=$iPublication}
    {url page="article" op="view" path=$article->getBestId()<unk> to_array:"version":$iPublication->getId()}
{/foreach}
```