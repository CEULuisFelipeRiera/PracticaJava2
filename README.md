# PracticaJava2

https://github.com/CEULuisFelipeRiera/PracticaJava2.git

Práctica: aplicación para gestionar cultivos
de bacterias II
Los biólogos para los que hemos hecho la aplicación se han dado cuenta de que no
todos los experimentos que van a realizar en las poblaciones duran 30 días, sino que
algunos van a durar algunos días más, y otros algunos días menos, aunque
definitivamente no pueden comenzar después de la fecha de finalización, por lo que nos
han pedido que la duración sea variable. Además, nos han pedido que cambiemos las
unidades en las cuales medimos la comida de las bacterias de miligramos (donde el
máximo eran 300) a microgramos (donde el máximo serán 300,000).
Por otro lado, también quieren trabajar con experimentos donde el patrón de suministro
de comida a las bacterias es diferente. Además del patrón de incremento lineal seguido
de decremento lineal que ya contemplamos en la primera versión de la aplicación,
quieren que también existan otras tres opciones para indicar la comida para las
bacterias: una cantidad de comida constante durante toda la duración del experimento;
incrementar linealmente la cantidad de comida de cada día partiendo de un valor inicial
y llegando a un valor final; y proporcionar una determinada cantidad de comida
constante durante todo el experimento un día, y al siguiente no proporcionar comida, al
siguiente se le proporciona, y al siguiente no se le proporciona, y así sucesivamente.
(Nota: 50% de la calificación de la práctica hasta aquí).
También quieren poder ordenar el listado de todas las poblaciones de bacterias por la
fecha de inicio asociada a la población de bacterias (orden cronológico de más antiguo a
más reciente), por el nombre de la población de bacterias, y por el número de bacterias
de la población. (Nota: 65 % de la calificación de la práctica hasta aquí)
Por otro lado, cuando han comenzado a hacer los experimentos con las bacterias se han
dado cuenta de que muchos de los experimentos no terminaban como ellos esperaban.
Por ello nos han pedido que la propia herramienta sea capaz de simular cómo va a ser la
evolución del experimento empleando simulaciones de Montecarlo. La simulación de
Montecarlo consiste en realizar simulaciones basadas en la generación de números
aleatorios y en la aplicación de una serie de restricciones que tratan de reflejar lo que
sucede en el mundo real, añadiendo una componente de aleatoriedad. Para hacer este
tipo de simulación consideraremos que las bacterias están sobre un plato de cultivo que
es un rectángulo formado por celdas todas ellas de tamaño igual y con 20 celdas de lado
(por lo que el plato tendrá 20 × 20 celdas).
Los científicos el primer día colocan a todas las bacterias en el centro del plato de
cultivo, ocupando un cuadrado con un lado de sólo 4 × 4 celdas. Cada una de estas
celdas se repartirá inicialmente las bacterias a partes iguales. Es decir, si inicialmente
tenemos una población de 1600 bacterias, cada celda del recuadro central de 4 × 4 del
plato tendrá 100 bacterias.
La comida para las bacterias se suministra de tal modo que se reparte a partes iguales
entre todas las celdas del plato de cultivo (no sólo donde hay bacterias). Es decir, si se
han añadido 40,000 microgramos de comida, a cada celda le tocan 100 microgramos de
comida. Consideraremos que la cantidad de comida en microgramos siempre se
representa por números enteros.
Para realizar la simulación de Montecarlo se aplicarán las siguientes reglas. Las
bacterias comienzan el primer día en el centro del plato, ocupando un subcuadrado de 4
× 4. Las bacterias se reparten a partes iguales entre todas las celdas del subcuadrado. La
comida del primer día está repartida a partes iguales entre todas las celdas del plato.
A continuación, comenzaremos a simular qué pasa ese día con cada una de las bacterias.
Seleccionaremos la primera bacteria. Para cada bacteria realizaremos los siguientes
pasos de la simulación de Montecarlo que consisten en lo siguiente:
1. Si la bacteria se encuentra en una celda donde hay 100 microgramos de comida
o más, la bacteria come 20 microgramos de comida, que desaparecerán de la
celda, y la bacteria "genera un número aleatorio" entre 0 y 100; si
a. el número es menor que 3, la bacteria se muere.
b. si el número es mayor o igual que 3 y menor que 60, la bacteria se queda
en la celda en la que está;
c. si el número es mayor o igual que 60 y menor que 100, la bacteria se
mueve a una celda contigua a la celda en la que está según se indica en la
tabla; excepto si dicha celda está fuera del plato; en ese caso se queda
donde está.
60 <=N < 65 65 <=N <70 70 <=N < 75
75 <=N <80 N < 3 se muere
3 <=N < 60 se
queda en esta celda
80 <=N < 85
 85 <=N <90 90 <=N < 95 95 <=N
