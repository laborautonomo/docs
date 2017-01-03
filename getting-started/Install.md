The framework is now on packagist <a href='https://packagist.org/packages/simple-mvc-framework/v2'>https://packagist.org/packages/simple-mvc-framework/v2</a>

Install from terminal now by using:

```php
composer create-project simple-mvc-framework/v2 foldername -s dev
```

The foldername is the desired folder to be created.

If you use Sublime you can also use the fetch package to download the framework from within Sublime Text <a href='http://code.tutsplus.com/articles/introducing-nettuts-fetch--net-23490'>http://code.tutsplus.com/articles/introducing-nettuts-fetch--net-23490</a>

- Download the framework
- Unzip the package.
- To run composer, navigate to your project on a terminal/command prompt then run 'composer install' that will update the vendor folder. Or use the vendor folder as is (composer is not required for this step)
- Upload the framework files to your server. Normally the index.php file will be at your root.
- Open the index.php file with a text editor, setup your routes.
- Open core/config.example.php and set your base URL and database credentials (if a database is needed). Set the default theme. Rename file to config.php
- Edit .htaccess file and save the base path. (if the framework is installed in a folder the base path should reflect the folder path /path/to/folder/ otherwise a single / will do.
