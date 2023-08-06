# Departamentos de Paraguay
Para que aparezcan los departamentos de Paraguay al agregar una dirección de entrega o de pago de un pedido, es necesario parchear la librería addressing, estos datos ya fueron agregados en la version [2.0.1](https://github.com/commerceguys/addressing/blob/v2.0.1/resources/subdivision/PY.json), pero aún no ha sido integrado por el módulo [address](https://www.drupal.org/project/address) que es una dependencia de commerce core.
# Requerimientos
Ejecutar en la terminal.
```javascript
composer require cweagans/composer-patches --dev
composer require symplify/vendor-patches --dev
```
# Pasos
Crea una carpeta "patches" en el directorio raiz y copia los archivos (PY.JSON y commerceguys-addressing-src-addressformat-addressformatrepository-php.patch) luego agrega en el archivo composer.json lo siguiente:
1. Sección "scripts" en caso de ejecutar actualizaciones vuelve a copiar datos de subdivisón en la librería.
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
