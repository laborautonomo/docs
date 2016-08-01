- Download the framework
- Unzip the package.
- Upload the framework files to your server. Normally the index.php file will be at your root.
- Open the index.php file with a text editor and set your base URL and database credentials (if a database is needed). Set the default theme and controller to be loaded.
- If using a Linux server edit .htaccess file and save the base path.

The first setting sets the timezone

```php
date_default_timezone_set('Europe/London');
```

Next set the application web URL and document root, the document root shouldn't need to be changed.

Once the DIR is set it can be used to get the application address.

```php
define('DIR','http://example.com/');
define('DOCROOT', dirname(__FILE__));
```

If using a database the database settings will need altering:

```php
define('DB_TYPE','mysql');
define('DB_HOST','localhost');
define('DB_NAME','database name');
define('DB_USER','root');
define('DB_PASS','root');
define('PREFIX','smvcf_');
```

The prefix is optional but highly recommended, its very useful when sharing databases with other applications, to avoid conflicts. The prefix should be the starting patten of all table names like smvcf_users

The framework provided a session helper class in order to avoid session conflicts a prefix is used.

```php
define('SESSION_PREFIX','smvcf_');
```

The framework needs a class to be set as a default this class is to be used when the application url is accessed. Additionally the theme can be changed by setting the template.


```php
$app->setController('welcome');
$app->setTemplate('default');
```
