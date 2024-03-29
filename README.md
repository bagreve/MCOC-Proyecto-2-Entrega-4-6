# MCOC-Proyecto-2-Entrega-4 & 6
Tiempos de procesamiento para una simulación son con un dt de 0.0001 segundos, un t max de 2. segundos y diametro de particula de 0.15 mm.

## Caracteristicas del Pc:

### Edicion de Windows
- Windows 10 Home

### Sistema
- Procesador: Intel(R)Core(TM) i3-4005U CPU @ 1.7GHz 1.7 GHz
- Memoria instalada(RAM): 8,00 GB
- Tipo de sistema: Sistema operativo de 64 bits, procesador x64
## Codigo 1:
## Tiempos de Procesamiento
Los tiempos de procesamiento del codigo son variables debido a que el procesador realiza distintas tareas mientras corre el codigo haciendo que demore algunas veces más y otras menos en finalizar, pero debido al tiempo disponible y la tardanza en procezar todo el codigo se procesará solo una vez cada codigo. El tiempo con diferente cantidad de particulas es exponencial debido a que mientras más particulas se tendran que realizar mas ciclos como es el caso de comparar radios y saber si chocan con el suelo o entre particulas.
Los graficos expuestos son el comportamiento de las particulas en el eje x e y en el tiempo de 2. segundos, donde se muestran las reacciones con las fuerzas de lift, drag y masa mientras se observan colisiones entre particulas y con el suelo creado por particulas del mismo diametro.
Los resultados no representan del todo la realidad, en primer lugar porque no se concideran fuerzas como Magnus y Basset, además de no ser del todo reales las constantes de lift, drag ni de masa, idealizandolas. Al momento del impacto se consideraron "resortes" que le aplicaban fuerzas en la direccion opuesta. Se usaron particulas perfectamente esfericas y por último el suelo es una cama de particulas circularesen perfecto orden y sin capacidad de movimiento en ninguna direccion.
Los cuellos de botella son los ciclos que se tienen que crear para revisar si las particulas chocaron entre ellas recorriendo cada posicion y comparandolas con las otras, los ciclos que revisan si chocaron contra el suelo generando una fuerza variable con la intencidad de un resorte. Es por eso que mientras más perticulas y más tiempo tomará considerablemente más tiempo.   

