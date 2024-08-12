Si el campo de texto de ACF contiene un shortcode y deseas que se ejecute y muestre su contenido en lugar de simplemente mostrar el texto del shortcode, puedes utilizar la función `do_shortcode()` en WordPress. Aquí te muestro cómo hacerlo:

### 1. Usar `get_field()` y `do_shortcode()`
Cuando recuperes el valor del campo de texto que contiene el shortcode, debes pasar ese valor a través de `do_shortcode()` para que se ejecute y muestre el resultado del shortcode.

### Ejemplo de Código
Supongamos que el nombre del campo en ACF es `mi_shortcode`. El código que usarías en tu plantilla sería algo como esto:

```php
<?php
if( function_exists('get_field') ) {
    // Recuperar el valor del campo
    $mi_shortcode = get_field('mi_shortcode');

    // Comprobar si el campo tiene un valor
    if( $mi_shortcode ) {
        // Ejecutar el shortcode y mostrar su contenido
        echo do_shortcode($mi_shortcode);
    }
}
?>
```

### Explicación
- **`get_field('mi_shortcode')`**: Recupera el contenido del campo ACF.
- **`do_shortcode($mi_shortcode)`**: Procesa el contenido como un shortcode, ejecutándolo y mostrando el resultado en lugar de simplemente mostrar el texto del shortcode.

### 2. Guardar y Visualizar
Guarda el archivo de plantilla después de agregar el código y visualiza la página en tu sitio web. Ahora, en lugar de mostrar el shortcode como texto, debería ejecutarse y mostrar el contenido que genera.

### Ejemplo Práctico
Si el campo ACF `mi_shortcode` contiene un shortcode como `[gallery id="123"]`, al usar el código anterior, se mostrará la galería en la página en lugar de mostrar `[gallery id="123"]` como texto.

Este enfoque es ideal para cuando necesitas integrar contenido dinámico generado por shortcodes en tus páginas utilizando campos personalizados de ACF.