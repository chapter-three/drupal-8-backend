#### [Drupal 8 Backend Training](README.md)

# Exercise 4:

## Creating a custom service.

You may be aware that Drupal has undergone a sea change in it's transition from 7 to 8. In addition to (almost) fully adopting an object oriented approach, Drupal 8 draws heavily from external frameworks and libraries. The most significant cornerstone of our new version of Drupal is the Symfony framework, a service oriented full stack php framework. Drupal 8 draws heavily from Symfony, using it for request and response handling, routes and controllers, and, you guessed it, for services and the service container.

What is a service container? A service container is basically just a global object that you can use to retrieve services.

What are services? Services are essentially just useful chunks of code that might be reused throughout your site. For example some services provided by core include `logger.factory` which you can use to create log entries (essentially replaces watchdog from d7), and `messenger` which you can use instead of `drupal_set_message`. Pulling these services from the service container allows Drupal to handle dependency management and to ensure that only services being used are actually instantiated, leading to a cleaner more organized codebase, and lower memory requirements than procedural php.