- Con 2 Particulas: 10.7 Segundos
![dos particulas](https://user-images.githubusercontent.com/53497030/66689184-429b4b80-ec60-11e9-807a-e6c207e085f0.png)

- Con 5 Particulas: 1 minuto 43 Segundos
![cinco  particulas](https://user-images.githubusercontent.com/53497030/66689185-429b4b80-ec60-11e9-85b0-b9f08e570bfd.png)

- Con 10 Particulas: 19 minutos 19 segundos
![diez particulas](https://user-images.githubusercontent.com/53497030/66691694-8b5a0100-ec6e-11e9-8147-a40c879820fa.png)

- Con 20 Particulas: Tras 1 hora 25 minutos se decide detener la operacion.

## Resultados del profesor:


- Para 2 particulas: 44.1 segundos
El primer grafico muestra en el cuadro de arriba, la distancia recorrida durante el tiempo y el cuadro de abajo, las diferentes alturas alcanzadas por las particulas en el tiempo.
El segundo grafico, consiste en ver la posicion de las particulas junto con el gradiente de velocidad del flujo
El último es sobre las velocidades de las particulas en los ejes x e y respecto al tiempo.
![particle_trajectories](https://user-images.githubusercontent.com/53497030/66692090-8cd8f880-ec71-11e9-9012-365c25500ea5.png)

![particle_velocities](https://user-images.githubusercontent.com/53497030/66692091-8cd8f880-ec71-11e9-8fb7-fffe704fc73f.png)

![particle_positions](https://user-images.githubusercontent.com/53497030/66692092-8cd8f880-ec71-11e9-990c-82a1dad8bc59.png)

- Para 5 particulas :115.1 segundos
El primer grafico muestra en el cuadro de arriba, la distancia recorrida durante el tiempo y el cuadro de abajo, las diferentes alturas alcanzadas por las particulas en el tiempo.
El segundo grafico, consiste en ver la posicion de las particulas junto con el gradiente de velocidad del flujo
El último es sobre las velocidades de las particulas en los ejes x e y respecto al tiempo.
![particle_trajectories](https://user-images.githubusercontent.com/53497030/66691998-c3fada00-ec70-11e9-9865-4457141eca4e.png)

![particle_velocities](https://user-images.githubusercontent.com/53497030/66691999-c3fada00-ec70-11e9-9a9b-efdc0e600ba3.png)

![particle_positions](https://user-images.githubusercontent.com/53497030/66692000-c3fada00-ec70-11e9-8c07-6eea4be40559.png)

- Para 10 particulas: 251.5 segundos
El primer gráfico, al igual que los nuestros muestra la posicion de las particulas en los ejes x e y. El segundo, consiste en ver la posicion de las particulas junto con el gradiente de velocidad del flujo y el último grafico es sobre las velocidades de las particulas en los ejes x e y respecto al tiempo.
![particle_positions](https://user-images.githubusercontent.com/53497030/66691767-1affaf80-ec6f-11e9-88fe-2a7f9044c3ac.png)

![particle_trajectories](https://user-images.githubusercontent.com/53497030/66691768-1affaf80-ec6f-11e9-8ba6-3447e82543c7.png)

![particle_velocities](https://user-images.githubusercontent.com/53497030/66691769-1b984600-ec6f-11e9-909c-9c052286b683.png)

- Para 20 particulas: 477 segundos
El primer grafico muestra en el cuadro de arriba, la distancia recorrida durante el tiempo y el cuadro de abajo, las diferentes alturas alcanzadas por las particulas en el tiempo.
El segundo grafico, consiste en ver la posicion de las particulas junto con el gradiente de velocidad del flujo
El último es sobre las velocidades de las particulas en los ejes x e y respecto al tiempo.
![particle_trajectories](https://user-images.githubusercontent.com/53497030/66692098-97938d80-ec71-11e9-837f-9203b3a8f3a1.png)

![particle_velocities](https://user-images.githubusercontent.com/53497030/66692099-97938d80-ec71-11e9-9065-e4f927af4643.png)

![particle_positions](https://user-images.githubusercontent.com/53497030/66692100-97938d80-ec71-11e9-9ab6-e3de62ac00aa.png)



## Codigo 2: optimizado
Este codigo nace del programa anterior pero optimizado con el fin de lograr que mientras mas particulas el tiempo de proseso tarde linealmente más, a diferencia del codigo anterior que era exponencial. Esto se logra gracias a cambiar el funcionamiento de la funcion de choque dentro del odeint que es lo que más tarda el programa anterior, es por eso que se separan las particlas que pueden chocar con las que no, acelerando el proceso ya que al no chocar el odeint se simplifica, otra cosa que se mejora es guardar los datos en un archivo binario para luego leerlos y plotearlos con un codigo aparte.

El programa tiene un paso de tiempo de 0.00001 segundos con un tiempo maximo de 0.05 segundos y se utilizaran los mismos archivos de posicionamiento del codigo anterior con 2, 5, 10 y 20 particulas.

- Con 2 Particulas: tiempo total 10.7100000381 segundos.
![Dos particulas](https://user-images.githubusercontent.com/53497030/68216627-ece86380-ffbf-11e9-9833-2f9011dea036.PNG)

- Con 5 Particulas: tiempo total 22.5629999638 segundos.
![Cinco particulas](https://user-images.githubusercontent.com/53497030/68216628-ece86380-ffbf-11e9-909d-c9874416331d.PNG)

- Con 10 Particulas: tiempo total 44.6019999981 segundos.
![Dies particulas](https://user-images.githubusercontent.com/53497030/68216634-efe35400-ffbf-11e9-9efc-84ec594fe6fc.PNG)

- Con 20 Particulas: tiempo total 86.361000061 segundos.
![Veinte particulas](https://user-images.githubusercontent.com/53497030/68216637-efe35400-ffbf-11e9-946c-b76c1015d46e.PNG)

