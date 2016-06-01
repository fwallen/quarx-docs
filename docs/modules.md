# Modules

Quarx comes with a handful of prebuilt modules for handling a basic application including Images, Files, Blog, Pages, Faqs, etc. Below you will find a full listing of the modules that come prepackaged with Quarx.

Pre-packaged Modules
------
* Blog
* Pages
* Menus
* Widgets
* Faqs
* Images
* Files
* Events

Images and Files:
------
The images and files modules are somewhat special in that they can be used inside the other modules or any module which would have a text column for something like details. Simply set the textarea to have the class `redactor` and your custom module will be able to insert images and downloadable file links inside the text area. To better understand take a look the `yab/quarx/src/Config/forms.php` file and see how the columns are defined for the blog and pages entries. Quarx uses Laracogs formMaker tools to make form building considerably easier and faster.

Images and files are available in the WYSIWYG toolbar which appears above textareas that have the class redactor added to them.