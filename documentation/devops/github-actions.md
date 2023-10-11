---
description: >-
  Our project uses some github action in order to maintain a clean and
  functionnal code.
---

# 🚧 Github actions

## <mark style="color:red;">Basics tests</mark>

#### Compilation tests

The first test the code will pass is the compilation test. You should **always** merge a **compilable** code on main branch, working on any machine. Github action will create a virtual ubuntu machine and will builld the code from nothing. Be sure to add all necessary libraries or tools in the installation process (yarn install, npm install etc...) !

#### Unit-tests

The code should work as expected and every new feature should not break older ones. In order to maintain stability, every features must be tested with unit-tests. Unit-tests will be verified on  main's branch merge request, and you may not merge without passing it. Be sure to update your tests.

#### Code format tests

The code should respect format rules, and should be as clean as possible (no warnings, no error, no unused libraries etc...). We use ESLint and prettier for typescript. Feel free to use another formater or linter of your choice, but please be sure to respect format rules established in the [code format rules ](code-format-rules.md)section. We recommand you to implement the "format on save" function in your IDE so you are sure to always respect format.

#### Makefile

All these tests will be launched from a Makefile, with the _<mark style="color:green;">make basic-tests</mark>_ command. please refer to the [Makefile](../to-start/makefile.md) section for further information.

## <mark style="color:red;">Automatic deployment</mark>&#x20;

We deploy our project on a distant azure machine. The project is automatically deployed in docker containers when a new release is created.&#x20;
