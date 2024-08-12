Para mostrar un campo de texto creado con Advanced Custom Fields (ACF) en una página de WordPress, debes seguir estos pasos:

### 1. Crear el Campo en ACF
Primero, asegúrate de haber creado el campo de texto en ACF y asignado a la página o post donde quieres mostrarlo. Una vez hecho esto, anota el nombre del campo (el "Field Name"), ya que lo necesitarás para acceder a su valor.

### 2. Editar el Template o Página
Dependiendo de dónde quieras mostrar el campo, deberás editar el archivo de plantilla de WordPress correspondiente. Esto puede ser el archivo `page.php`, `single.php`, `index.php`, o un archivo de plantilla específico si estás utilizando un tema hijo.

### 3. Usar el Código PHP para Mostrar el Campo
Dentro del archivo de plantilla, inserta el siguiente código PHP en el lugar donde quieras que aparezca el campo:

```php
<?php
// Asegúrate de que ACF esté activo y disponible
if( function_exists('get_field') ) {
    // Reemplaza 'nombre_del_campo' con el nombre del campo ACF que creaste
    $mi_campo = get_field('nombre_del_campo');

    // Comprueba si el campo tiene un valor y muéstralo
    if( $mi_campo ) {
        echo '<p>' . esc_html($mi_campo) . '</p>';
    } else {
        echo '<p>No hay valor para este campo.</p>';
    }
}
?>
```

### 4. Guardar y Visualizar
Guarda los cambios en el archivo de plantilla y visualiza la página en tu sitio web. El valor del campo de texto debería aparecer en la ubicación específica donde colocaste el código.

### Ejemplo Completo
Supongamos que creaste un campo ACF llamado `subtitulo`. Aquí tienes un ejemplo de cómo mostrarlo en el archivo de plantilla:

```php
<?php
if( function_exists('get_field') ) {
    $subtitulo = get_field('subtitulo');

    if( $subtitulo ) {
        echo '<h2>' . esc_html($subtitulo) . '</h2>';
    }
}
?>
```

Este código mostrará el subtítulo en un encabezado `<h2>` en la página donde se utiliza.

### Alternativa: Usar el Shortcode de ACF en el Editor
Si prefieres no editar el archivo de plantilla, también puedes usar un shortcode en el editor de WordPress:

```html
[acf field="nombre_del_campo"]
```

Este shortcode mostrará el valor del campo ACF directamente en el contenido de la página o post.

¡Y eso es todo! Con estos pasos deberías poder mostrar cualquier campo de texto creado con ACF en tu página de WordPress.