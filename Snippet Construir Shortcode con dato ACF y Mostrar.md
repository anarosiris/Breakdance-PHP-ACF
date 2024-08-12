Para lograr lo que describes, donde el campo `shortcode_precio_woocommerce` de ACF contiene un número y deseas construir un shortcode como `[wcpbc_product_price id=""]` colocando el número dentro de las comillas, puedes hacer lo siguiente:

### Código para Construir y Ejecutar el Shortcode

```php
<?php
if( function_exists('get_field') ) {
    // Recuperar el valor del campo ACF
    $id_producto = get_field('shortcode_precio_woocommerce');

    // Comprobar si el campo tiene un valor (es decir, un número)
    if( $id_producto ) {
        // Construir el shortcode usando el número obtenido
        $shortcode = '[wcpbc_product_price id="' . esc_attr($id_producto) . '"]';

        // Ejecutar el shortcode y mostrar su contenido
        echo do_shortcode($shortcode);
    }
}
?>
```

### Explicación del Código

1. **`get_field('shortcode_precio_woocommerce')`**: Obtiene el valor del campo ACF que contiene el número (ID del producto).
2. **`esc_attr($id_producto)`**: Escapa el número para asegurarse de que no haya caracteres no deseados o peligrosos (buena práctica de seguridad).
3. **`$shortcode = '[wcpbc_product_price id="' . esc_attr($id_producto) . '"]'`**: Construye el shortcode colocando el ID dentro de las comillas.
4. **`do_shortcode($shortcode)`**: Procesa el shortcode y muestra el precio del producto.

### Ejemplo en un Contexto Práctico
Si el campo `shortcode_precio_woocommerce` contiene el número `123`, el código construirá y ejecutará el siguiente shortcode:

```php
[wcpbc_product_price id="123"]
```

Esto mostrará el precio del producto con ID `123` en la página.

### Instrucciones Adicionales
- **Asegúrate de que el campo ACF esté correctamente configurado**: El campo `shortcode_precio_woocommerce` debe ser de tipo "Número" para que siempre devuelva un valor numérico.
- **Pruebas**: Es buena idea probar este código en una página específica primero antes de implementarlo en una plantilla más general, para asegurarte de que funciona como esperas.

Este enfoque debería cumplir con tu objetivo de transformar un número almacenado en ACF en un shortcode personalizado y luego ejecutarlo dinámicamente en tu página.