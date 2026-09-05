---
image: https://api.imageee.com/bold?text=PHP%20Scraper:%20Devolviendo%20la%20simplicidad%20al%20scraping%20y%20al%20crawling&bg_image=https://images.unsplash.com/photo-1542762933-ab3502717ce7
description: "PHPScraper es una librería PHP gratuita y de código abierto para hacer web scraping y crawling de sitios web. Extrae enlaces, imágenes, meta tags, palabras clave y mucho más con una API simple y encadenable."
---

<center>PHP Scraper: Devolviendo la simplicidad al scraping y al crawling</center>
===================================================

<p align="center">
  <img
    alt="PHP Scraper: Devolviendo la simplicidad al scraping y al crawling"
    src="/logo-light.png"
  />
  <p align="center">
    <a href="https://github.com/spekulatius/PHPScraper/actions/workflows/test.yaml">
      <img src="https://github.com/spekulatius/PHPScraper/actions/workflows/test.yaml/badge.svg" alt="Unit Tests">
    </a>
    <a href="https://packagist.org/packages/spekulatius/PHPScraper">
      <img src="https://poser.pugx.org/spekulatius/PHPScraper/d/total.svg" alt="Total Downloads">
    </a>
    <a href="https://packagist.org/packages/spekulatius/PHPScraper">
      <img src="https://poser.pugx.org/spekulatius/PHPScraper/v/stable.svg" alt="Latest Version">
    </a>
    <a href="https://packagist.org/packages/spekulatius/PHPScraper">
      <img src="https://poser.pugx.org/spekulatius/PHPScraper/license.svg" alt="License">
    </a>
  </p>
  <p align="center">
    <b>de <a href="https://peterthaleikis.com?src=phpscraper">Peter Thaleikis</a></b>
  </p>
</p>

El raspado de la web usando PHP puede hacerse más fácilmente. Esta es una envoltura de opinión alrededor de algunas grandes bibliotecas de PHP para hacer el acceso a la web más fácil.

Los ejemplos cuentan la historia mucho mejor. Echa un vistazo.

::: tip Nota
Este sitio web de documentación en español es WIP. Por favor, eleve un PR en GitHub si encuentra algún error. Gracias!
:::


La idea 💡️
----------

