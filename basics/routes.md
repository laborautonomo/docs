Routing lets you create your own url paths, based on the path you can load a closure or a controller!

Routing is build into the v2.1 nothing needs to be called in order to use a route, you only need to create your route in index.php

<b>Routing Setup</b>
Namespace's are included into all classes now, a namespace is kind of like a layer. Adding a namespace to a class means their can be multiple classes with the same name as long as each is in a different namespace.
With routes the namespace is \Core\Router:: followed by the method call typing out the namespace every time is long winded, thankfully they shortcuts can be created by creating an alias:

```php
use core\router as Router;
```

By using the use keyword \core\router can be references as Router.

To define a route call the static name Route:: followed by either a post or get ('any' can also be used to match both post and get requests) to match the HTTP action. Next set the path to match and what do, call a closure or a controller.

```php
Router::any('', 'closure or controller');
```

<b>Closures</b>

A closure is a function without a name, they are useful when you only need simple logic for a route, to use a closure first call Route:: then set the url pattern you want to match against followed by a function

```php
Router::get('simple', function(){
  //do something simple
});
```

Controllers and model can be used in a closure by instantiating the root controller

```php
$c = new core\controller();
$m = new models\users();

$m->get_users();
```

Having said that it's better to use a controller once you need access to a model.


Closures are convenient but can soon become messy.

<b>Controllers</b>

To call a route to a controller instead of typing a function instead enter a string. In the string type the namespace of the controller (\controller if located in the root of the controllers folder) then the controller name, finally specify what method of that class to load. They are dictated by a @ symbol.

Say I have a controller called users (in the root of the controllers folder) and I want to load a userslist function:
```php
Route::get('users','\controllers\users@userslist');
```

The above would call the users controllers and the userlist method when /users is in the url via a get request.

Routes can respond to both GET and POST requests
To use a post route:
```php
Router::post('blogsave', '\controllers\blog@savepost');
```

To respond to either a post or get request use any:
```php
Router::any('blogsave', '\controllers\blog@savepost');
```

<b>Routing Filters</b>

Routes can use filters to dynamically pass values to the controller / closures, their are 3 filters:

- any - can use characters or numbers
- num - can only use numbers
- all - will accept everything including any slash paths

To use a filter place the filter inside parenthesis and use a colon inside route path

```php
Router::get('blog/(:any)', '\controllers\blog@post');
```

Would get past to app/controllers/blog.php anything after blog/ will be passed to post method.

```php
public function post($slug){
```

If there is no route defined, you can call a custom callback, like:
```php
Router::error('\core\error@index');
```

Finally to run the routes:
```php
Router::dispatch();
```

# Full Example
```php
use core\router as Router;

//define routes
Router::get('', '\controllers\welcome@index');

//call a controller in called users inside a admin folder inside the controllers folder
Router::('admin/users','\controllers\admin\users@list');

//if no route found
Router::error('error@index');

//execute matched routes
Router::dispatch();
```

# Legacy Calls

To call controllers and methods by their name and not a custom route can be done by calling the controller file name followed by the method. Any params are passed as keys to an array so only one param is used.

For instance to call the welcome controller and a method called custom enter the url http://example.com/welcome/custom.

To load the index method: http://example.com/welcome the /index is not needed, it would be called automatically.
