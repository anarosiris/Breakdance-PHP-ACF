Para cambiar el valor del campo de tipo verdadero/falso en ACF para todos los posts de un tipo específico de manera masiva, puedes usar un script en PHP que actualice estos valores. Aquí te muestro cómo hacerlo:

1. **Crear un archivo de script**:
   - Crea un archivo PHP en la raíz de tu instalación de WordPress o en un lugar accesible.

2. **Escribir el script**:
   Copia y pega el siguiente código en el archivo PHP que creaste. Este script actualizará el valor del campo ACF para todos los posts del tipo "post".

   ```php
   <?php
   // Cargar WordPress
   require_once('wp-load.php');

   // Configura el nombre del campo ACF y el tipo de post
   $acf_field_name = 'nombre_del_campo'; // Cambia esto por el nombre de tu campo ACF
   $post_type = 'post'; // Cambia esto si usas un tipo de post diferente

   // Obtener todos los posts del tipo especificado
   $args = array(
       'post_type' => $post_type,
       'posts_per_page' => -1, // Obtener todos los posts
       'post_status' => 'publish' // Solo posts publicados
   );
   $posts = get_posts($args);

   foreach ($posts as $post) {
       // Actualizar el campo ACF a verdadero (true)
       update_field($acf_field_name, true, $post->ID);
   }

   echo 'Todos los posts han sido actualizados.';
   ?>
   ```

3. **Ejecutar el script**:
   - Sube el archivo PHP al servidor y accede a él desde el navegador. Por ejemplo, si lo guardaste como `update-acf-field.php` en la raíz, ve a `http://tusitio.com/update-acf-field.php`.

4. **Eliminar el script**:
   - Una vez que el script haya ejecutado correctamente y todos los campos se hayan actualizado, asegúrate de eliminar el archivo PHP del servidor para evitar problemas de seguridad.

**Nota importante**: Realiza una copia de seguridad de tu base de datos antes de ejecutar cualquier script que modifique datos en masa. Esto te permitirá restaurar la información en caso de cualquier error.


Para adaptar el script anterior al campo específico que mencionas, `indice_contenidos_entrada`, y asegurarte de que se establezca por defecto en verdadero, aquí te dejo el código personalizado:

```php
<?php
// Cargar WordPress
require_once('wp-load.php');

// Configura el nombre del campo ACF
$acf_field_name = 'indice_contenidos_entrada'; // Nombre del campo ACF tipo verdadero/falso

// Obtener todos los posts del tipo 'post'
$args = array(
    'post_type' => 'post', // Ajusta si el tipo de post es diferente
    'posts_per_page' => -1, // Obtener todos los posts
    'post_status' => 'publish' // Solo posts publicados
);
$posts = get_posts($args);

// Recorrer cada post y actualizar el campo ACF
foreach ($posts as $post) {
    // Establecer el campo ACF a verdadero (true)
    update_field($acf_field_name, true, $post->ID);
}

echo 'Todos los posts han sido actualizados al valor verdadero en el campo "indice_contenidos_entrada".';
?>
```

### Instrucciones para ejecutar el script:
1. **Crea un archivo PHP** con el código anterior. Puedes llamarlo, por ejemplo, `update-acf.php`.
2. **Sube el archivo al servidor** donde está alojado tu sitio de WordPress. Generalmente, puedes subirlo a la raíz del directorio de WordPress.
3. **Accede al archivo desde tu navegador** para ejecutar el script. La URL será algo como `http://tusitio.com/update-acf.php`.
4. **Verifica los cambios** en tu panel de WordPress para asegurarte de que todos los posts han sido actualizados correctamente.
5. **Elimina el archivo del servidor** para mantener segura tu instalación de WordPress.

### Consideraciones de seguridad:
- Asegúrate de tener una copia de seguridad reciente de tu sitio antes de ejecutar el script.
- Elimina el script del servidor una vez que hayas verificado que los cambios se han aplicado correctamente para prevenir que alguien más pueda ejecutarlo.