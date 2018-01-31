## Doctrine 2

### Memcached
```php
echo 'flush_all' | nc localhost 11211
```

#### Dump różnic sql
```php
php app/console doctrine:schema:update --dump-sql
```

#### Generowanie Entities

```php
//Import xml
php app/console doctrine:mapping:import --force MainBundle xml

//Generowanie entity pojedynczo (z adnotacjami) - opcja filter
php app/console doctrine:mapping:convert annotation ./src --force

//Generowanie getterów i setterów
php app/console doctrine:generate:entities MainBundle
```

```php
php bin/console doctrine:mapping:convert annotation ./src/MainBundle/Resources/config/doctrine/metadata/orm --from-database --force

php bin/console doctrine:mapping:import MainBundle annotation

php bin/console doctrine:generate:entities MainBundle
```

#### Generowanie CRUD
```php
php app/console generate:doctrine:crud
php app/console generate:doctrine:crud --entity=AcmeBlogBundle:Post
```

## Debugowanie
```php
php app/console doctrine:schema:validate
```

## AUTH I ACL

### Sprawdzenie zalogowania
```php
$securityContext = $this->container->get('security.authorization_checker');
if ($securityContext->isGranted('IS_AUTHENTICATED_REMEMBERED')) {
  dbs('aa');
}else{
  dbs('bb');
}
```     

### Pobranie zalogowanego usera
```php
$user = $this->container->get('security.context')->getToken()->getUser();
$user->getId();
```

## VIEW LAYER
### $app
```php
//Klasa Symfony\Bundle\FrameworkBundle\Templating\GlobalVariables
public function getSecurity();
public function getUser();
public function getRequest();
public function getSession();
public function getEnvironment();
public function getDebug();

```
        

