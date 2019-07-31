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


from allauth.account.forms import LoginForm
class MyCustomLoginForm(LoginForm):
  def login(self, *args, **kwargs):
    return super(MyCustomLoginForm, self).login(*args, **kwargs)

ACCOUNT_FORMS = {'login': 'mysite.forms.MyCustomLoginForm'}

from allauth.account.forms import SignupForm
class MyCustomSignupForm(SignupForm):
  def save(self, request):
    user = super(MyCustomSignupForm, self).save(request)
    return user

ACCOUNT_FORMS = {'signup': 'mysite.forms.MyCustomSignupForm'}

from allauth.account.forms import ChangePasswordForm
class MyCustomChangePasswordForm(ChangePasswordForm):
  def save(self):
    super(MyCustomChangePasswordForm, self).save()

ACCOUNT_FORMS = {'change_password': 'mysite.forms.MyCustomChangePasswordForm'}

```

```
```

```
```


