### django-allauth
---
https://github.com/pennersr/django-allauth

```py
from django.contrib.auth.validators import ASCIIUsernameValidator
custom_username_validators = [ASCIIUsernameValidator()]
ACCOUNT_USERNAME_VALIDATORS = 'some.module.validators.custom_username_validators'

ACCOUNT_FORMS = {
  'login': 'allauth.account.forms.LoginForm',
  'signup': 'allauth.account.forms.SignupForm',
  'add_email': 'allauth.account.forms.AddEmailForm',
  'change_password': 'allauth.account.forms.ChangePasswordForm',
  'set_password': 'allauth.account.forms.SetPasswordForm',
  'reset_password': 'allauth.account.forms.ResetPasswordForm',
  'reset_password_from_key': 'allauth.account.forms.ResetPasswordKeyForm',
  'disconnect': 'allauth.socialaccount.forms.DisconnectForm'
}
```

```
```

```
```