Acceder a sitios web y recoger información básica de la web es demasiado complejo. Esta envoltura alrededor de [BrowserKit](https://symfony.com/doc/current/components/browser_kit.html) (antes [Goutte](https://github.com/FriendsOfPHP/Goutte)) lo hace más fácil. Te ahorra el uso de XPath y demás, dándote acceso directo a todo lo que necesitas. Web scraping con PHP reimaginado.


Apoyos 💪️
-------------

Este proyecto está patrocinado por:

<a href="https://bringyourownideas.com" target="_blank" rel="noopener noreferrer"><img src="https://bringyourownideas.com/images/byoi-logo.jpg" height="100px"></a>

¿Quieres patrocinar este proyecto? [Escríbeme](https://peterthaleikis.com/contact).


Ejemplos
--------

Aquí hay algunos ejemplos de lo que la biblioteca de raspado web puede hacer en este momento:

### Scrape Meta Information:

```php
$web = new \Spekulatius\PHPScraper\PHPScraper;

/**
 * Navegue hasta la página de pruebas. Contiene:
 *
 * <meta name="author" content="Lorem ipsum" />
 * <meta name="keywords" content="Lorem,ipsum,dolor" />
 * <meta name="description" content="Lorem ipsum dolor etc." />
 * <meta name="image" content="https://test-pages.phpscraper.de/assets/cat.jpg" />
 */
$web->go('https://test-pages.phpscraper.de/meta/lorem-ipsum.html');

// Obtener la información:
echo $web->author;          // "Lorem ipsum"
echo $web->description;     // "Lorem ipsum dolor etc."
echo $web->image;           // "https://test-pages.phpscraper.de/assets/cat.jpg"
```

La mayor parte de la información se puede acceder directamente, ya sea como cadena o como matriz.


### Raspado de contenidos, como imágenes:

```php
$web = new \Spekulatius\PHPScraper\PHPScraper;

/**
 * Navegue hasta la página de prueba. Esta página contiene dos imágenes:
 *
 * <img src="https://test-pages.phpscraper.de/assets/cat.jpg" alt="absolute path">
 * <img src="/assets/cat.jpg" alt="relative path">
 */
$web->go('https://test-pages.phpscraper.de/meta/lorem-ipsum.html');

var_dump($web->imagesWithDetails);
/**
 * [
 *     'url' => 'https://test-pages.phpscraper.de/assets/cat.jpg',
 *     'alt' => 'absolute path',
 *     'width' => null,
 *     'height' => null,
 * ],
 * [
 *     'url' => 'https://test-pages.phpscraper.de/assets/cat.jpg',
 *     'alt' => 'relative path',
 *     'width' => null,
 *     'height' => null,
 * ]
 */
```

Alguna información *opcionalmente* se devuelve como un array con detalles. Para este ejemplo, una simple lista de imágenes está disponible usando `$web->images` también. Esto debería facilitar el raspado de la web.

Se puede encontrar más código de ejemplo en los ejemplos y pruebas.


Instalación
------------

La instalación suele realizarse mediante [Composer](https://getcomposer.org).

### Instalación con Composer

```bash
composer require spekulatius/phpscraper
```

Una vez completada la instalación, el paquete será recogido por el autocargador de Composer. En las aplicaciones y frameworks típicos de PHP como Laravel o Symfony ya puedes empezar a hacer scraping. Ahora puedes usar cualquiera de los ejemplos anotados o los ejemplos en la carpeta `tests/`.

### Uso en proyectos VanillaPHP

Si estás construyendo un proyecto VanillaPHP, necesitarás incluir el autoloader en tu script en la parte superior de tu script PHP:

```php
require 'vendor/autoload.php';
```

Si estás usando un framework como Laravel, Symfony, Laminas, Phalcon o CakePHP, no necesitarás este paso. El autoloader se incluye automáticamente.


Configuración
-------------

La configuración adicional es opcional. A continuación se muestran las opciones correctamente disponibles.

### Soporte de Proxy

Si necesita proxies, puede configurar el soporte de proxy con `setConfig`:

```php
$web->setConfig(['proxy' => 'http://user:password@127.0.0.1:3128']);
```

### Timeout

Puedes establecer el `timeout` usando `setConfig`:

```php
$web->setConfig(['timeout' => 15]);
```

Si se pone el tiempo de espera a cero, se desactivará.

### Desactivación de SSL

Aunque no se recomienda, puede ser necesario desactivar las comprobaciones de SSL. Puede hacerlo utilizando:

```php
$web->setConfig(['disable_ssl' => true]);
```

Puedes llamar a `setConfig` varias veces. Almacena la configuración y la fusiona con los ajustes anteriores. Esto debe tenerse en cuenta en el improbable caso de uso cuando se desestablecen los valores.


¿Has encontrado un error y lo has arreglado? ¡Impresionante!
----------------------------------
Antes de empezar, familiarícese con las [directrices de contribución](/contributing.html). Si tiene alguna pregunta, no dude en ponerse en contacto con nosotros.


Pruebas: Asegurarse de que funciona.
----------------------------

El código está cubierto a grandes rasgos con pruebas de extremo a extremo. Para ello, se alojan páginas web sencillas en *https://test-pages.phpscraper.de/*, cargado y analizado usando [PHPUnit](https://phpunit.de/). Estas pruebas también son adecuadas como ejemplos - véase `tests/`!

Dicho esto, es probable que haya casos límite que no funcionen y puedan causar problemas. Si encuentras uno, por favor, levanta un bug en GitHub.
