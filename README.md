# PHP Code Challenge

*a repository helping you to solve AdventOfCode challenges using PHP*

[![CI](https://github.com/frederikhs/php-code-challenge/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/frederikhs/php-code-challenge/actions/workflows/ci.yml)
[![License](https://img.shields.io/github/license/frederikhs/php-code-challenge)](LICENSE)

### How to get started

#### Requirements
- git
- make
- docker

```bash
# clone this repository
git@github.com:frederikhs/php-code-challenge.git

# change directory
cd php-code-challenge

# build the development docker container and log in
make

# example output
[php-code-challenge] hiper@699bb1052ac8:/var/php-code-challenge $
```

### Run solution
Your solution can be run in two different ways. Either with a test using PHPUnit or with a script like [**scripts/run_year_2021_day_02.php**](code/scripts/run_year_2021_day_02.php).

To run a solution using PHPUnit, inside the development container run the following composer commands:

```bash
# to run PHPStan and PHPUnit
[php-code-challenge] hiper@699bb1052ac8:/var/php-code-challenge $ composer test

# to only run PHPStan
[php-code-challenge] hiper@699bb1052ac8:/var/php-code-challenge $ composer phpstan

# to only run PHPUnit
[php-code-challenge] hiper@699bb1052ac8:/var/php-code-challenge $ composer phpunit
```

To run a solution with a script, inside the development container run the following command:

```bash
[php-code-challenge] hiper@699bb1052ac8:/var/php-code-challenge $ php scripts/run_year_2021_day_02.php 
```

### Project layout

Inside the [**code**](code) directory, the following structure is set up
- [**input**](code/input) (for input files related to your solutions)
- [**scripts**](code/scripts) (for php scripts if you want to run your code using a script)
- [**src**](code/src) (for your solutions to be implemented in)
- [**tests**](code/tests) (for your solutions to be tested. This is the preferred way of running your solution)

Inside [**input**](code/input) files are scoped using a directory structure where files are grouped by the year and day of the challenge.

Inside [**src**](code/src) each challenge has its own namespace allowing you to implement your solution using a single class like [**Year2021Day02**](code/src/Year2021Day02/Solution.php), or using multiple files.

The [**tests**](code/tests) are using a flattened layout since each challenge consists of only two files. A [**SolutionHelper**](code/tests/lib/SolutionHelper.php) class can be extended to facilitate easier reading of input files. 

### CI using GitHub Actions

This repository contains a [**ci.yml**](.github/workflows/ci.yml) file with a workflow that runs PHPStan and PHPUnit whenever your push. This ensures that even if you did not run the tests before pushing, GitHub Actions will.

### Aligning Code Style

With this repository you also have an option to fix code style using PHP CS Fixer. The code style is defined in [**.php-cs-fixer.dist.php**](code/.php-cs-fixer.dist.php).

To fix code style, inside the development container run the following command:

```bash
[php-code-challenge] hiper@699bb1052ac8:/var/php-code-challenge $ composer fix
```