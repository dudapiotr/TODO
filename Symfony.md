## Doctrine 2
### Generowanie Entities

```php
//Import xml
php app/console doctrine:mapping:import --force TestBundle xml

//Generowanie entity pojedynczo (z adnotacjami) - opcja filter
php app/console doctrine:mapping:convert annotation ./src --filter Report

//Generowanie getterów i setterów
php app/console doctrine:generate:entities TestBundle
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
        

