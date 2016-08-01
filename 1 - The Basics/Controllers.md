Controllers are the bread and butter of the framework they control when a model is used and equally when to include a view for output. A controller is a class with methods these methods are the outputted pages when set as public or protected. Private methods are not treated as pages.

A method can be used for telling a view to show a page or outputting a data stream such as XML or a JSON array.  Put simply they are the logic behind your application.

Controllers are created inside the controllerâ??s folder. To create a controller, create a new file, the convention is to keep the filename in lowercase without any special characters or spaces.

The name of the class should use CamelCasing meaning the first letter of each word is a capital letter.

Controllers need to use the main Controller; they extend it, the syntax is

```php
class Welcome extends Controller {

}
```

Controllers will need to access methods and properties located in the parent controller (core/controller.php) in order to do this they need to call the parent constructor inside a construct method.

```php
public function __construct(){
   parent::__construct();
}
```

The construct method is called automatically when the controller is instantiated once called the controller can then call any property or method in the parent controller that is set as public or protected.

**The following properties are available to the controller**

- $_view / object to use view methods
- $loadModel / includes and instantiates a model
- $_url / holds the current page url


**Methods:**


- loadModel /loads a model, the model can be placed directly in the models folder or in a sub folder, the path to the model is passed directly. For example:
```php
public function index(){
    $this->loadModel('admin/admin_model');
}
```
- _getUrl / sets the page url


Controllers should have a public method called index this method is executed when the controller is called.

For instance the following would use a view, by calling the view property and calling its render method, pass in the path to the file inside the views folder.

```php
public function index(){
    $this->_view->render('welcome/welcome');
}
```

A controller can have many methods, a method can call another method, all standard OOP behaviour is honoured.

Data can be passed from a controller to a view by passing an array to the view.

The array can be made up from keys. Each key can hold a single value or another array.

The array must be passed to the method for it to be used inside the view page or in a template (covered in the templates section)

```php
$data['title'] = 'My Page Title';
$data['content'] = 'The contact for the page';
$data['users'] = array('Dave','Kerry','John');

$this->_view->render('contacts',$data);
```

Using a model is very similar, an array holds the results from the model, the model calls a method inside the model.

```php
$contacts = $this->loadModel('contacts_model');
$data['contacts'] = $contacts->getContacts();
```
