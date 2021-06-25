# Tarea02-SOLID

## Repositorio 

https://github.com/vecalciskay/javabits/tree/master/programas/batallaNaval

## Open-Closed Principle

La clase Barco es la única sobre la que se puede instanciar los objetos que se van a mostrar en la partida, sin embargo, en BatallaNaval tenemos diferentes tipos de naves que no necesariamente son Barcos, en consecuencia, si quisiéramos incluirlas a futuro tendríamos que reescribir código muchas veces.
Solución:
Hacer una interfaz Objeto, que nos permita identificar si un Objeto es de Ataque o Defensa. Para el caso de Ataque, tenemos 2 tipos: Submarinos y Barcos. Para la Defensa, tenemos Minas. La diferencia entre esta versión y la anterior es que podríamos hacer más complejo el juego sin ningún problema.

# UML

![Batalla Naval - copia](https://user-images.githubusercontent.com/33163800/123380881-9c879600-d555-11eb-9645-47f3d90511d1.png)


![BatallaNaval - Solución SOLID - copia](https://user-images.githubusercontent.com/33163800/123381033-cccf3480-d555-11eb-9674-bdb6fd0a8b2f.png)

# Código

![Captura de pantalla (104)](https://user-images.githubusercontent.com/33163800/123381372-46ffb900-d556-11eb-8ec2-6bf009bdd734.png)
![Captura de pantalla (105)](https://user-images.githubusercontent.com/33163800/123381376-47984f80-d556-11eb-9231-f3ded444658e.png)
![Captura de pantalla (106)](https://user-images.githubusercontent.com/33163800/123381379-4830e600-d556-11eb-8163-269378013088.png)

# Propuesta


![Captura de pantalla (107)](https://user-images.githubusercontent.com/33163800/123382202-474c8400-d557-11eb-956c-be786bfd601f.png)

## Repositorio 2

https://github.com/erik/Asteroids

## Violación de SRP

El programa cuenta con una clase llamada Stage, la clase no solo se encarga de mostrar el nivel del juego y su información, sino que también maneja colisiones.
Debido a esto la clase cuenta con muchas responsabilidades llevándole a violar en principio SOLID de SRP (single responsibility principle)

Caso 1: Creación del nivel

![image](https://user-images.githubusercontent.com/70679514/123452638-383ff300-d5a4-11eb-9a11-0137b0e07ba4.png)

![image](https://user-images.githubusercontent.com/70679514/123452651-3b3ae380-d5a4-11eb-9034-101660c14279.png)

![image](https://user-images.githubusercontent.com/70679514/123452660-3e35d400-d5a4-11eb-8fb2-e460988fec2d.png)

Caso 2: Manejar colisiones

![image](https://user-images.githubusercontent.com/70679514/123452685-44c44b80-d5a4-11eb-8a0c-eecd913bdb1f.png)

![image](https://user-images.githubusercontent.com/70679514/123452692-48f06900-d5a4-11eb-8029-a6bc42c47388.png)

## Violación de OCP

Dentro de la clase Asteroid existe una violación al principio de OCP ya que si en un futuro se quisiera añadir más tamaños de asteroides(Scales) se tendrían que modificar todos los constructores de la clase para poder realizar el cambio, lo que significaría que está abierto a modificaciones y cerrado a extensiones, violando así el OCP.

Caso 1: Asteroid

![image](https://user-images.githubusercontent.com/70679514/123452817-6ae9eb80-d5a4-11eb-9ba3-d57b270ed3a5.png)

![image](https://user-images.githubusercontent.com/70679514/123452835-6f160900-d5a4-11eb-96bc-fe2ddabc1b43.png)

## Soluciones

SRP

Caso 1: Creación del nivel

Crear una nueva clase StageLoader en el cual se encuentran los métodos referentes a la creación del nivel, quedando algo parecido a lo siguiente:

![image](https://user-images.githubusercontent.com/70679514/123452920-85bc6000-d5a4-11eb-96c9-ed03ddc19aa5.png)

Caso 2: Manejar Colisiones

Se creó una clase Collision con los métodos:
-	checkCollisions ()
-	checkBulletCollision ()
-	
![image](https://user-images.githubusercontent.com/70679514/123452975-966cd600-d5a4-11eb-8bab-b76bb6b73083.png)

OCP

Caso 1: Asteroid
Se remplaza la clase Asteroid por una interfaz Asteroid de la cual sus subclases son los diferentes tamaños de asteroides que tendría el juego.

![image](https://user-images.githubusercontent.com/70679514/123453027-a5ec1f00-d5a4-11eb-9ddd-a41ec1fb09e9.png)

![image](https://user-images.githubusercontent.com/70679514/123453034-a7b5e280-d5a4-11eb-962b-9f3a1dabe81d.png)

De esta forma todos los nuevos tamaños de asteroides que quisieran añadirse en un futuro solo necesitarían crearse en una nueva clase sin necesidad de modificar las clases existentes, de esta manera se cumple OCP al estar cerrado a modificaciones y abierto a extensiones.

## UML

![image](https://user-images.githubusercontent.com/70679514/123453085-b7352b80-d5a4-11eb-8ad1-fa6cb66be84d.png)

## Propuesta 

![image](https://user-images.githubusercontent.com/70679514/123453112-c0be9380-d5a4-11eb-843b-38829d02cb2c.png)



Repositorio3: https://github.com/anuvgupta/murk.git

![image](https://user-images.githubusercontent.com/74307558/123459956-94a71080-d5ac-11eb-8377-35d879cb00a7.png)

Agrega un tipo de accion para cada celda dependiendo del lugar donde se encuentre el jugador pero si quisieramos agregar mas lugares con su respectiva acción se estaria violando el principio LSP, por lo cual una solución mas óptima seria crear una clase abstracta de acciones con el metodo addAction(que se encargara de agregar la accion) en la cual de ella van a extender los diferentes tipos de Lugares con su respectivo addAction.

![image](https://user-images.githubusercontent.com/74307558/123460017-a5578680-d5ac-11eb-9754-ec91a527d3cd.png)

Así cumplimos con OCP y LSP

La clase Player manipula los datos del jugador y a la vez también lo hace con los datos de Item por lo cual incumple con SRP.
![image](https://user-images.githubusercontent.com/74307558/123460286-02ebd300-d5ad-11eb-9a06-4e7dd129d434.png)

Por lo cual:
![image](https://user-images.githubusercontent.com/74307558/123460743-b6ed5e00-d5ad-11eb-81dd-ec5ba5ac2116.png)







