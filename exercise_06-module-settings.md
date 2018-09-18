## Module Settings

With Drupal console, you can create module settings forms and design values to be stored in config through the interactive command line interface. The generate command is `generate:form:config`.

![Generate Module Settings Form](https://user-images.githubusercontent.com/159693/45673815-8add4e00-bae0-11e8-84fd-9e214dd327c3.png)

This command will generate the routing file, the form file and the default config file for your settings form. Notice `_form: '\Drupal\example\Form\ExampleConfigForm'` under defaults for the route. This tells drupal to load the form via the form controller.

Go to `/admin/config/example/exampleconfig` To see and edit the config.

![Config Form](https://user-images.githubusercontent.com/159693/45674699-7c903180-bae2-11e8-80b5-eadd1bd43c9f.png)

#### Cheat Sheet:

```
➜  example_site vendor/bin/drupal generate:form:config

 // Welcome to the Drupal Form Config generator
 Enter the module name [module_filter]:
 > example

 Enter the Form Class name [DefaultForm]:
 > ExampleConfigForm

 Enter the Form id [example_config_form]:
 > 

 Do you want to load services from the container? (yes/no) [no]:
 > 

 Do you want to generate a config file? (yes/no) [yes]:
 > 

 Do you want to generate a form structure? (yes/no) [yes]:
 > 

Available types: button, checkbox, checkboxes, color, date, datelist, datetime, email, entity_autocomplete, field_ui_table, fieldset, file, hidden, image_button, item, language_select, machine_name, managed_file, number, password, password_confirm, path, radio, radios, range, search, select, submit, table, tableselect, tel, text_format, textarea, textfield, token, url, value, weight

 Enter a new field properties

 New field type (press <return> to stop adding fields) []:
 > number

 Input label:
 > Cache Lifetime

 Input machine name [cache_lifetime]:
 > 

 Description []:
 > How long to cache the listing.               

 Default value []:
 > 300

 Weight for input item [0]:
 > 


 Enter a new field properties

 New field type (press <return> to stop adding fields) []:
 > textfield

 Input label:
 > List Name

 Input machine name [list_name]:
 > 

 Maximum amount of characters [64]:
 > 

 Width of the textfield (in characters) [64]:
 > 

 Description []:
 > The name of the list

 Default value []:
 > 

 Weight for input item [0]:
 > 

 Enter a new field properties

 New field type (press <return> to stop adding fields) []:
 > 

 Enter the route path [/admin/config/example/exampleconfig]:
 > 

 Generate a menu link (yes/no) [yes]:
 > 

 A title for the menu link [ExampleConfigForm]:
 > Example Config

 Menu parent [system.admin_config_system]:
 > 

 A description for the menu link [A description for the menu entry]:
 > Configuration for the example module.
```
