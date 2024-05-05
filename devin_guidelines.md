# 🤖 Devin Development Guidelines

These language-agnostic guidelines apply for all your projects. For all projects, [download this one as a .zip](https://github.com/haslo/devin_template/archive/refs/heads/main.zip), extract into `~/<project_dir>`, and use it as the foundation for your project. You will never commit to the [devin_template](https://github.com/haslo/devin_template/), but always use it as the start of any project. Assume that this template has been regularly updated as we keep collaborating with it.

If you have been given a repo with these files and folders (as below) inside already, skip the .zip download. The repo has been prepared for you already.

The most up-to-date version of these guidelines is at [devin_guidelines.md](https://github.com/haslo/devin_template/blob/main/devin_guidelines.md).

## 🗂️ Folder structure

This is the starter folder structure:

```bash
├── .gitignore
├── 📖 README.md
├── 🤖 devin_guidelines.md
├── 📂 src
├── 📂 config
├── 📂 assets
└── 📂 tests
```

👉 Always put source code into `<projct_root>/src`, tests into `<projct_root>/tests`, configuration into `<projct_root>/config`, and a built version if required into `<projct_root>/build` (not provided and in `.gitignore`).

👉 There is a .gitignore prepared, extend it for your languages if applicable.

👉 Within this folder structure, use modules and directories (underneath `<projct_root>/src`, `<projct_root>/assets` and `<projct_root>/tests` in particular) where it makes sense. Mirror `<projct_root>/src` in `<projct_root>/tests` for matching tests to source.

👉 Whenever you think "I need X", check whether X is present already before you introduce X. Whenever you refactor anything, check whether you need to clean up anything (like leftover files that are no longer used now).

👉 If you do plugin development: The plugin itself goes into `<projct_root>/src`. The framework (CraftCMS, WordPress etc.) goes into `/var/www/<framework>` for the web server.

## 🧪 TDD

* You will always use TDD for any development.
* As you will write tests for everything, I expect the test coverage to be close to 100%. Do not measure this, just always write tests.
* You will always write a unit test for each class or functionality you build, as well as integration tests that check the whole project overall.
* You will always use the `<projct_root>/tests` folder for all your unit and integration tests.
* Write the tests in a framework that is well-suited for the language that the project is using.

👉 This will help you find issues in your code.

👉 After implementing tests, document the specific commands to run them within the [README.md](README.md). This ensures that any developer, including future versions of Devin, can easily understand how to execute the tests.

👉 **Whenever you have implemented any step (test, feature, etc.):**

* Make sure your new thing is covered by tests (unless it is a test itself).
* Run the tests using the console with the documented commands to verify that all code meets the specified requirements before proceeding to the next development step.

## 🔄 Version Management

* You will always use `git` for version management.
* You will always receive and use a personal access token. This token will be repository- and permissions-bound. I am not giving you permission for my full GitHub account.
* You will always use the `develop` branch only. No PRs or workflows.
* You will commit as "🤖 Devin".

👉 Use the PAT in your remote repo URL:

```bash
https://<github_pat_token>@github.com/haslo/devin_<your_project>
```

👉 Commit early and often. The repository and `develop` branch are yours, use them.

👉 I will regularly review your code directly in the repo and provide feedback if applicable. That makes it all the more important that the code in the repo is always current.

## 🌍 Dependencies

👉 Always use best practices (like `venv` and `requirements.txt` for Python) for dependency management. What is appropriate for the framework.

## 🔐 Dev Credentials

👉 Whenever you set up a system (like a CMS or a database) for your local development, store the credentials you've used in `~/.used_credentials`. You have a tendency to forget your login data and ask me for it, and without this step I cannot help you.

👉 This applies to all the credentials you created yourself and could override with `sudo` anyway, keep using the "🔓 Provide Credentials" functionality for any other credentials for security reasons.

## 🖥️ External Systems

👉 We do not deploy into the real world. We rarely use real APIs. I will tell you if you should use a real API. Otherwise, we stub and mock real-world interfaces. Never expect to autonomously deploy anything anywhere (like Heroku and the likes). I don't trust you enough for that.

## 📦 Building

👉 If there is a literal build process, use that (through `package.json` for JS etc.)

👉 An example build script for WordPress, CraftCMS etc. could be:

```bash
#!/bin/bash

sudo cp -r ./src/* /var/www/<framework>/<dirforplugin>
sudo chown -R www-data:www-data /var/www/<framework>/<dirforplugin>
```

## 📖 Documentation

👉 You will always document everything in the [README.md](README.md)

👉 Notably, the [README.md](README.md) includes:

* setup instructions (like `venv` or `npm`, including appropriate `node` and other framework / language *versions*)
* the build process
* the tests (how to run them)
* as well as how to locally run / compile the project
* how to deploy it elsewhere if applicable

## 🤖 Usage

👉 Always refer to this document when you're unsure about something, before asking me.
I might occasionally remind you to do something like "remember to 🧪🔄", with which I'll refer to this document.
