# Declarar una tabla simple


```php
$table = Tablefy::getInstance('tabla_prueba');
$table->setHeader(array('name_columna1','name_columna2'));
$table->setData(function()  {
	  $data  = obtener_datos()
      return $data
  },function($n) {
       return array(
        'name_columna1'           =>$n['campo_1'],
        'name_columna2'          => $n['campo_2'],
       );
  });

$table->prepare();


```
# Declarar el nombre de las columnas
```php
$table->setHeader(array('name_columna1','name_columna2'));

```

# cargar datos a la tabla
```php
$table->setData(function()  {
	  $data  = obtener_datos()
      return $data
  },function($n) {
       return array(
        'name_columna1'           =>$n['campo_1'],
        'name_columna2'          => $n['campo_2'],
       );
  });

```

# Opciones de la tabla
```php
 $table->setOption('Nombre de la Opcion&', function($n)  {
    //codigo a ejecutar
    });

 ```


# Opcion par Exportar Tabla a pdf y Excell
```php
$table->export('PDF','Excel');

```