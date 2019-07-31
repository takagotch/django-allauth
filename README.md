### django-allauth
---
https://github.com/pennersr/django-allauth

```py
from django.contrib.auth.validators import ASCIIUsernameValidator
custom_username_validators = [ASCIIUsernameValidator()]
ACCOUNT_USERNAME_VALIDATORS = 'some.module.validators.custom_username_validators'

ACCOUNT_FORMS = {
  'login': 'allauth.account.forms.LoginForm',
  'signup': '',
  'add_email': '',
  
}
```

```
```

```
```