<100
2. Si la bacteria se encuentra en una celda donde hay menos de 100 microgramos
de comida y más de 9 microgramos de comida, la bacteria come 10 microgramo
de comida, que desaparecerá de la celda, y la bacteria genera un número
aleatorio entre 0 y 100; si
a. el número es menor que 6, la bacteria se muere.
b. si el número es mayor o igual que 6 y menor que 20, la bacteria se queda
en la celda en la que está;
c. si el número es mayor o igual que 20 y menor que 100, la bacteria se
mueve a una celda contigua a la celda en la que está según se indica en la
tabla; excepto si dicha celda está fuera del plato; en ese caso se queda
donde está.
20 <=N < 30 30 <=N <40 40 <=N < 50
50 <=N <60 N < 6 se muere
6 <=N < 20 se
queda en esta celda
60 <=N < 70
 70 <=N <80 80 <=N < 90 90 <=N
<100
3. Si la bacteria se encuentra en una celda donde hay 9 microgramos o menos de
comida, la bacteria genera un numero aleatorio entre 0 y 100; si
el número es menor que 20, la bacteria se muere.
b. si el número es mayor o igual que 20 y menor que 60, la bacteria se
queda en la celda en la que está;
c. si el número es mayor o igual que 60 y menor que 100, la bacteria se
mueve a una celda contigua a la celda en la que está según se indica en la
tabla; excepto si dicha celda está fuera del plato; en ese caso se queda
donde está.
60 <=N < 65 65 <=N <70 70 <=N < 75
75 <=N <80 N < 20 se muere
20 <=N < 60 se
queda en esta celda
80 <=N < 85
 85 <=N <90 90 <=N < 95 95 <=N
<100
Esta simulación se realiza "10 veces por día" (es decir, para cada bacteria, para cada día
hay que repetir 10 veces los pasos descritos sobre estas líneas). Tras los 10 pasos de la
simulación para cada bacteria, si la bacteria no se ha muerto, calcularemos toda la
cantidad de comida que la bacteria "ha comido" a lo largo de este día y:
1. Si la bacteria ha comido 150 microgramos de comida o más, la bacteria crea tres
bacterias hijas que estarán en la misma celda donde está su madre. En la
simulación de este día no hay que hacer nada con ellas, pero en la simulación del
siguiente día serán bacterias como otra cualquiera y habrá que simularlas.
2. Si la bacteria ha comido de 100 a 150 microgramos de comida, la bacteria crea
dos bacterias hijas que estarán en la misma celda.
3. Si la bacteria ha comido de 50 a 100 microgramos de comida, la bacteria crea
una bacteria hija que estará en la misma celda que ella.
4. Si la bacteria ha comido menos de 50 microgramos de comida, la bacteria no
tiene ningún hijo.
Esta simulación deberá realizarse para todas las bacterias, exceptuando las bacterias
hijas de este día. Una vez la simulación se ha realizado para todas las bacterias,
habremos terminado de simular el primer día. A continuación, se comenzará a simular
el siguiente día; la simulación comenzará repartiendo a partes iguales entre todas las
celdas del plato la comida del día siguiente, que se acumulará a la comida que pueda
haber quedado en esa celda del día anterior. Y se volverá a comenzar a simular todas las
bacterias que estén vivas, tanto las que han sobrevivido del día anterior, como las hijas
que han tenido. Y así sucesivamente hasta llegar a los días que dure el experimento.
Cuando realicemos una simulación, el experimento deberá de ir calculando cuántas
bacterias hay cada día. Este número de bacterias se almacenarán en una matriz
tridimensional que tendrá una matriz bidimensional por día, y para cada día contendrá
en la matriz bidimensional la información relativa al número de bacterias vivas que hay
en ese día y en esa celda al final de la simulación, así como la comida que ha quedado
sin comer en esa celda ese día.
Una vez haya terminado la simulación, deberá mostrarse los resultados al usuario. Para
ello, podremos mostrar el número de bacterias de cada celda del plato en la consola, o
en la pantalla de la aplicación swing. Una solución más elegante sería mostrar en
pantalla una ventana con un panel con una matriz donde se pintarán todas las celdas del
plato de cultivo. El color de cada una de las celdas deberá reflejar de algún modo el
número de bacterias que hay dentro de ella. Por ejemplo, si hay 20 o más bacterias en
una celda, se dibuja en rojo. Si hay entre 15 y 19 bacterias, se dibuja en morado. Si hay
entre 10 y 14 bacterias, se dibuja en naranja. Si hay entre 5 y 9 bacterias se dibujan en
amarillo. Si hay entre 1 y 4 bacterias se dibuja en verde. Si no hay ninguna bacteria, se
dibuja en blanco. Podrán emplearse otros mecanismos de representación del número de
bacterias (por ejemplo, un gradiente de colores reflejando el número de bacterias de
cada celda).
La aplicación deberá permitir realizar las siguientes acciones:
1. Abrir un archivo que contenga un experimento
2. Crear un nuevo experimento
3. Crear una población de bacterias y añadirla al experimento actual
4. Visualizar los nombres de todas las poblaciones de bacterias del experimento
actual
5. Borrar una población de bacterias del experimento actual
6. Ver información detallada de una población de bacterias del experimento actual
7. Realizar y visualizar la simulación correspondiente con una de las poblaciones
de bacterias del experimento.
8. Guardar (se supone que para usar esta opción previamente hemos abierto un
archivo)
9. Guardar como
Necesariamente habrá que guardar en modo texto toda la información correspondiente
con cada experimento. No será necesario guardar la información correspondiente con la
simulación, ya que ésta podrá volver a generarse cada vez que se cargue un experimento
en la aplicación.
Al seleccionar la opción 4, deberá preguntársele al usuario si desea ver las poblaciones
ordenadas por nombre, por fecha o por cantidad de bacterias, y mostrarlas ordenadas
por el campo adecuado.
Consejos
Habla con el profesor para determinar cuál es la mejor forma para representar y
almacenar los datos, y de estructurar la práctica. Organiza la práctica en al menos tres
paquetes. Uno se encargará de la interfaz de usuario, otro se encargará de cargar y
guardar datos en el disco duro, y el tercero se encargará de la lógica de negocio: añadir
ratones, eliminar ratones, etc.… Utiliza funciones y métodos aislados, atómicos y con
una responsabilidad completa. Si tienes dudas sobre la utilidad de una función o
método, consulta con el profesor. Visualice especialmente las clases donde se realiza el
UML y la separación de paquetes.
Sobre la entrega y evaluación de la práctica
Se recomienda la entrega de la práctica el día 15 de mayo para poder revisarla
junto a los profesores antes del examen de la convocatoria ordinaria. 
La práctica debe ser entregada en formato electrónico antes del 9 de junio (inclusive).
Para considerar que la práctica está entregada, el alumno deberá haber completado la
entrega en formato electrónico (a través del campus virtual). La práctica deberá
contener así mismo un fichero ejecutable .jar que permita ejecutar el código fuente
sin necesidad de compilar el código. Si no se encuentra el fichero .jar la práctica se
calificará con un 0.
Por cada semana que se retrase la entrega de la práctica a partir de esta fecha, la nota
final de la práctica se le descontará 1 punto (0.15 puntos por día aproximadamente). La
práctica puede realizarse a través de una consola o a través de una aplicación gráfica de
escritorio empleando swing. El alumno tendrá que realizar una defensa de la práctica; si
el alumno es incapaz de defender la práctica y explicar su funcionamiento, su nota en la
práctica será un 0.
Ítems a entregar: Implementación íntegra de los requisitos establecidos en el
enunciado
de la práctica junto a la memoria descriptiva del trabajo realizado. Se evaluará de forma
más positiva la descripción de requisitos no implementados y conocidos descritos en la
memoria que la falta de funcionalidad desconocida y no descrita.
Todas las clases y sus clases y funciones contenidas deben tener las correspondientes
pruebas unitarias.
Como resultado de esta entrega final se deberá enviar un fichero zip con la carpeta
completa que contenga el proyecto software IntelliJ o NetBeans correspondiente a la
práctica (asegúrese de que incluye todo el código fuente, es la carpeta anterior al src,
test, etc..) y además un fichero ejecutable .jar que permita ejecutar la práctica sin tener
que compilar el código fuente.
La entrega de la práctica forma parte de la evaluación de la práctica.
La memoria incluirá una portada con el nombre del alumno y se ajustará a la siguiente
estructura:
 Análisis y descripción de la aplicación. Este análisis y descripción dará respuesta
