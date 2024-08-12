Cuando el campo ACF es de tipo "Objeto de publicación" (o "Post Object" en inglés), el valor que obtienes puede ser un objeto completo de la publicación o simplemente el ID de la publicación, dependiendo de cómo lo manejes. Para tu caso, donde necesitas el ID de la publicación para generar un shortcode, puedes hacerlo de la siguiente manera:

### Código para Construir y Ejecutar el Shortcode con Objeto de Publicación

```php
<?php
if( function_exists('get_field') ) {
    // Recuperar el objeto de la publicación desde el campo ACF
    $producto = get_field('campo-donde-se-almacena-dato');

    // Verificar si el campo tiene un valor y que sea un objeto de publicación
    if( $producto ) {
        // Obtener el ID de la publicación (producto en WooCommerce)
        $id_producto = $producto->ID;

        // Construir el shortcode usando el ID del producto obtenido
        $shortcode = '[wcpbc_product_price id="' . esc_attr($id_producto) . '"]';

        // Ejecutar el shortcode y mostrar su contenido
        echo do_shortcode($shortcode);
    }
}
?>
```

### Explicación del Código

1. **`get_field('campo-donde-se-almacena-dato')`**: Recupera el objeto de publicación completo que está seleccionado en el campo ACF de tipo "Objeto de publicación".
2. **`$producto->ID`**: Extrae el ID de la publicación desde el objeto `$producto`.
3. **`esc_attr($id_producto)`**: Escapa el ID del producto para evitar posibles problemas de seguridad.
4. **`$shortcode = '[wcpbc_product_price id="' . esc_attr($id_producto) . '"]'`**: Construye el shortcode colocando el ID dentro de las comillas.
5. **`do_shortcode($shortcode)`**: Procesa y ejecuta el shortcode para mostrar el precio del producto en la página.

### Instrucciones Adicionales

- **Configuración del campo ACF**: Asegúrate de que el campo `campo-donde-se-almacena-dato` esté configurado como "Objeto de publicación" y esté relacionado con productos de WooCommerce.
- **Objeto de publicación**: Si recuperas un objeto completo, siempre debes acceder al ID a través de `$producto->ID`.

### Ejemplo Práctico
Si seleccionas un producto con ID `123` en el campo ACF, el código construirá y ejecutará el siguiente shortcode:

```php
[wcpbc_product_price id="123"]
```

Este código mostrará el precio del producto con ID `123` en la página.

Este enfoque te permite utilizar la flexibilidad del campo "Objeto de publicación" en ACF para seleccionar productos y automáticamente generar el shortcode necesario para mostrar el precio del producto seleccionado en tu página de WordPress.