# Departamentos de Paraguay
Agrega departamentos de Paraguay a la librería addressing en Drupal Commerce, ya agregado en la version [2.0.1](https://github.com/commerceguys/addressing/blob/v2.0.1/resources/subdivision/PY.json), ésta librería es incorporado por el módulo [address](https://www.drupal.org/project/address) que es una dependencia de commerce core pero aún con la versión 2.0 de addressing.
# Requerimientos
Ejecutar en la terminal.
```javascript
composer require cweagans/composer-patches --dev
composer require symplify/vendor-patches --dev
```
# Pasos
Crea una carpeta "patches" y copia los archivos (PY.JSON y commerceguys-addressing-src-addressformat-addressformatrepository-php.patch) adentro y agrega en el archivo composer.json lo siguiente:
1. Sección "scripts" en caso de actualizaciones para volver a copiar datos de subdivisón en la librería.
```javascript
"scripts": {
        "post-install-cmd": [
            "cp patches/PY.json vendor/commerceguys/addressing/resources/subdivision/"
        ],
        "post-update-cmd": [
            "cp patches/PY.json vendor/commerceguys/addressing/resources/subdivision/"
        ]
       },
```
 2. Sección "extra" para parchear la librería.
 ```javascript
 "extra": {
        "patches": {
            "commerceguys/addressing": [
                "patches/commerceguys-addressing-src-addressformat-addressformatrepository-php.patch"
            ]
        },
        "enable-patching": true,
        "composer-exit-on-patch-failure": true,
 ```
 3. Ejecutar.
```javascript
composer install
```
