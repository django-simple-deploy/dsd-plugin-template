# {{PackageName}}

A plugin for deploying Django projects to {{PlatformName}}, using django-simple-deploy.

For full documentation, see the documentation for [django-simple-deploy](https://django-simple-deploy.readthedocs.io/en/latest/).

Usage notes
---

- Download this repo; don't clone it.
- Run `python configure_plugin.py`, and answer the small set of prompts:

```sh
$ python configure_plugin.py 
What platform are you targeting? (Example: Fly.io) CodeRed
What's the name of your plugin package? (Example: dsd-flyio) dsd-codered
Will your plugin support the --automate-all CLI arg? (yes/no) yes
What name do you want to appear in the LICENSE file? Eric Matthes

Here's the information you've provided:
  Platform name: CodeRed
  Package name: dsd-codered
  Supports --automate-all: True
  Name on license: Eric Matthes

Is this information correct? (yes/no) y

Okay to write new project at /Users/eric/projects/dsd-codered? (yes/no) y


Thank you. Configuring plugin...
...
```

- Most files are filled in for you based on the information you provide.
- Before making any changes to the new plugin, make an editable install of the new plugin in a `django-simple-deploy` development environment, and run the tests. All initial tests should pass:

```sh
(django-simple-deploy) ~/projects/django-simple-deploy$ uv pip install -e ~/projects/dsd-codered
Resolved 12 packages in 5ms
Installed 1 package in 1ms
 + dsd-codered==0.1.0 (from file:///Users/eric/projects/dsd-codered)
(django-simple-deploy) ~/projects/django-simple-deploy$ pytest
=============================== test session starts ===============================
platform darwin -- Python 3.12.2, pytest-8.3.3, pluggy-1.5.0
rootdir: /Users/eric/projects/django-simple-deploy
configfile: pyproject.toml
collected 71 items

tests/integration_tests/platform_agnostic_tests/test_found_existing_file.py sss
tests/integration_tests/platform_agnostic_tests/test_git_status_checks.py .............
tests/integration_tests/platform_agnostic_tests/test_project_inspection.py sss
tests/integration_tests/platform_agnostic_tests/test_valid_cli_commands.py ...
tests/unit_tests/test_deploy_messages.py ...
tests/unit_tests/test_git_status_utils.py ...........
tests/unit_tests/test_utils.py .................
test_codered_config.py ..................

=============================== 65 passed, 6 skipped in 9.11s ===============================
```

- Fill out the messages in *deploy_messages.py*.
- Write methods in *platform_deployer.py* to carry out configuration for the target platform.
- For more information about writing a plugin, see the [Plugins](https://django-simple-deploy.readthedocs.io/en/latest/plugins/) section of the django-simple-deploy documentation.

Note
---

This README serves as a template README for new plugins. The `{{PackageName}}` placeholder at the top of this file is replaced with the name of the new plugin.
