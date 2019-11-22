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


# Funcion Filtrado Disponibles con Formity y Doris-PDO
Filtro a el contenido de una Tabla
 ```php
 $table = Tablefy::getInstance('tabla_filtrado');
 //aqui se indica a el formulario que contiene los campos de filtrado
 $table->setFilter('formulario-fiiltrado');

 //declara el set header
 ...
 //declarar el set data con pagination
 $table->setData(function($Pagination) use($db) {
    return Libs::funcion_de_llenado($db, $pagination);
  });

 ```

En la declaracion del formulario
 ```php


 
 ```


Dentro de la funcion  de llenado
```php

 static function obtener_listado_de_contactos($db, $pagination = null) {
  $where = array();
  if(($pagination instanceof Pagination) && $pagination->has_filter) {
    $filtro = $pagination->filter;
    if(@!is_null($filtro['campo_filtro'])) {
        $where[] = "P.campo_db =".(string) $filtro['campo_filtro'];
      }     
  }

  $where = array_filter($where, function($n) { return !empty($n); });
  $where = !empty($where) ? ' AND ' . implode(' AND ', $where) : '';

  $consulta =" SELECT * FROM  TU_TABLA WHERE eliminado not null ".$where

 }
```
