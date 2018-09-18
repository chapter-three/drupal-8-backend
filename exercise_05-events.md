#### [Drupal 8 Backend Training](README.md)

# Exercise 5:

## Events

A Drupal 8 Event is very similar to hooks in both Drupal 7 and Drupal 8. It's basically a method of allowing developers to respond to certain occurences within the Drupal execution flow. In this exercise we'll demonstrate the concept of events by hiding the route we created in Exercise 3, but first a disclaimer: This is a purely didactic example, it is only intended to demonstrate how Events are used and is not a good way to handle route accessibility.

1. To start let's use our trusty Drupal Console to generate an Event listener:

    ```bash
    lando drupal generate:event:subscriber
    ```

    ```bash
     Enter the module name [admin_toolbar]:
     > example

     Enter the service name [example.default]:
     > example.hide_route

     Enter the class name [DefaultSubscriber]:
     > HideRouteSubscriber


    Type the event name or use keyup or keydown.
    This is optional, press enter to continue

     Enter event name []:
     > kernel.request

     Enter the callback function name to handle event [kernel_request]:
     > handleRequest

     Enter event name []:
     >

     Do you want to load services from the container? (yes/no) [no]:
     > yes


    Type the service name or use keyup or keydown.
    This is optional, press enter to continue

     Enter your service []:
     > current_route_match
     Enter your service []:
     >

     Do you want proceed with the operation? (yes/no) [yes]:
     >
    ```

2. Open `/modules/custom/example/example.services.yml` and notice that there's a new service with the service name specified above, and with a special tag specifiying that it's an event subscriber.

3. Go to your dev site and visit `/example/site-name` and verify that it's working.

4. Edit `/modules/custom/example/src/EventSubscriber/HideRouteSubscriber.php` and edit the handleRequest method to mirror the following:

    ```php
    public function handleRequest(Event $event) {
      if ($this->currentRouteMatch->getRouteName() === 'example.example_controller_getSiteName') {
        throw new \Symfony\Component\HttpKernel\Exception\NotFoundHttpException();
      }
    }

    ```

5. Refresh the page and verify that you now get a 404 error.


[Next Exercise (#6 Module Settings)](exercise_06-module-settings.md)
