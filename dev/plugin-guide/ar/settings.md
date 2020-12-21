---
title: إعدادات الإضافات - دليل الإضافات لOJS و OMP
---

# إعدادات الإضافات

يمكن للإضافات إضافة إعدادات حتى يمكن للمحرر أو المشرف تكوين الإضافة. يتم الوصول إلى الإعدادات من خلال قائمة الإضافات في منطقة إعدادات الموقع.

> يصف هذا القسم كيفية إنشاء نموذج إعدادات منفصل للملحق. في بعض الحالات، ستوفر تجربة مستخدم أفضل إذا قمت بإضافة إعدادات إلى نماذج الإعدادات الحالية. تعلم كيفية تعديل نموذج موجود في [مثال الحقل المخصص](./examples-custom-field). 
> 
> {:.tip}

أضف طريقة `getActions()` إلى البرنامج المساعد الخاص بك لإضافة إجراء الإعدادات في قائمة الإضافات.

![لقطة شاشة تظهر إجراء إعدادات لملحق لغة نمط الاستشهاد](../plugin-settings-action.png)

```php
البرنامج التعليمي لمدرب الامثل الاضافي يمد برنامج Genericplugin {
    الدالة العامة getActions($request, $actionArgs{

    // احصل على الإجراءات الموجودة
        $actions = الأصل :getActions($request, $actionArgs)؛
        إذا (!$this->getEnabled()) {
            العودة $actions;
        }

    // إنشاء LinkAction الذي سيتصل بالأسلوب المساعد
    // "الإدارة" مع الفعل "إعدادات".
        $router = $request->getRouter();
        استيراد ('lib.pkp.classes.linkAction.request. JaxModal')؛
        $linkAction = LinkAction(
            'إعدادات',
            AjaxModal(
                $router->url(
                    $request,
                    بطل،
                    بطل،
                    'إدارة',
                    بطل،
                    صفيفة(
                        'فعل' => 'إعدادات',
                        'إضافة' => $this->getName(),
                        'الفئة' => 'العامة'
                    )
                )،
                $this->getDisplayName()
            )،
            __('المدير'. لوغين العروض)،
            ملغاة
        )؛

    // أضف رابط العمل إلى الإجراءات القائمة.
    // أجعلها أول إجراء يكون متسقا مع
    // إضافات أخرى.
        array_unshift($actions، $linkAction)؛

        إرجاع $actions؛
    }
}
```

أضف طريقة `إدارة ()` لتحميل نموذج الإعدادات عند النقر على `LinkAction`.

```php
البرنامج التعليمي الموسع يوسع البرنامج المساعد Genericplugin {
    إدارة الوظيفة العامة ($args, $request{
        تبديل ($request->getUserVar('verb')) {

      // إرجاع رد JSON الذي يحتوي على
      // إعدادات نموذج
      الحالة 'إعدادات':
        $templateMgr = TemplateManager:::getManager($request)؛
        $settingsForm = $templateMgr->جلب ($this->getTemplateResource('إعدادات). pl'));
        إرجاع JSONMessage(true, $settingsForm);
        }
        إعادة الوالد::manage($args, $request)؛
    }
}
```

```html
<!-- templates/settings.tpl -->
<form>
  <label for="secretKey">المفتاح السري</label>
  <input type="text" name="secretKey" value="secretKey">
  <button type="submit">حفظ</button>
</form>
```

## صف الاستمارة

يمكن للإضافات استخدام نظام معالجة نموذج التطبيق لتحميل إعدادات الإضافات والتحقق منها وحفظها. قم بتحديث طريقة `الإدارة ()` لاستخدام نموذج `المخصص`.

```php
البرنامج التعليمي الموسع يوسع البرنامج المساعد Genericplugin {
    إدارة الوظيفة العامة ($args, $request{
        تبديل ($request->getUserVar('verb')) {
      الحالة 'إعدادات':

        // تحميل النموذج المخصص
        $this->استيراد ('tutorialexamSettingsForm')؛
        $form = نموذج دروس دراسي جديد($this)؛

        // إحضار النموذج لأول مرة يحمله، قبل
        // حاول المستخدم حفظه
        إذا (!$request->getUserVar('save')) {
          $form->initData();
                  إرجاع JSONMessage(صحيح, $form->جلب ($request))؛
        }

        // المصادقة على النموذج وتنفيذه
        $form->readInputData();
        إذا كان ($form->تحقق ()) {
          $form->تنفيذ();
          إرجاع JSONMessage(صحيح)؛
        }

        عائد الوالد::manage($args, $request)؛

}
```

