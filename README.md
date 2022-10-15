# RoboticsLab4
## Requerimientos
* Ubuntu 20.04 LTS o version compatible
* ROS Noetic 
* MATLAB 2015b o superior
* Robotics toolbox de mathworks
* Robot PhantomX Pincher

## 1. Parametros DH y uso del toolBox
Primero medimos las distacias entre cada una de las articulaciones para luego sacar los parametros DH del robot.
![Diagrama](imagenes/Dibujo.png)

Luego creamos su par virtual con el toolbox.
![Parametros DH](imagenes/DH.jpeg)

Primero hicimos un diagrama del robot para poder sacar sus parámetros DH y poder hacer su par virtual con el toolbox.
Con el robot creado lo ponemos en la posición de Home para ver su MTH. Cabe aclarar que nosotros escogimos nuestro Home igual al del robot con todos sus motores en 0.

![MTH](imagenes/MTH.png)

Luego pusimos le robot en diferentes posiciones las cuales son:
![Pos](imagenes/Pos.jpeg)

Y estos son los resultados:

![Q4](imagenes/q4.jpeg)
![Q1](imagenes/q.jpeg)
![Q2](imagenes/q2.jpeg)
![Q3](imagenes/q3.jpeg)
![Q5](imagenes/q5.jpeg)

## 2. Conecciones con MatLab
Primero tenemos que crear un scrip que sea capas de publicar cada tópico del controlador de junta.
Este scrip lo que hace es crear el cliente de pose y posición para luego poner el vector objetivo de los motores, cambiar al ID del controlador que se va a utilizar y asignarlo al motor, convertir los grados a 10 bits y por último verificar los límites y enviar el mensaje.

![Scrip](imagenes/Juntas.jpeg)

En esta parte básicamente se revisa si el tópico esta activo luego se crea el publicador, se inicializa la recepción del mensaje del suscriptor y luego se imprime el valor de cada junta con su valor en radianes.

![Simu](imagenes/Simulacion.jpeg)

## 3. Union de todo
Para la parte final utlizamos un ciclo para enviar secuencialmente el mensaje a cada motor.

![Todo](imagenes/Todo.png)

## Conclusiones
* ROS funciona de manera independiente a Matlab o Python, los scripts desarrollados en estos programas solo nos permiten comunicarnos con los diferentes nodos que se encuentren en ejecución.
* Por medio de los paquetes provistos por Dynamixel es posible controlar el Robot PhantomX Pincher de manera sencilla, adicionalmente con el repositorio PXRobot es posible que la comunicación entre los servomotores se de uno a uno de manera serial, lo cuál facilitó la modificación de las poses del robot en Matlab
