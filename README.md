Yii 2 raamistiku laiendus DGS API kasutamiseks
==============================================

API dokumentatsioon
-------------------
https://www.ra.ee/dgs-api/doc/index

Eelistatud paigaldus
--------------------

Eelistatud paigaldusviis on **composeri** kaudu.

Lisa rakenduse **composer.json** faili paketi nimi ja versioon:

```json
"require": {
    "rahvusarhiiv/dgsapi": "dev-main"
}
```

ja githubi repositoorium:

```json
"repositories": [
    {
        "type": "vcs",
        "url": "https://github.com/erikuus/yii2-dgsapi-extension"
    }
]
```

Seejärel jooksuta terminalis käsku

```shell
composer update
```

Alternatiivne paigaldus
-----------------------

Laadi kõik laienduse failid Githubist alla ja paigalda rakenduse **vendor/rahvusarhiiv/dgsapi/** kausta.

Lisa faili **vendor/yiisoft/extensions.php** järgmised read:

```php
'rahvusarhiiv/dgsapi' => [
    'name' => 'rahvusarhiiv/dgsapi',
    'version' => 'dev-main',
    'alias' => [
        '@rahvusarhiiv/dgsapi' => $vendorDir . '/rahvusarhiiv/dgsapi',
    ],
],
```

Seadistus
---------
Lisa konfiguratsioonifailis komponentide hulka **rahvusarhiiv\dgsapi\DgsApi**:

```php
'dgsapi' => [
    'class' => 'rahvusarhiiv\dgsapi\DgsApi',
    'url' => 'https://www.ra.ee/dgs-api/api/v1/dip/'
]
```

Kasutamine
----------
```php
$response = Yii::$app->dgsapi->request('get-file-path', [
    'uid' => 'b1bc1876-d34b-57d1-a7a5-7563ef53333b'
]);
