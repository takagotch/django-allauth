### django-allauth
---
https://github.com/pennersr/django-allauth

```py
from django.contrib.auth.validators import ASCIIUsernameValidator
custom_username_validators = [ASCIIUsernameValidator()]
ACCOUNT_USERNAME_VALIDATORS = 'some.module.validators.custom_username_validators'


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

from allauth.account.decorators import verified_email_required
@verified_email_required
def verified_users_only_view(request):

ACCOUNT_USER_MODEL_USERNAME_FIELD = None
ACCOUNT_EMAIL_REQUIRED = True
ACCOUNT_USERNAME_REQUIRED = False
ACCOUNT_AUTHENTICATION_METHOD = 'email'


ACCOUNT_ADAPTER = 'project.users.adapter.MyAccountAdapter'
from django.conf import settings
from allauth.account.adapter import DefaultAccountAdapter
class MyAccountAdapter(DefaultAccountAdapter):
  def get_login_redirect_url(self, request):
    path = "/accounts/{username}/"
    return path.format(username=request.user.username)

from django.contrib import admin
from django.contrib.auth.decorators import login_required
admin.site.login = login_requreid(admin.site.login)


class GoogleNoDefaultScopeProvider(GoogleProvider):
  id = 'google_no_scope'
  def get_default_scope(self):
    return []
provider_classes = [GoogleNoDefaltScopeProvider]
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

{% providers_media_js %}

{% get_social_accounts user as accounts %}

{{accounts.twitter}} -- a list of connected Twitter accounts
{{accounts.twitter.0}} -- the first Twitter account
{% if accounts %} -- if there is at least one social account

{% get_providers as socialaccount_providers %}
```

```
```


