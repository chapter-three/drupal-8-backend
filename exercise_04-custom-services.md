#### [Drupal 8 Backend Training](README.md)

# Exercise 4:

## Creating a custom service.

You may be aware that Drupal has undergone a sea change in it's transition from 7 to 8. In addition to (almost) fully adopting an object oriented approach, Drupal 8 draws heavily from external frameworks and libraries. The most significant cornerstone of our new version of Drupal is the Symfony framework, a service oriented full stack php framework. Drupal 8 draws heavily from Symfony, using it for request and response handling, routes and controllers, templating, and, you guessed it, for services and the service container.

What is a service container? A service container is basically just a global object that you can use to retrieve services. What are services? Services are essentially just useful chunks of code that might be reused throughout your site. For example some services provided by core include `logger.factory` which you can use to create log entries (essentially replaces watchdog from d7), and `messenger` which you can use instead of `drupal_set_message`. Pulling these services from the service container allows Drupal to handle dependency management and to ensure that only services being used are actually instantiated, this leads to a cleaner more organized codebase, while providing performance benefits over other object oriented architectures.

In this exercise we will create a service that calculates California sales tax.

1. Now we can use console to generate the scaffolding for our service. Navigate to your drupal docroot and run the command:

    ```bash
    lando drupal generate:service
    ```

    This will once again start up an interactive prompt -- enter the following:

    ```bash
     Enter the module name [admin_toolbar]:
     > example

     Enter the service name [example.default]:
     > example.tax_calc

     Enter the Class name [DefaultService]:
     > ExampleTaxCalc

     Create an interface (yes/no) [yes]:
     > no

     Do you want to load services from the container? (yes/no) [no]:
     >

     Enter the path for the services [/modules/custom/example/src/]:
     >

     Do you want proceed with the operation? (yes/no) [yes]:
     >
     ```

2. You now have all the scaffolding code needed for a custom service. Open `/modules/custom/example/example.services.yml`. This is the file that defines your module's services. Observe our `example.tax_calc` service specifies that it uses the class `Drupal\example\ExampleTaxCalc`. This class can be found in `/modules/custom/example/src/ExampleTaxCalc.php`, open that file now.

3. Let's create a method that actually does something! Add the following code to the `ExampleTaxCalc` class:

    ```php
    public function calculateCaliforniaSalesTax($amount) {
      return 1.0725 * $amount;
    }
    ```

[Next Exercise (#5 Events)](exercise_05-events.md)
