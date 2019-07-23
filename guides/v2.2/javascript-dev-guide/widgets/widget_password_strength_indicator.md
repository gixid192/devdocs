---
group: javascript-developer-guide
subgroup: 3_Widgets
title: PasswordStrengthIndicator widget
---

## Overview {#password_strength_indicator_overview}

The Magento password strength indicator {% glossarytooltip f0dcf847-ce21-4b88-8b45-83e1cbf08100 %}widget{% endglossarytooltip %} provides immediate feedback on the validity and strength of a password while it is being typed.
If the password is not strong enough, Magento prompts the user to choose a new password.

The password strength indicator widget source is [`<Magento_Customer_module_dir>/view/frontend/web/js/password-strength-indicator.js`].

The widget is being used in the following templates:

- [`<Magento_Ui_module_dir>/view/frontend/templates/form/register.phtml`] customer register template.
- [`<Magento_Ui_module_dir>/view/frontend/templates/form/forgotpassword.phtml`] customer forgot password template.
- [`<Magento_Ui_module_dir>/view/frontend/templates/form/edit.phtml`] customer account edit template.

## Initialize the password_strength_indicator widget {#password_strength_indicator_initialize}

To initialize the widget in your script, use the following general notation:

```javascript
$('#password-input').passwordStrengthIndicator({
    <option1>: <value1>,
    <option2>: <value2>,
    ...
});
```

For details about how to initialize the widget in a`.phtml` template, refer to the [JavaScript initialization]({{ page.baseurl }}/javascript-dev-guide/javascript/js_init.html){:target="_blank"} topic.

## Options {#password_strength_indicator_options}

The password strength indicator widget has the following options:
-   [passwordSelector](#password_strength_indicator_password_selector)
-   [passwordStrengthMeterSelector](#password_strength_indicator_password_strength_meter_selector)
-   [passwordStrengthMeterLabelSelector](#password_strength_indicator_password_strength_meter_label_selector)
-   [formSelector](#password_strength_indicator_form_selector)
-   [emailSelector](#password_strength_indicator_email_selector)

### passwordSelector {#password_strength_indicator_password_selector}

Selector for the password input.

**Type**: String 

**Default value**: `[type=password]`

### passwordStrengthMeterSelector {#password_strength_indicator_password_strength_meter_selector}

Selector for the password strength visualization block.

**Type**: String 

**Default value**: `[data-role=password-strength-meter]`

### passwordStrengthMeterLabelSelector {#password_strength_indicator_password_strength_meter_label_selector}

Selector for the password strength visualization block label.

**Type**: String 

**Default value**: `[data-role=password-strength-meter-label]`

### formSelector {#password_strength_indicator_form_selector}

The selector for the form block.

**Type**: String 

**Default value**: `form`

### emailSelector {#password_strength_indicator_email_selector}

The selector for the email input.

**Type**: String 

**Default value**: `input[type="email"]`

## Events {#password_strength_indicator_events}

The password strength indicator widget listens for `change`, `keyup`, and `paste` events on the password and the email inputs. Listening to the email input is optional.

## Code sample

The following example shows how to initialize the password strength indicator widget and pass options during the initialization.

```html
<form action="BACKEND_ACTION" method="post">
    <fieldset class="fieldset">
        <div class="field password required" data-mage-init='{"passwordStrengthIndicator": {
            "passwordStrengthMeterSelector":"[data-role=strength-meter]",
            "passwordStrengthMeterLabelSelector":"[data-role=strength-meter-label]"
        }}'>
            <label class="label" for="password">Password</label>
            <div class="control">
                <input type="password" class="input-text" name="password" id="password">
                <div id="password-strength-meter-container" data-role="strength-meter" aria-live="polite">
                    <div id="password-strength-meter" class="password-strength-meter">
                        <span id="password-strength-meter-label" data-role="strength-meter-label">
                            No Password
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </fieldset>
    <div class="actions-toolbar">
        <div class="primary">
            <button type="submit" class="action submit primary"><span>Set a New Password</span></button>
        </div>
    </div>
</form>
```

### Result

The result is an indication of the strength of the user's password.

![Password Strength Indicator Widget]({{ site.baseurl }}/common/images/widget/password-strength-indicator-widget-result.png)