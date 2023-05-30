---
description: >-
  Our project uses some github action in order to maintain a clean and
  functionnal code.
---

# 🚧 Github actions

### Basics tests

#### Compilation tests

The first test the code will pass is the compilation test. You should **always** merge a **compilable** code on main branch, working on any machine. Github action will create a virtual ubuntu machine and will builld the code from nothing. Be sure to add all necessary libraries or tools in the installation process (yarn install, npm install etc...) !