a las siguientes preguntas:
o Cómo se han organizado y estructurado las clases y cuál es la
responsabilidad de cada una.
o Qué decisiones de diseño se han tomado.
o Qué comprobaciones de integridad (y excepciones) se han
implementado.
o Qué estructuras de datos ha utilizado y por qué lo ha hecho.
o Qué técnicas de ordenación y búsqueda ha utilizado y por qué lo ha
hecho.
o Diagramas de clases UML.
 Listado de fallos conocidos y funcionalidades definidas en el enunciado que
no se han implementado en el código entregado.
 Listado de todo el código fuente de la aplicación organizado por paquetes (si
aplica) y clases.
 Conclusiones (que incluirán, obligatoriamente, una valoración del tiempo
dedicado a la práctica).
Además de la defensa, la práctica se evaluará en relación a:
 Organización y estructura del código (utilización de conceptos y patrones de
programación, orientada a objetos: herencia, polimorfismo, encapsulación,
reutilización, utilización correcta de estructuras de control, etc.).
 Utilización de estructuras de datos adecuadas y utilización de técnicas de
ordenación y búsqueda, . . . El uso de todas ellas deberá ser analizado y
justificado en la memoria descriptiva.
 Uso de Javadoc para documentar las clases y métodos.
 Funcionamiento ajustado a los requisitos establecidos (incluyendo, además de
chequeos de datos, integridad de la información, gestión de excepciones...).
 Claridad del código y adecuación a las normas de estilo (correcto nombrado
de clases, métodos y variables, comentarios internos, indentación del código...).
Se advierte al alumno de que, como parte de la evaluación, se utilizará una herramienta
antiplagio de código. En caso de copia total o parcial del código de la práctica, se
aplicarán las medidas correspondientes en el código de conducta de la universidad
CEU-San Pablo. 




