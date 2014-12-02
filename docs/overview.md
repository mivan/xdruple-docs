# Overview of xDruple technology stack

By xDruple we understand the system based on Drupal 7 core and contributed modules, that are organized and extended with our core patches and modules. The main purpose of all the actions we do with Drupal is to provide robust way to develop Drupal-based web systems in team environment with absolute guarantee of delivering all requested features.

## Technology stack

As our goal is to guarantee a quality and delivery of requested functionality, we prefer to strictly fix the stack of used technologies. So from down up we use these technologies:

- Ubuntu 14.04
- Nginx 1.4
- PHP 5.5
- PostgresQL 9.3
- Drupal 7
- SASS 3.2
- Compass 0.12
- Twitter Bootstrap 3
 
Also, for development we use Vagrant and VirtualBox to maintain virtual machines.

Both server and Vagrant setup is organized in our [xdruple-server](https://github.com/xtuple/xdruple-server) project.

## Composer and Satis

To maintain and deliver Drupal core and contrib modules (and other libraries too) we use [Composer](http://getcomposer.org). Composer is a dependency manager for PHP projects. By using it we gain few benefits:

- we can use different branches for contrib modules, so applying patches in one project make it immediately available for the other projects;
- we can use all the power of PHP community and its libraries, distributed via [Packagist](http://packagist.org);
- we can use PHP class auto-loader, provided by Composer.

Satis — is a Composer repository generator that allows to public own repositories without a need to publish them. So we can distribute forked from Drupal.org to Github contrib projects for our usage. Also through our Satis server we can distribute our own contrib modules and themes. Full list of the projects you can see on [satis.codedrivendrupal.com](http://satis.codedrivendrupal.com) (note, that even all modules are in the list, some of them may be actually a private repositories).

## Project structure

Default project structure is provided by [xdruple-drupal](https://github.com/xtuple/xdruple-drupal) repository. It carries only some default files needed to start the project. All the libraries, including Drupal core, are delivered by Composer automatically. During the development, Git will also maintain only code for the project itself (like theme or features) and configuration. 

## Code-Driven Drupal

We have to differ the same term "Code-Driven Drupal" that may be used in few meanings:

- [Code-Driven Drupal](https://github.com/CodeDrivenDrupal/code-driven-drupal/) as a forked and extended with some functionality version of [Pressflow 7](https://github.com/pressflow/7) (we would call it just "Drupal core" in documentation);
- Code-Driven Drupal as a development methodology, that doesn't require the xDruple stack, and just refers to the way Drupal is used (we wouldn't refer it, as we just assume that's the only methodology we use);
- Code-Driven Drupal as a set of modules, that allows us to provide Drupal development (we would call it "OpenCDD", referencing on of our key [module](git@github.com:CodeDrivenDrupal/opencdd.git) that is used to ensure some basic functionality).

## SASS/Compass

[SASS](http://sass-lang.com) is a language that compiles into CSS. It provides a lot of syntax sugar, including mixins and variables, which allows to simplify theming. [Compass](http://compass-style.org) is a framework for SASS. It provides it's own project structure, configuration and additional set of mixins. We use Compass via our own Drupal module [Compass](git@github.com:CodeDrivenDrupal/compass.git). This module allows other Drupal modules and themes declare the support of Compass, write their own styles in SASS and see re-compiled results immediately (after page reload, of course).

## Twitter Bootstrap 3

[Twitter Bootstrap](http://getbootstrap.com) is a CSS framework that provides decent set of front-end elements and good mobile/responsive support. As we've already been using SASS/Compass, we connect Bootstrap via official [Bootstrap for SASS](https://github.com/twbs/bootstrap-sass) port. But we not only connect Bootstrap styles to the project, but also have a [Bootstrap 3](https://github.com/CodeDrivenDrupal/bootstrap3) Drupal module. This module integrates Bootstrap very deep into Drupal by overriding default theming functions and behaviors.
