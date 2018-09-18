#### [Drupal 8 Backend Training](README.md)

## Exercise 2:

## Configuration Management

One of the biggest accomplishments of Drupal 8 is the inclusion of a brand new configuration management system (sometimes referred to as CMI, something of a misnomer at this point, but which has stuck around since the project was an [initiative](https://www.drupal.org/about/strategic-initiatives) and stands for Configuration Management Initiative).

Those of you who have worked on Drupal 7 sites in the past may be familiar with the module "Features", a module with the stated purpose of bundling certain bits of configuration together as a "Feature" and exporting it to code so that it could be easily reused. Unfortunately this module ended up being abused to handle the problem of configuration management, a problem that we can summarize as follows: If I spend an hour and a half clicking checkboxes and toggling select lists the Drupal admin UI (maybe I'm creating a view or a new content type), how can I deploy these configuration changes from dev to stage to production without spending an additional hour and a half for each deployment redoing this configuration manually.

The configuration management system solves this problem by storing all site configuration as drupal entities that can be both exported to and imported from yaml files. At long last, Drupal has a consistent relaible method for saving configuration as revisionable code.

In addition to quick and easy configuration deployments, some other benefits include: consistency -- even if I was happy to spend that hour and a half making manual configuration changes, every deployment would be another opportunity to introduce bugs -- and resilliancy -- if there are issues with a config deployment we can immediately revert, review changes in version control, and quickly import the problematic code either in our local or dev environments for debugging.

In this exercise we will import the config currently saved in git, make and export a configuration change, and then verify that the change was preserved as importable code.

1. Navigate to your drupal docroot and open `/sites/default/config` either in a file browser, or text editor. The yaml files in this folder represent the configuration for your entire site. Browse the files for a minute, open some up in a text editor if you feel curious.

2. Navigate back to your drupal docroot on the command line and run

    ```bash
    lando drush cim
    ```

    The drush command `cim` (short for config-import) will import the config files currently saved in git.

3. Go back to the `/sites/default/config` directory, open node.type.article.yml, and take a look at the keys and values.

4. Log in to your local dev site and visit `/admin/structure/types/manage/article`, does this look familiar?

5. Let's make a change in the UI and see if we can get it to show up in the config file. Change the description for the Article content type to whatever you like, and click "Save content type".

6. Back on the command line, navigate to your docroot and run

    ```bash
    lando drush cex
    ```

    The drush command `cex` (short for config-export) will export your site's active config as yaml files into the config directory, overwritting the previous files. Make sure to type `y` to confirm your export.

7. Go back to the `/sites/default/config` directory and open node.type.article.yml. Do you see your change?

8. Now let's commit our change to git and write a meaningful commit message. This is left as an exercise, feel free to speak up if you need a little refresher!