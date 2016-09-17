鹊桥
====



DIRECTORY STRUCTURE
-------------------

```
common
    config/              contains shared configurations
    mail/                contains view files for e-mails
    models/              contains model classes used in both backend and frontend
console
    config/              contains console configurations
    controllers/         contains console controllers (commands)
    migrations/          contains database migrations
    models/              contains console-specific model classes
    runtime/             contains files generated during runtime
backend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains backend configurations
    controllers/         contains Web controller classes
    models/              contains backend-specific model classes
    runtime/             contains files generated during runtime
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
frontend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains frontend configurations
    controllers/         contains Web controller classes
    models/              contains frontend-specific model classes
    runtime/             contains files generated during runtime
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
    widgets/             contains frontend widgets
vendor/                  contains dependent 3rd-party packages
environments/            contains environment-based overrides
tests                    contains various tests for the advanced application
    codeception/         contains tests developed with Codeception PHP Testing Framework
```
NGINX CONFIG 
-------------

```
    location ~ \.php$ {
        root            /home/users/yourname/webroot;
        fastcgi_pass    $php_upstream;
        fastcgi_index   index.php;
        include         fastcgi.conf;
    }

    location / {
        root /home/users/yourname/webroot;
        index index.php;
        fastcgi_pass    $php_upstream;
        include         fastcgi.conf;
       # rewrite ^/([^/.]*)(/[^\?]*)?((\?.*)?)$ /$1/index.php$2$3 break;
        if (!-e $request_filename){
            rewrite ^/(.*) /index.php last;
        }
    }

    location ~ \.js$ {
        root             /home/users/yourname/webroot;
    }

    location ~ ^/(.*)/(favicon.ico|static|css|assert|upload) {
         root            /home/users/yourname/webroot;
    }

```
