# Strict Type Declaration CS issue

> Note: `config/development.config.php.dist` is a direct copy from the [Mezzio Skeleton](https://github.com/mezzio/mezzio-skeleton/blob/3.6.x/config/development.config.php.dist).

## Instructions

1. Copy `config/development.config.php.dist` to `config/development.config.php`
2. Run CS check: `./vendor/bin/phpcs`

Result:

```powershell
C:\source\strict-type-declaration-cs-issue> .\vendor\bin\phpcs
E 1 / 1 (100%)



FILE: config\development.config.php
----------------------------------------------------------------------
FOUND 2 ERRORS AFFECTING 2 LINES
----------------------------------------------------------------------
 24 | ERROR | [x] Wrong place of strict type declaration statement;
    |       |     must be above comment
 29 | ERROR | [x] Expected 24 spaces before double arrow; 1 found
----------------------------------------------------------------------
PHPCBF CAN FIX THE 2 MARKED SNIFF VIOLATIONS AUTOMATICALLY
----------------------------------------------------------------------

Time: 347ms; Memory: 10MB
```

3. Run CS fix: `./vendor/bin/phpcbf`

Result:

```powershell
C:\source\strict-type-declaration-cs-issue> .\vendor\bin\phpcbf
F 1 / 1 (100%)



PHPCBF RESULT SUMMARY
----------------------------------------------------------------------
FILE                                                  FIXED  REMAINING
----------------------------------------------------------------------
config\development.config.php                         2      1
----------------------------------------------------------------------
A TOTAL OF 2 ERRORS WERE FIXED IN 1 FILE
----------------------------------------------------------------------

Time: 476ms; Memory: 10MB

```

4. Run CS check again: `./vendor/bin/phpcs`

Result:

```powershell
C:\source\strict-type-declaration-cs-issue> .\vendor\bin\phpcs
E 1 / 1 (100%)



FILE: config\development.config.php
----------------------------------------------------------------------
FOUND 1 ERROR AFFECTING 1 LINE
----------------------------------------------------------------------
 5 | ERROR | The file-level docblock must follow the opening PHP tag
   |       | in the file header
----------------------------------------------------------------------

Time: 340ms; Memory: 10MB
```

5. Conclusion

Initially the CS shows the error:

> Wrong place of strict type declaration statement; must be above comment

`phpcbf` is able to fix it. But CS then shows a new error:

> The file-level docblock must follow the opening PHP tag in the file header
