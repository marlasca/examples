# Cambiar machine_name de un field de un Content type
Atención: se va a modificar un content type, por lo que perderemos los datos.

```
//Export content type
vendor/drupal/console/bin/drupal config:export:content:type module_name

cd /modules/module_name/config/optional

//Replace machine_name in all the files
find ./ -type f -exec sed -i 's/mn_old/mn_new/g' {} \;

//Replace machine_name in all the files names
rename 's/mn_old/mn_new/' *

//In the drupal portal, Extend -> Uninstall module (if it is installed) and Import again.
```
