---
layout: default
language: 'es-es'
version: '4.0'
title: 'Estándar de codificación'
keywords: 'coding standard, zephir'
---

# Estándar de Código de Phalcon

* * *

![](/assets/images/document-status-stable-success.svg) ![](/assets/images/version-{{ page.version }}.svg)

Última actualización: 04-07-2019

Phalcon está escrito en [Zephir](https://zephir-lang.com), un lenguaje creado por el equipo de Phalcon y que se encuentra en continuo desarrollo. Por ello, aunque los desarrolladores quisieran seguirlo, no hay todavía ningún estándar de código establecido.

En este documento se describe el estándar de código que utiliza Phalcon para editar archivos de Zephir. El estándar de código es una variante de [PSR-12](https://www.php-fig.org/psr/psr-12/) desarrollada por [PHP-FIG](https://www.php-fig.org/)

## Archivos

- Los archivos deben usar solo UTF-8 sin [BOM (marca de orden de bytes)](https://es.wikipedia.org/wiki/Marca_de_orden_de_bytes).
- Los nombres de los archivos deben estar en formato [StudlyCaps](https://en.wikipedia.org/wiki/Studly_caps).
- Todos los archivos deben usar el final de línea de Unix LF (linefeed).
- Todos los archivos deben terminar con una única línea en blanco.
- Los nombres de las carpetas también deben estar en formato StudlyCaps y el árbol de carpeta/subcarpeta debe seguir el espacio de nombres (namespace) de la clase.

```php
phalcon/Acl/Adapter/Memory.zep
```

```php
namespace Phalcon\Acl\Adapter;

use Phalcon\Acl\Adapter;

class Memory extends Adapter
{

}
```

- El código debe utilizar 4 espacios para la sangría, no tabulaciones.
- Las líneas deben tener como máximo 80 caracteres. El límite de la longitud de línea es de 120 caracteres.
- There must be one blank line after the namespace declaration, and there must be one blank line after the block of use declarations.
- There must not be trailing whitespace at the end of non-blank lines.
- Blank lines may be added to improve readability and to indicate related blocks of code.
- There must not be more than one statement per line.

## Clases

- Class names must be declared in StudlyCaps.
- Opening braces for classes must go on the next line, and closing braces must go on the next line after the body.
- Abstract classes must be prefixed by `Abstract`
- Interfaces must be suffixed by `Interface`

### Constantes

- Class constants must be declared in all upper case with underscore separators.
- Class constants must appear at the top of the class.
- Class constants must be sorted alphabetically by constant name.

```php
namespace Phalcon\Acl;

class Enum
{
    const ALLOW = 1;
    const DENY  = 0;
}
```

### Propiedades

- Class properties must be declared in camelCase.
- Class properties must be sorted alphabetically based on name.
- Whenever possible, properties must have a default value.
- Whenever possible, properties must have a docblock that defines their type with the `@var` declaration.
- Properties must not be prefixed with underscore `_`. The only exception is if the property name is a reserved keyword such as `default`, `namespace` etc.

```php
namespace Phalcon\Acl\Adapter;

use Phalcon\Acl\Adapter;

class Memory extends Adapter
{
    /**
     * Returns latest key used to acquire access
     *
     * @var string | null
     */
    protected activeKey = "" { get };
}
```

### Métodos

- Method names must be declared in camelCase.
- Methods must be sorted alphabetically and based on their visibility. The order is `public`, `protected` and `private`. `__construct` if defined must be at the top of the class.
- Method names must not be prefixed with underscore `_`.
- All methods must have a return type. If the method does not return anything it should be marked `void`
- Opening braces for methods must go on the next line, and closing braces must go on the next line after the body.
- Visibility must be declared on all properties and methods; `abstract` and `final` must be declared before the visibility; `static` must be declared after the visibility.

```php
abstract public function getElement() -> var;

final public function getElement() -> var;

public static function getElement() -> var;
```

- Control structure keywords must have one space after them; method and function calls must not.
- Opening braces for control structures must go on the same line, and closing braces must go on the next line after the body.
- Control structures such as `if` must not have parentheses around the conditional, unless it is a complex one.

```php
if typeof variable === "array" {

}
```

### Method Arguments

- In the argument list, there must not be a space before each comma, and there must be one space after each comma.
- Each method must have its type declared before it
- Method arguments with default values must go at the end of the argument list.

```php
public function setElement(string! name, var value) -> void;
```

- Argument lists MAY be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list must be on the next line, and there must be only one argument per line.

### Archivos PHP

PHP files such as tests must follow [PSR-12](https://www.php-fig.org/psr/psr-12/).