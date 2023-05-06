# kb-para-catalogo-de-productos

//Para implementar la Base de Conocimientos (KBs) en CLIPS, primero se debe definir la estructura de los hechos para representar a los clientes y los productos en el catálogo.

(deftemplate cliente
   (slot id (type INTEGER))
   (slot nombre (type STRING))
   (slot correo (type STRING))
   (slot cel (type STRING)))

(deftemplate producto
   (slot marca (type STRING))
   (slot modelo (type STRING))
   (slot memoria (type INTEGER))
   (slot precio (type FLOAT))
   (slot existencia (type INTEGER)))
   
   //A continuación, se definen los hechos para representar a los clientes y los productos en la KB.
   
   (defrule agregar-cliente
   (not (cliente (id ?)))
   =>
   (assert (cliente (id 1) (nombre "Juan Perez") (correo "juanperez@gmail.com") (cel "5544332211")))
   (assert (cliente (id 2) (nombre "Maria Garcia") (correo "mariagarcia@hotmail.com") (cel "5555667788")))
   (assert (cliente (id 3) (nombre "Pedro Lopez") (correo "pedrolopez@yahoo.com") (cel "5566778899"))))
   
(defrule agregar-productos
   (not (producto (marca ?)))
   =>
   (assert (producto (marca "Apple") (modelo "Watch Series 6") (memoria 32) (precio 7999.99) (existencia 10)))
   (assert (producto (marca "Samsung") (modelo "Galaxy S21") (memoria 128) (precio 13999.99) (existencia 5)))
   (assert (producto (marca "Huawei") (modelo "MatePad Pro") (memoria 256) (precio 10999.99) (existencia 8)))
   (assert (producto (marca "American Express") (modelo "Tarjeta de Crédito") (memoria 0) (precio 0) (existencia 100))))

//Por último, se definen los hechos para representar las tarjetas de crédito en la KB.

(deftemplate tarjeta
   (slot nombre (type STRING))
   (slot tasa (type FLOAT))
   (slot limite (type FLOAT)))

(defrule agregar-tarjetas
   (not (tarjeta (nombre ?)))
   =>
   (assert (tarjeta (nombre "Banamex") (tasa 20.0) (limite 50000.0)))
   (assert (tarjeta (nombre "BBVA") (tasa 18.0) (limite 70000.0)))
   (assert (tarjeta (nombre "American Express") (tasa 25.0) (limite 100000.0))))

//Con estas reglas y hechos, se ha implementado la KB con los clientes, el catálogo de productos y las tarjetas de crédito. Ahora se puede realizar inferencias y consultas sobre esta KB en CLIPS.
