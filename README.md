# PHPCS Differing Results POC

This repo shows PHPCS will provide different results when running against single and multiple files.

To reproduce the issue:

1. `git clone` this repo and `cd` into the project root
1. `composer install` to install dependencies
1. Run ` ./vendor/bin/phpcs`
1. Run ` ./vendor/bin/phpcs category.php`
1. Notice PHPCS flags warnings in `category.php` only when run against the project

The output will be the following:

#### Output of ` ./vendor/bin/phpcs`:

```
FILE: /path/to/phpcs_poc/functions.php
----------------------------------------------------------------------------------------
FOUND 0 ERRORS AND 2 WARNINGS AFFECTING 2 LINES
----------------------------------------------------------------------------------------
 13 | WARNING | Comment refers to a TODO task "Load this conditionally"
    |         | (Generic.Commenting.Todo.TaskFound)
 15 | WARNING | In footer ($in_footer) is not set explicitly wp_enqueue_script; It is
    |         | recommended to load scripts in the footer. Please set this value to
    |         | `true` to load it in the footer, or explicitly `false` if it should be
    |         | loaded in the header.
    |         | (WordPress.WP.EnqueuedResourceParameters.NotInFooter)
----------------------------------------------------------------------------------------
FILE: /path/to/phpcs_poc/category.php
----------------------------------------------------------------------------------------
FOUND 0 ERRORS AND 2 WARNINGS AFFECTING 2 LINES
----------------------------------------------------------------------------------------
 11 | WARNING | Found precision alignment of 1 spaces.
    |         | (WordPress.WhiteSpace.PrecisionAlignment.Found)
 12 | WARNING | Found precision alignment of 1 spaces.
    |         | (WordPress.WhiteSpace.PrecisionAlignment.Found)
----------------------------------------------------------------------------------------
```

#### Output of ` ./vendor/bin/phpcs category.php`:


```
. 1 / 1 (100%)

Time: 132ms; Memory: 8Mb
```

#### Output of ` ./vendor/bin/phpcs functions.php`:

```
FILE: /path/to/phpcs_poc/functions.php
----------------------------------------------------------------------------------------
FOUND 0 ERRORS AND 2 WARNINGS AFFECTING 2 LINES
----------------------------------------------------------------------------------------
 13 | WARNING | Comment refers to a TODO task "Load this conditionally"
    |         | (Generic.Commenting.Todo.TaskFound)
 15 | WARNING | In footer ($in_footer) is not set explicitly wp_enqueue_script; It is
    |         | recommended to load scripts in the footer. Please set this value to
    |         | `true` to load it in the footer, or explicitly `false` if it should be
    |         | loaded in the header.
    |         | (WordPress.WP.EnqueuedResourceParameters.NotInFooter)
----------------------------------------------------------------------------------------
```
