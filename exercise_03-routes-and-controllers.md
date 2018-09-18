#### [Drupal 8 Backend Training](README.md)

## Exercise 3:

## Routes and Controllers

The simplest way to create a custom page in drupal is with a controller. You can use drupal console to create a controller and inject a service into it. That service can be used to get information. We will cover services more in depth in the next exercise, where we will create a custom one.

The first thing we will need to do is create a custom module as a starting point. Let's use [Drupal Console](https://drupalconsole.com/) to do some scaffolding for us:

1. Navigate to your drupal root on the command line and type

    ```bash
    lando drupal generate:module
    ```

    This may look a little confusing, but `drupal` is just the name of the executable for drupal console. This command will start up an interactive prompt -- enter the following (an empty prompt signifies that you can hit enter to confirm the default value)

    ```bash
     Enter the new module name:
     > Example

     Enter the module machine name [example]:
     >

     Enter the module Path [modules/custom]:
     >

     Enter module description [My Awesome Module]:
     >

     Enter package name [Custom]:
     >

     Enter Drupal Core version [8.x]:
     >

     Do you want to generate a .module file? (yes/no) [yes]:
     >

     Define module as feature (yes/no) [no]:
     >

     Do you want to add a composer.json file to your module? (yes/no) [yes]:
     >

     Would you like to add module dependencies? (yes/no) [no]:
     >

     Do you want to generate a unit test class? (yes/no) [yes]:
     >

     Do you want to generate a themeable template? (yes/no) [yes]:
     >

     Do you want proceed with the operation? (yes/no) [yes]:
     >

    ```

    You should now have the required module files: `example.info.yml` and `example.module` under `/modules/custom/example`.

2. Next let's use drupal console to generate a controller. Follow the example below, but make sure to use `lando drupal` instead of `vendor/bin/drupal`

![Generate Controller](https://user-images.githubusercontent.com/159693/45672711-bd397c00-badd-11e8-9660-08010da7949d.png)

3. Edit `web/modules/custom/example/src/Controller/ExampleController.php` change `getSiteName` to look like the following:

```
  /**
   * Getsitename.
   *
   * @return string|array
   *   Return Hello string.
   */
  public function getSiteName() {
    $site_name = $this->config('system.site')->get('name');

    return [
      '#type' => 'markup',
      '#markup' => $this->t('The site name is: :site_name', [':site_name' => $site_name]),
    ];
  }
```

4. Make note of the `example.routing.yml` file. This file tells drupal that there is a page that can be loaded at the `example/site-name` path and how to load it.

```
example.example_controller_getSiteName:
  path: '/example/site-name'
  defaults:
    _controller: '\Drupal\example\Controller\ExampleController::getSiteName'
    _title: 'Get site Name'
  requirements:
    _permission: 'access content'
```

5. Enable your module using the following command:

```bash
lando drush en example -y
```

6. Visit your local development site and navigate to the path defined in your routing file (/example/site-name).

#### Cheat sheet
`generate:controller` parameters:

```
 // Welcome to the Drupal Controller generator
 Enter the module name [module_filter]:
 > example

 Enter the Controller class name [DefaultController]:
 > ExampleController

 Enter the Controller method title (to stop adding more methods, leave this empty) []:
 > Gett site Name

 Enter the action method name [hello]:
 > getSiteName

 Enter the route path [/example/getSiteName]:
 > /example/site-name

 Enter the Controller method title (to stop adding more methods, leave this empty) []:
 > 

 Do you want to generate a unit test class? (yes/no) [yes]:
 > 

 Do you want to load services from the container? (yes/no) [no]:
 > yes


Type the service name or use keyup or keydown.
This is optional, press enter to continue

 Enter your service []:
 > config.factory
 Enter your service []:
 > 

 Do you want proceed with the operation? (yes/no) [yes]:
 > yes
```

[Next Exercise (#4 Custom Services)](exercise_04-custom-services.md)
