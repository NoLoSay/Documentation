---
description: >-
  Makefile will allow Nolosay to have common commands to make easier
  comprehension
---

# 🤝 Makefile&#x20;

## <mark style="color:red;">Mandatory commands</mark>

#### install

_<mark style="color:green;">make install</mark>_ command will automatically install all necessary libraries for the project (API, back, front etc...).&#x20;

```makefile
install:
	@echo "running install..."
	// insert libraries installation process (yarn install, npm etc....)
```

#### build

_<mark style="color:green;">make build</mark>_ will build / compile your project in order to make it functional.

```makefile
build:
	@echo "Building project..."
	// insert your building process here (apk creation, server build etc...)
```

#### lint

_<mark style="color:green;">make lint</mark>_ keep the code clean. eYou must have a linter/formater process. Only the linter is mandatory, however the automatic formater is strongly recommended

```makefile
lint:
	@echo "running linter..."
	// insert your linter process (eslint, prettier etc...).
	// You can use yarn or npm script here if you prefer
```

#### unit-tests

_<mark style="color:green;">make unit-tests</mark>_ runs your tests. Keep the code safe.

```makefile
unit-tests:
	@echo "running unit-tests..."
	// insert your unit-tests process(es) here.
```

#### start

_<mark style="color:green;">make start</mark>_ will start your project (start the api, the server, the client etc...).

```makefile
start:
	@echo "Starting..."
	// insert your starting process here (yarn start, npm start etc...)
	// WARNING: prefer run it in background so it doesn't block
	// github-actions process(es).
```

## <mark style="color:red;">Name & Tag</mark>

Name and tag are based on package.json "name" and "version" property by default. If you don't have package.json or you want to set it manually, please change:

```makefile
TAG := $(shell cat package.json | grep 'version' | cut -d"\"" -f4)
NAME := $(shell cat package.json | grep 'name' | cut -d"\"" -f4)
```

## <mark style="color:red;">Github actions</mark>

#### basic tests

_<mark style="color:green;">make basic tests</mark>_ will execute make install, build, lint, unit-tests and start (start is not in background). This can be useful if you want to simulate a github action locally without using act brefore push your branch. &#x20;

```makefile
basic-tests:
	clear
	@echo "####################### BASIC TESTS for Nolosay: $(NAME) v.$(TAG) #######################"
	$(MAKE) install &&\
	$(MAKE) build &&\
	$(MAKE) lint &&\
	$(MAKE) unit-tests &&\
	$(MAKE) start
	// feel free to custom it, but make sure you have at least these make call.
```

## <mark style="color:red;">Exemple</mark>

Copy / paste this template to your new projects. Feel free to customize it with your own commands.

{% code title="Makefile" %}
```makefile
TAG := $(shell cat package.json | grep 'version' | cut -d"\"" -f4)
NAME := $(shell cat package.json | grep 'name' | cut -d"\"" -f4)

###### COMMANDS ######

## installation
install:
	@echo "running install..."

reinstall:
	@echo "running install..."

clear-install:
	@echo "Clearing installation..."

## build
build:
	@echo "Building project..."

## tests
unit-tests:
	@echo "running unit-tests..."
 

## lint & format
lint:
	@echo "running linter..."


## start
start:
	@echo "Starting..."


start-background:
	@echo "Starting in background..."


## github actions
basic-tests:
	clear
	@echo "####################### BASIC TESTS for Nolosay: $(NAME) v.$(TAG) #######################"
	$(MAKE) install &&\
	$(MAKE) build &&\
	$(MAKE) lint &&\
	$(MAKE) unit-tests &&\
	$(MAKE) start

## other
show_version:
	@echo $(NAME): v.$(TAG)

.PHONY: install lint build unit-tests show_version start-background start
```
{% endcode %}
