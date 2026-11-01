# Django Custom User Model (experiment)

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-4.2-092E20?logo=django&logoColor=white)
![Status](https://img.shields.io/badge/status-early%20stage-f7768e)

An early-stage Django project exploring a **custom user model**. It defines `CustomUser(AbstractUser)` with extended profile fields and wires up a registration form and admin configuration. Treat it as a learning sandbox rather than a finished application.

## What's inside

- `users/models.py` – `CustomUser` extends `AbstractUser` with date of birth, phone number, state of origin, sex, hobbies, about me, address, occupation, department/unit and a profile picture (`ImageField`). `groups` and `user_permissions` use custom `related_name`s.
- `users/forms.py` – `CustomUserCreationForm` (username, password pair and the profile fields) and `CustomUserForm` for editing profile fields.
- `users/views.py` – `register` view that validates the form, saves the user, logs them in and adds a success message.
- `users/admin.py` – admin list display covering the custom fields.
- `user_management/` – project settings (SQLite, media uploads) and URL configuration (`/register/`, `/admin/`).

## Running it

```bash
git clone https://github.com/Blueskale/user_management.git
cd user_management
python3 -m venv venv && source venv/bin/activate
pip install "Django>=4.2,<5" Pillow
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Visit http://127.0.0.1:8000/admin/ to manage custom users.

## Status and known gaps

- `AUTH_USER_MODEL` is not set in `settings.py` yet, so Django still authenticates against its default `User`; `CustomUser` exists as a separate table.
- The registration template is a placeholder, and the view redirects to a `user_profile` URL that has not been defined.
- A local virtual environment (`myenv/`) was committed by mistake; the project does not depend on it.
