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

from allauth.account.forms import SetPasswordForm
class MyCustomSetPasswordForm(SetPasswordForm):
  def save(self):
    super(MyCustomSetPasswordForm, self).save()

ACCOUNT_FORMS = {'set_password': 'mysite.forms.MyCustomSetPasswordForm'}

from allauth.account.froms import ResetPasswordForm
class MyCustomSetPasswordForm(ResetPasswordForm):
  email_address = super(MyCustomResetPasswordForm, self).save()
  return email_address

ACCOUNT_FORMS = {'reset_password': 'mysite.forms.MyCustomResetPasswordForm'}


SOCIALACCOUNT_FORMS = {
  'login': 'allauth.socialaccount.forms.DisconnectForm',
  'signup': 'allauth.socialaccount.forms.SignupForm',
}

from allauth.socialaccount.forms import SignupForm
class MyCustomSocialSignupForm(SignupForm):
  def save(self):
    user = super(MyCustomSocialSignupForm).save()
    return user

SOCIALACCOUNT_FORMS = {'signup': 'mysite.forms.MyCustomSocialSignupForm'}

from allauth.socialaccount.forms import DisconnectForm
class MyCustomSocialDisconnectForm(DisconnectForm):
  def save(self):
    super(MyCustomSocialDisconnectForm).save()

SOCIALACCOUNT_FORMS = {'disconnect': 'mysite.forms.MyCustomSocialDisconnectForm'}
```

```
{% load account %}
{% user_display user %}

{% load account %}
{% user_display user as user_display %}
{% blocktrans %}{{ user_display }} has logged in...{% endblocktrans %}


{% load socialaccount %}
<a href="{% provider_login_url "openid" openid="https://www.google.com/accounts/o8/id" next="/success/url/" %}"></a>
<a href="{% provider_login_url "twitter" %}">Twitter</a>

```

```
```


