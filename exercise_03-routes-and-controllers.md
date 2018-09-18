## Routes and Controllers

The is a simple way to create a custom page in drupal is with a controller. You can use drupal console to create a controller and inject a service into it. That service can be used to get information.

![Generate Controller](https://user-images.githubusercontent.com/159693/45672711-bd397c00-badd-11e8-9660-08010da7949d.png)

Edit `web/modules/custom/example/src/Controller/ExampleController.php` change `getSiteName` to look like the following:

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

Make note of the `example.routing.yml` file. This file tells drupal that there is a page that can be loaded at the `example/site-name` path and how to load it.

```
example.example_controller_getSiteName:
  path: '/example/site-name'
  defaults:
    _controller: '\Drupal\example\Controller\ExampleController::getSiteName'
    _title: 'Get site Name'
  requirements:
    _permission: 'access content'
```

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
