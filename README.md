# bases_de_datos_relacionales
 práctica del modulo de bases de datos relacionales del bootcamp de Keepcoding. 

## Justificación

### Usuario

He decidido dentro de usuario crear los siguientes apartados:

    Id_usuario
    Dni
    Nombre
    Apellidos
    Fecha_nacimiento
    FK Contacto_id

En el caso de contacto quería tenerlo en una tabla separada porque teléfono y e-mail podrían entenderse como un conjunto de datos, tuve que referenciarlo en la propia entidad usuario para garantizar que en cada usuario al menos esta un teléfono, ya que en la tabla contacto, teléfono está como NOT NULL.

### Contacto

Dentro de contacto tengo los siguientes campos:

    Id_contacto
    Teléfono
    E-mail
    
Aunque no era obligatorio para la práctica preferí dar la opción de agregar e-mails (aunque no es un campo obligatorio), facilitando así que si "mi primo" en un futuro decide hacer campañas de marketing electronico y enviar e-mails a sus clientes pues pueda hacerlo.

### Dirección

En la tabla dirección tengo los siguientes campos:

    PK/FK Usuario_id
    numero_portal
    Piso
    Puerta
    FK Calle
    Codigo_postal 

En esta tabla incluí un campo llamado puerta, podría haber combinado piso y puerta y haber tenido valores como "1 Izq" pero me parecía más limpio y que daba mas opciones a futuro la opción por la que me decanté. 
Las opciones que entendí que podrían no estar obligatoriamente en una dirección no las hice NOT NULL.

### Calle

En la tabla calle tengo los siguientes campos:

    Id_calle
    Calle 

Esta tabla nace porque decidí tener el campo calle separado para evitar posibles duplicidades, un usuario podría residir en la misma calle que otro, asi que para mí tenía sentido el crear una tabla a parte y referenciar la calle desde ahí. 

### Películas

En la tabla películas tengo los siguientes campos:

    Pelicula_id
    Nombre_pelicula
    FK Género
    Sinopsis

Para la tabla películas quise separar tanto género para evitar duplicidades como directores, por el mismo motivo que en la tabla dirección, además de permitir que una película pueda tener más de un director.

### Género

En la tabla género tengo los siguientes campos:

    Genero_id
    Genero

En esta tabla registro los diversos géneros a los que puede estar asociada una película, así evito que en películas pueda haber valores en el campo género repetidos.

### Directores

En la tabla directores tengo los siguientes campos:

    Directores_id
    FK Pelidula_id
    FK Director_id

Esta tabla nace de la idea de poder tener más de un director relacionado con una película.

### Director

En la tabla director tengo los siguientes campos:

    Director_id
    Nombre_director  

En esta tabla ya si que almaceno todos los directores.

### Copia

En la tabla copia tengo los siguientes campos:

    Id_copia
    FK Id_pelicula
    
Esta tabla nace de la necesidad de tener más de una copia por película.

### Alquiler

En la tabla alquiler tengo los siguientes campos:

	alquiler_id 
	inicio_alquiler 
	fin_alquiler 
	FK id_usuario 
	FK id_copia 
	
Esta tabla tiene como finalidad crear una relación entre un usuario que alquila una película y la copia que se lleva, así como la información de la fecha y la hora en la que la alquiló y la fecha y la hora en la que la ha devuelto (de no estar devuelta su valor sera null y la consideraremos como alquilada).

# Adicional

He añadido varios unique index con la intención de que datos como el dni, el email, teléfono, nombre de un director, género de las peliculas, las calles, y las propias películas no puedan repetirse, en los datos donde contenemos textos los comparo transformandolos a minúsculas para evitar que puedan entrar dos entidades con el mismo nombre pero uno en mayúsculas y otro en minúsculas.

