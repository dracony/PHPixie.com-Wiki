# Change default structure to your own

Hello! You can change dirs very simple.
___
Structure will be:

index.php

.htaccess

composer.json

app

-->assets

-->-->config

-->-->views


-->classes

-->-->App

-->-->-->Controller

-->-->-->Model

-->-->-->Page.php

-->-->-->Pixie.php

core (vendor dir)
___
Let's start:

1. composer.json: add this after "require" block:

```
"config": {
    		"vendor-dir" : "core/"
		}
```

2. classes/Pixie.php in `after_bootstrap()`:

```
$this->assets_dirs = array();
$this->assets_dir[] = $this->pixie->root_dir.'app/assets';
```

3. web/index.php: change third and fourth lines:

```
$loader = require $root.'/core/autoload.php';
$loader->add('', $root.'/app/classes/');
```

4. .htaccess: replace all content to these lines:

```
RewriteEngine On
RewriteBase / #May be, you need to comment this line, google it!
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule .* index.php?$0 [NC,L]
```

5. Now change dirs:

```
/web/index.php => index.php
/assets and /classes => /app/assets and /app/classes
/vendor => /core
```

Posted by [Max Nixischev](https://github.com/agmanix/). Thanks [dracony](https://github.com/dracony) for explanation