يحدد صف `استمارة` القالب، ويضع قواعد التحقق ويحفظ إعدادات الإضافة.

```php
استيراد ('lib.pkp.classes.form). المهر')؛
البرنامج التعليمي التدريبي الموسع، تمدد النموذج {

  /** @var TutorialexamplePlugin */
  العام $plugin؛

    وظيفة عامة __construct($plugin) {

    // تحديد قالب الإعدادات وتخزين نسخة من عنصر الإضافة
        الوالد:__construct($plugin->getTemplateResource('إعدادات). pl'));
    $this->الملحق = $plugin;

    // دائماً إضافة POST والتحقق من صحة CSRF لتأمين النموذج الخاص بك.
        $this->addCheck(FormValidatorPost($this));
        $this->addCheck(FormValidatorCSRF($this));
    }

  /**
   * إعدادات التحميل المحفوظة بالفعل في قاعدة البيانات
   *
   * يتم تخزين الإعدادات حسب السياق، بحيث يمكن لكل مجلة أو اضغط
   * أن يكون لها إعدادات مختلفة.
   */
    وظيفة عامة initData() {
    $contextId = التطبيق: :get()->getrequest()->getContext()->getId();
    $this->setData('Key', $this->plugin->getSetting($contextId, 'سر المفتاح'))؛
    الوالد:initData();
    }

  /**
   * تحميل البيانات التي تم تقديمها مع النموذج
   */
    الوظيفة العامة (readInputData() {
        $this->ReUserVars(['secretKey'])؛
    الوالد:readInputData();
  }

  /**
   * إحضار أي بيانات إضافية مطلوبة لاستمارة البيانات الخاصة بك.
   *
   * البيانات التي تم تعيينها في النموذج باستخدام $this->setData() خلال
   * initData() أو readInputData() سيتم تمريرها إلى القالب
*.
   */
    جلب الوظيفة العامة ($request، $template = null، $display = خطأ) {

    // مرير اسم الملحق إلى القالب بحيث يمكن أن يكون
    // مستخدم في عنوان URL الذي يتم إرسال النموذج إلى
    $templateMgr = TemplateManager::getManager($request)؛
    $templateMgr->تعيين ('pluginName', $this->plugin->getName())؛

    عودة الوالد::fetch($request، $template، $display)؛
  }

    /**
     * حفظ الإعدادات
     */
    تنفيذ الوظيفة العامة() {
    $contextId = التطبيق: :get()->getrequest()->getContext()->getId();
        $this->إضافة->تحديث($contextId، 'سر Key', $this->getData('سر Key'))؛

    // أخبر المستخدم أن الحفظ ناجح.
        import('classes.notification.NotificationManager');
        $notificationMgr = new NotificationManager();
        $notificationMgr->createTrivialNotification(
      Application::get()->getRequest()->getUser()->getId(),
      NOTIFICATION_TYPE_SUCCESS,
      ['contents' => __('common.changesSaved')]
    );

        return parent::execute();
    }
}
```

قم بتحديث قالب `settings.tpl` لإرسال النموذج إلى طريقة `إدارة ()` للملحق الإضافي.

```html
<script>
    $(function() {ldelim}
        $('#tutorialExampleSettings').pkpHandler('$.pkp.controllers.form. JaxFormHandler');
    {rdelim});
</script>

<form
  class="pkp_form"
  id="tutorialExampleSettings"
  method="POST"
  action="{url router=$smarty.const.ROUTE_COMPONENT op="manage" category="generic" plugin=$pluginName verb="settings" save=true}"
>
  <! - إضافة رمز csrf دائما لتأمين شكلك-->
    {csrf}

  {fbvFormArea}
        {fbvFormSection}
            {fbvElement
        type="text"
        id="المفتاح"
        value=$secretKey
        label="plugins. enic.tutorialexam. ecretKey"
      }
        {/fbvFormSection}
  {/fbvFormArea}
    {fbvFormButtons submitText="عادي. ave"}
</form>
```

---

عندما تكون مستعدا، يمكنك [تحرير الملحق الخاص بك](./release) للجمهور.
