# Mejores prácticas para los bots de Discord


* NB: estas pautas están destinadas a los bots que se ejecutan en servidores públicos. Si tu
bot está restringido a los privados, es probable que este documento no se aplique a usted. *

1. #### Prefijos de comando
    1. ** Los comandos deben invocarse explícitamente **
    Los bots no deberían activarse en
chat normal. En su lugar, use un prefijo de comando o solo responda cuando su bot esté
@mencionado directamente.
    2. ** Utilice prefijos únicos **
    Prefijos de un solo carácter como `!`, `$` Y `.`
son comunes para activar comandos y dan lugar a superposiciones con otros bots.
Si opta por usar un prefijo para su bot, considere usar palabras (`búho`) o
caracteres Unicode únicos (`¨`). Además, debe evitar usar '#' o '@' como
prefijos, ya que pueden usarse para mencionar un canal o un miembro.
Idealmente, el prefijo de su bot debería ser configurable en un servidor por servidor
base, de modo que los propietarios del servidor puedan asegurarse de que cada bot tenga su propio
prefijo de su elección.
    3. ** No seas codicioso **
    Limítese a un pequeño número de prefijos para
reducir el riesgo de colisión con otros.
    4. ** No abuses de las menciones **
    Si responde directamente a un comando, no use un
mencionar, pueden conducir a bucles de respuesta de bot. Las menciones están bien si son de larga duración.
se ejecuta el comando, pero los mensajes privados son una buena alternativa.
2. #### Comandos
    1. ** Tener un comando `info` **
    Debe proporcionar información sobre el bot
como el marco que está usando y la versión utilizada, los comandos `help` y,
lo más importante, quién lo hizo.
    2. ** No responda con "comando no válido" **
    Si un usuario usa un comando que no
no existe, entonces déjelo fallar silenciosamente. No haga que responda con algo como
"comando inválido". Aunque si el comando es correcto, pero los argumentos son incorrectos
entonces está bien responder con "argumentos inválidos". Si hay más de un bot en
un servidor que comparte un prefijo, esto puede resultar en un uso muy desagradable.
3. #### API y comportamiento
    1. ** Sea respetuoso con la API de Discord **
    Bots que abusan y hacen mal uso de Discord
API arruina cosas para todos. Asegúrese de tener en cuenta la limitación de velocidad y el retroceso
en el código de su bot y sea inteligente al usar la API. Asegúrate de pedir
ayuda si no está seguro de la forma correcta de implementar las cosas.
    2. ** Ignora tus propios mensajes y los de otros bots **
    Esto ayuda a prevenir infinitos
bucles automáticos y posibles vulnerabilidades de seguridad. Usando un espacio de ancho cero como `\ u200B`
y `\ u180E` al principio de cada mensaje también evita que su bot
activando los comandos de otros bots. La API de Discord también te dice si un usuario es un bot
(Propiedad `bot` en objetos` User` -
[ver la referencia] (https://discordapp.com/developers/docs/resources/user#user-object)).
    3. ** Mantenga las funciones NSFW bloqueadas en los canales NSFW **
    Todos los comandos / funciones de NSFW solo deberían funcionar en (Discord) canales marcados con NSFW.
    4. ** Use mencionar el bot para ayudar a los usuarios. **
    Permitir una mención como prefijo
("@MyBot help") o agregando una forma de encontrar el prefijo del bot con solo una mención ("@MyBot"
o "@MyBot, ¿cuál es tu prefijo?") ayudará a los usuarios nuevos a tu bot a obtener
empezado. (Asegúrese de que sea cual sea el mensaje, se encuentra fácilmente. Una excelente manera de hacer
esto es incluyéndolo en presencia de su bot). La alternativa es la puntuación de fuerza bruta
personajes para encontrarlo, lo que será difícil para los bots después de 2 y 3. Además, una mención
es el prefijo más exclusivo de todos.

Si tiene una idea para agregar o cambiar este documento, haga una
pull request y podemos discutirlo.
