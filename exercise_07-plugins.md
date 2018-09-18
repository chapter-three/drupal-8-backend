#### [Drupal 8 Backend Training](README.md)

# Exercise 7:

## Plugins

Plugins are Drupal 8's way of providing pluggable functionality. They let you create classes that follow a specified contract, making them swappable, which can then be used in various parts of the Drupal system. Some examples include drupal blocks, CKEditor plugins, and image formatters.

In this exercise we will use drupal console to generate a custom block.

1. Use Drupal console to generate a block plugin:

    ```bash
    Enter the module name [admin_toolbar]:
     > example

     Enter the plugin class name [DefaultBlock]:
     > HelloBlock

     Enter the plugin label [Hello block]:
     >

     Enter the plugin id [hello_block]:
     >

     Enter the theme region to render the Plugin Block. []:
     >

     Do you want to load services from the container? (yes/no) [no]:
     >


    You can add input fields to create special configurations in the block.
    This is optional, press enter to continue
     Do you want to generate a form structure? (yes/no) [yes]:
     > no

     Do you want proceed with the operation? (yes/no) [yes]:
     >

    ```

2. Open the file `modules/custom/example/src/Plugin/Block/HelloBlock.php`. Observe the comment above the class -- the code following `@Block` is called an annotation and is actual functional code that specifies the plugin id and other metadata (in this case admin label).

3. Edit the `build` method to include a nice greeting:

    ```php
    public function build() {
      $build = [];
      $build['hello_block']['#markup'] = 'yo.';

      return $build;
    }

    ```

4. Visit your local development site and go to `/admin/structure/block`, pick a region in your theme and place your new block.

5. Visit any page and view your new block!