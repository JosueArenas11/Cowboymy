%------------------------------------------------------------------------------
% Módulo: procedimiento
% Propósito: Ejecutar un procedimiento que imprime "#YOLO!" en la consola.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define un procedimiento que imprime "#YOLO!" en la salida estándar.
% No retorna ningún valor, ya que su propósito es ejecutar un efecto secundario
% (imprimir en consola).
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(procedimiento).
% 2. Llamar a la función:
% procedimiento:procedure().
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del procedimiento `procedure/0`.
%
% Notas:
% Este es un procedimiento básico que demuestra cómo funcionan las funciones
% que solo tienen efectos secundarios en Erlang.
%------------------------------------------------------------------------------
% Definición del módulo
-module(procedimiento).
% Exportación de la función procedure/0
-export([procedure/0]).
% Definición del procedimiento
% `procedure/0` imprime "#YOLO!" en la consola.
-spec procedure() -> _.
procedure() ->
io:format("#YOLO!~n").
%------------------------------------------------------------------------------
% Módulo: procedimiento
% Propósito: Ejecutar un procedimiento que imprime "#YOLO!" en la consola.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define un procedimiento que imprime "#YOLO!" en la salida estándar.
% No retorna ningún valor, ya que su propósito es ejecutar un efecto secundario
% (imprimir en consola).
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(procedimiento).
% 2. Llamar a la función:
% procedimiento:procedure().
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del procedimiento `procedure/0`.
%
% Notas:
% Este es un procedimiento básico que demuestra cómo funcionan las funciones
% que solo tienen efectos secundarios en Erlang.
%------------------------------------------------------------------------------
% Definición del módulo
-module(procedimiento).
% Exportación de la función procedure/0
-export([procedure/0]).
% Definición del procedimiento
% `procedure/0` imprime "#YOLO!" en la consola.
-spec procedure() -> _.
procedure() ->
io:format("#YOLO!~n").
%------------------------------------------------------------------------------
% Módulo: points
% Propósito: Crear una estructura de datos para un punto 2D.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una estructura de datos para representar un punto en un plano
% 2D utilizando dos números en coma flotante (X e Y). También provee funciones
% para crear un nuevo punto y acceder a sus coordenadas.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(points).
% 2. Crear un nuevo punto:
% P = points:new(1.5, 2.5).
% 3. Obtener las coordenadas X e Y del punto:
% X = points:x(P).
% Y = points:y(P).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación de la estructura de datos `point/0` y funciones
% básicas `new/2`, `x/1` y `y/1`.
%
% Notas:
% Este módulo utiliza mapas para representar puntos. Alternativamente, se puede
% implementar usando tuplas en lugar de mapas.
%------------------------------------------------------------------------------
% Definición del módulo
-module(points).
% Exportación de funciones
-export([new/2, x/1, y/1]).
% Declaración del tipo opaco
% `point/0` es una estructura de datos que contiene dos números en coma flotante, X e Y.
-opaque point() :: #{x => float(), y => float()}.
-export_type([point/0]).
% Especificación de la función new/2
% Crea un nuevo punto con coordenadas X e Y.
-spec new(float(), float()) -> point().
new(X, Y) ->
#{x => X, y => Y}.
% Especificación de la función x/1
% Devuelve la coordenada X de un punto.
-spec x(point()) -> float().
x(#{x := X}) ->
X.
% Especificación de la función y/1
% Devuelve la coordenada Y de un punto.
-spec y(point()) -> float().
y(#{y := Y}) ->
Y.
% Implementación alternativa con mapas
% PointAsAMap = #{x => X, y => Y}.
% Implementación alternativa con tuplas
% PointAsATuple = {X, Y}.
%------------------------------------------------------------------------------
% Módulo: iterar_lista
% Propósito: Iterar sobre los valores de una lista y aplicar una función a cada elemento.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función para iterar sobre una lista y ejecutar la función
% `do_something/1` para cada elemento de la lista. Se utilizan dos implementaciones:
% comprensión de listas y `lists:foreach/2`.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(iterar_lista).
% 2. Llamar a la función:
% iterar_lista:iterar([1, 2, 3, 4, 5]).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo con funciones para iterar sobre listas.
%
% Notas:
% Este módulo aplica una operación (definida en `do_something/1`) a cada elemento
% de una lista, demostrando diferentes maneras de realizar la iteración en Erlang.
%------------------------------------------------------------------------------
% Definición del módulo
-module(iterar_lista).
% Exportación de las funciones
-export([iterar/1, do_something/1]).
% Definición de la función que itera sobre los elementos de una lista
% Aplica la función `do_something/1` a cada elemento de la lista usando dos métodos:
% - Comprensión de listas
% - `lists:foreach/2`
-spec iterar([any()]) -> ok.
iterar(Items) ->
% Implementación usando comprensión de listas
[do_something(X) || X <- Items],
% Implementación alternativa usando lists:foreach
lists:foreach(fun do_something/1, Items),
ok.
% Definición de la función do_something/1
% Aplica una operación a cada elemento (en este ejemplo, simplemente lo imprime).
-spec do_something(any()) -> ok.
do_something(X) ->
io:format("Procesando: ~p~n", [X]).
%------------------------------------------------------------------------------
% Módulo: iterar_indices_valores
% Propósito: Iterar sobre los índices y valores de una lista e imprimirlos.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función para iterar sobre los índices y valores de una lista.
% Utiliza `lists:zip/2` para combinar los índices generados con los valores de la lista.
% Luego imprime cada par índice-valor.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(iterar_indices_valores).
% 2. Llamar a la función:
% iterar_indices_valores:iterar([a, b, c, d]).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo con función para iterar sobre índices y valores.
%
% Notas:
% Este módulo muestra cómo obtener y trabajar con los índices y valores de una lista
% en Erlang, utilizando la función `lists:zip/2`.
%------------------------------------------------------------------------------
% Definición del módulo
-module(iterar_indices_valores).
% Exportación de la función
-export([iterar/1]).
% Definición de la función que itera sobre los índices y valores de una lista
% Usa `lists:zip/2` para emparejar los índices generados con los valores de la lista.
-spec iterar([any()]) -> ok.
iterar(Items) ->
% `lists:seq(1, length(Items))` genera una secuencia de índices del 1 al tamaño de la lista.
% `lists:zip/2` combina los índices con los valores de la lista.
WithIndex = lists:zip(lists:seq(1, length(Items)), Items),
% Imprime la lista de pares índice-valor.
io:format("Índices y Valores: ~p~n", [WithIndex]),
ok.
%------------------------------------------------------------------------------
% Módulo: crear_mapa
% Propósito: Crear un mapa con pares clave-valor como contenido inicial.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función para crear un mapa (associative array) en Erlang
% con algunos pares clave-valor proporcionados como contenido inicial.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(crear_mapa).
% 2. Llamar a la función:
% crear_mapa:nuevo_mapa().
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo con un ejemplo básico de creación de mapas.
%
% Notas:
% Los mapas en Erlang permiten asociar claves con valores. Las claves pueden ser
% átomos, cadenas, binarios u otros tipos de datos.
%------------------------------------------------------------------------------
% Definición del módulo
-module(crear_mapa).
% Exportación de la función
-export([nuevo_mapa/0]).
% Definición de la función que crea un nuevo mapa con contenido inicial
% Crea un mapa con varias claves y valores de diferentes tipos.
-spec nuevo_mapa() -> map().
nuevo_mapa() ->
% Crear un mapa con claves y valores de diferentes tipos.
X = #{one => 1, "two" => 2.0, <<"three">> => [i, i, i]},
% Imprimir el mapa.
io:format("Mapa creado: ~p~n", [X]),
X.
%------------------------------------------------------------------------------
% Módulo: arbol_binario
% Propósito: Definir una estructura de datos para un árbol binario.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una estructura de datos recursiva para un árbol binario.
% Cada nodo del árbol contiene un dato y referencias a sus hijos izquierdo y derecho,
% que también son árboles binarios. La estructura no tiene referencia al nodo padre.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(arbol_binario).
% 2. Crear un árbol binario:
% Arbol = #{data => 10, left => #{data => 5, left => #{data => 3, left => none, right =>
none}, right => none}, right => #{data => 15, left => none, right => none}}.
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Definición de la estructura de datos `binary_tree/1`.
%
% Notas:
% La estructura `binary_tree/1` es un mapa que permite representar árboles binarios
% con datos de tipo `T`. Los hijos izquierdo y derecho también son árboles binarios.
%------------------------------------------------------------------------------
% Definición del módulo
-module(arbol_binario).
% Exportación de tipos
-export_type([binary_tree/1]).
% Definición del tipo de árbol binario
% Un árbol binario tiene un dato y dos hijos, que son también árboles binarios.
-type binary_tree(T) ::
#{ data := T
, left := binary_tree(T) | none
, right := binary_tree(T) | none
}.
% Definición de `none` para representar nodos vacíos
-type none() :: none.
%------------------------------------------------------------------------------
% Módulo: barajar_lista
% Propósito: Generar una permutación aleatoria de los elementos de una lista.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que baraja una lista generando una permutación
% aleatoria de sus elementos. Utiliza la función `rand:uniform/0` para asignar
% valores aleatorios a cada elemento y luego ordena la lista por esos valores.
%
% Dependencias:
% Se requiere que el módulo `rand` esté disponible para generar números aleatorios.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(barajar_lista).
% 2. Llamar a la función:
% barajar_lista:barajar([a, b, c, d]).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para barajar una lista utilizando permutaciones
aleatorias.
%
% Notas:
% La función `rand:uniform/0` genera un número decimal aleatorio entre 0 y 1,
% lo cual se utiliza para ordenar la lista y así barajar los elementos.
%------------------------------------------------------------------------------
% Definición del módulo
-module(barajar_lista).
% Exportación de la función
-export([barajar/1]).
% Definición de la función que baraja una lista
% Genera una permutación aleatoria de los elementos de la lista X.
-spec barajar([any()]) -> [any()].
barajar(X) ->
% Genera una lista de pares {valor_aleatorio, elemento} para cada elemento en X.
% Luego, ordena esta lista por el valor aleatorio y extrae los elementos.
[Y || {_, Y} <- lists:sort([ {rand:uniform(), N} || N <- X])].
%------------------------------------------------------------------------------
% Módulo: verificar_valor
% Propósito: Verificar si una lista contiene un valor específico.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
% Descripción:
% Este módulo define una función para verificar si una lista contiene un valor específico.
% La función utiliza `lists:member/2` para realizar la verificación. También se presentan
% implementaciones alternativas para lograr la misma tarea.
%
% Dependencias:
% Ninguna.
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(verificar_valor).
% 2. Llamar a la función:
% verificar_valor:contiene(3, [1, 2, 3, 4]).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo con funciones para verificar la existencia de un valor en
una lista.
% Notas:
% La función `lists:member/2` es la forma más directa y eficiente de realizar esta verificación.
% También se incluyen implementaciones alternativas para ilustrar cómo se puede hacer de manera
% recursiva.
%------------------------------------------------------------------------------
% Definición del módulo
-module(verificar_valor).
% Exportación de la función
-export([contiene/2]).
% Implementación principal utilizando `lists:member/2`
% Verifica si el valor X está en la lista Lista.
-spec contiene(any(), [any()]) -> boolean().
contiene(X, Lista) ->
lists:member(X, Lista).
% Implementación alternativa utilizando recursión
% Verifica si el valor Value está en la lista. Retorna true si lo encuentra, false si no.
-spec miembro(any(), [any()]) -> boolean().
miembro(_, []) -> false;
miembro(Value, [H|T]) ->
case H of
Value -> true;
_ -> miembro(Value, T)
end.
% Implementación alternativa utilizando un patrón de coincidencia
% Verifica si el valor Value está en la lista. Retorna true si lo encuentra, false si no.
-spec miembro_parecido(any(), [any()]) -> boolean().
miembro_parecido(_, []) -> false;
miembro_parecido(Value, [H|_]) when Value =:= H -> true;
miembro_parecido(Value, [_|T]) -> miembro_parecido(Value, T).
%------------------------------------------------------------------------------
% Módulo: iterar_mapa
% Propósito: Iterar sobre las claves y valores de un mapa e imprimirlos.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que itera sobre un mapa y imprime cada clave
% y su valor correspondiente. Utiliza `maps:fold/3` para recorrer el mapa y
% la función `io:format/2` para la salida.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(iterar_mapa).
% 2. Llamar a la función:
% iterar_mapa:imprimir_mapa(#{"a" => 1, "b" => 2, "c" => 3}).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para iterar sobre claves y valores de un mapa.
%
% Notas:
% La función `maps:fold/3` es útil para recorrer mapas y aplicar una función a cada
clave-valor.
%------------------------------------------------------------------------------
% Definición del módulo
-module(iterar_mapa).
% Exportación de la función
-export([imprimir_mapa/1]).
% Definición de la función que itera sobre un mapa e imprime las claves y valores
% Itera sobre el mapa MyMap e imprime cada clave y valor.
-spec imprimir_mapa(map()) -> ok.
imprimir_mapa(MyMap) ->
% Utiliza maps:fold/3 para iterar sobre el mapa.
maps:fold(
fun(K, V, Acc) ->
% Imprime la clave y el valor.
io:format("~p: ~p~n", [K, V]),
Acc
end,
ok,
MyMap
).
%------------------------------------------------------------------------------
% Módulo: seleccionar_aleatorio_flotante
% Propósito: Seleccionar un número flotante aleatorio en el intervalo [a..b).
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que genera un número flotante aleatorio en el intervalo
% [a..b), donde `a` es inclusivo y `b` es exclusivo. Utiliza la función `rand:uniform/0`
% para generar un número aleatorio en el rango [0, 1) y lo escala al intervalo deseado.
%
% Dependencias:
% Se requiere que el módulo `rand` esté disponible para generar números aleatorios.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(seleccionar_aleatorio_flotante).
% 2. Llamar a la función:
% seleccionar_aleatorio_flotante:aleatorio(2.0, 5.0).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para seleccionar un número flotante aleatorio en
un intervalo.
%
% Notas:
% La precondición es que `a` debe ser menor que `b` para asegurar un intervalo válido.
%------------------------------------------------------------------------------
% Definición del módulo
-module(seleccionar_aleatorio_flotante).
% Exportación de la función
-export([aleatorio/2]).
% Definición de la función que selecciona un número flotante aleatorio en [a..b)
% La precondición es que A < B.
-spec aleatorio(float(), float()) -> float().
aleatorio(A, B) when A < B ->
% Genera un número aleatorio en el intervalo [A, B).
A + (B - A) * rand:uniform().
%------------------------------------------------------------------------------
% Módulo: seleccionar_aleatorio_entero
% Propósito: Seleccionar un número entero aleatorio en el intervalo [a..b].
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que genera un número entero aleatorio en el intervalo
% [a..b], donde tanto `a` como `b` son inclusivos. Utiliza la función `crypto:rand_uniform/2`
% para generar un número aleatorio en el rango deseado.
%
% Dependencias:
% Se requiere que el módulo `crypto` esté disponible para generar números aleatorios.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(seleccionar_aleatorio_entero).
% 2. Llamar a la función:
% seleccionar_aleatorio_entero:aleatorio(3, 7).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para seleccionar un número entero aleatorio en
un intervalo.
%
% Notas:
% La precondición es que `a` debe ser menor que `b` para asegurar un intervalo válido.
%------------------------------------------------------------------------------
% Definición del módulo
-module(seleccionar_aleatorio_entero).
% Exportación de la función
-export([aleatorio/2]).
% Definición de la función que selecciona un número entero aleatorio en [a..b]
% La precondición es que A < B.
-spec aleatorio(integer(), integer()) -> integer().
aleatorio(A, B) when A < B ->
% Genera un número entero aleatorio en el intervalo [A, B].
crypto:rand_uniform(A, B + 1).
%------------------------------------------------------------------------------
% Módulo: estructura_arbol
% Propósito: Definir una estructura de árbol recursiva donde cada nodo puede tener cero
o más hijos.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define un registro para representar un nodo en un árbol. Cada nodo puede
tener
% un valor y una lista de nodos hijos. La estructura es recursiva, ya que cada nodo puede
contener
% otros nodos como hijos.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(estructura_arbol).
% 2. Crear un nodo y un árbol:
% NodoHijo = #node{value = 1}.
% NodoPadre = #node{value = 2, children = [NodoHijo]}.
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para definir una estructura de árbol.
%
% Notas:
% La estructura es recursiva porque cada nodo puede contener una lista de nodos hijos,
% los cuales son instancias de la misma estructura.
%------------------------------------------------------------------------------
% Definición del módulo
-module(estructura_arbol).
% Exportación del registro
-export([node/0]).
% Definición del registro para un nodo en el árbol
-record(node, {
value :: any(), % Valor almacenado en el nodo
children = [] :: [node#{}] % Lista de hijos, que son nodos
}).
%------------------------------------------------------------------------------
% Módulo: invertir_lista
% Propósito: Invertir el orden de los elementos de una lista.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que invierte el orden de los elementos de una lista.
% Utiliza la función `lists:reverse/1` para realizar la inversión de la lista.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(invertir_lista).
% 2. Llamar a la función:
% invertir_lista:invertir([1, 2, 3, 4]).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para invertir una lista.
%
% Notas:
% La función `lists:reverse/1` realiza la inversión de la lista, creando una nueva lista
% con el orden de los elementos invertido.
%------------------------------------------------------------------------------
% Definición del módulo
-module(invertir_lista).
% Exportación de la función
-export([invertir/1]).
% Definición de la función que invierte el orden de los elementos de una lista
% Toma una lista y devuelve una nueva lista con los elementos en orden inverso.
-spec invertir([any()]) -> [any()].
invertir(List) ->
lists:reverse(List).
%------------------------------------------------------------------------------
% Módulo: buscar_item
% Propósito: Buscar un ítem X en una matriz 2D M y devolver las coordenadas (i, j) de la
celda que contiene el ítem.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%% Descripción:
% Este módulo define una función que busca un ítem en una matriz 2D. Si el ítem se
encuentra,
% devuelve las coordenadas de la celda en la que se encuentra. Si el ítem no se encuentra,
la función
% lanza una excepción `notfound`.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(buscar_item).
% 2. Llamar a la función:
% buscar_item:search(5, [[1, 2, 3], [4, 5, 6], [7, 8, 9]]).
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para buscar un ítem en una matriz 2D.
%
% Notas:
% La función devuelve una tupla `{i, j}` con las coordenadas del ítem si se encuentra,
% y lanza una excepción si el ítem no se encuentra en la matriz.
%------------------------------------------------------------------------------
% Definición del módulo
-module(buscar_item).
% Exportación de la función
-export([search/2]).
% Definición de la función que busca un ítem en una matriz 2D
% Toma un ítem X y una matriz M, y devuelve las coordenadas {i, j} del ítem.
-spec search(T, [[T]]) -> {pos_integer(), pos_integer()}.
search(X, M) -> search(X, M, 1).
search(_, [], _) -> throw(notfound);
search(X, [R|Rs], RN) ->
case search_row(X, R) of
notfound -> search(X, Rs, RN+1);
CN -> {RN, CN}
end.
search_row(X, Row) -> search_row(X, Row, 1).
search_row(_, [], _) -> notfound;
search_row(X, [X|_], CN) -> CN;
search_row(X, [_|Elems], CN) -> search_row(X, Elems, CN+1).
%------------------------------------------------------------------------------
% Módulo: convertir_a_entero
% Propósito: Convertir una cadena de texto a un número entero.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que convierte una cadena de texto que representa un
número entero
% en un valor entero. La función utiliza `list_to_integer/1` para realizar la conversión.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(convertir_a_entero).
% 2. Llamar a la función:
% convertir_a_entero:convertir("123").
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para convertir una cadena de texto a un entero.
%
% Notas:
% La función `list_to_integer/1` toma una cadena de texto en formato decimal y devuelve el
valor entero correspondiente.
%------------------------------------------------------------------------------
% Definición del módulo
-module(convertir_a_entero).
% Exportación de la función
-export([convertir/1]).
% Definición de la función que convierte una cadena de texto a un entero
% Toma una cadena de texto en formato decimal y devuelve el número entero
correspondiente.
-spec convertir(string()) -> integer().
convertir(S) ->
list_to_integer(S).
%------------------------------------------------------------------------------
% Módulo: convertir_a_cadena
% Propósito: Convertir un número real a una cadena de texto con 2 decimales.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que convierte un número real en su representación en
cadena de texto
% con 2 dígitos decimales. La función utiliza `io_lib:format/2` para realizar la conversión.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(convertir_a_cadena).
% 2. Llamar a la función:
% convertir_a_cadena:convertir(123.456).
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para convertir un número real a una cadena con 2
decimales.
%
% Notas:
% La función `io_lib:format/2` toma un formato de cadena con especificador `~.2f` para
indicar 2 decimales
% y devuelve la cadena de texto resultante.
%------------------------------------------------------------------------------
% Definición del módulo
-module(convertir_a_cadena).
% Exportación de la función
-export([convertir/1]).
% Definición de la función que convierte un número real a una cadena con 2 decimales
% Toma un número real y devuelve su representación en cadena con 2 dígitos decimales.
-spec convertir(float()) -> string().
convertir(X) ->
io_lib:format("~.2f", [X]).
%------------------------------------------------------------------------------
% Módulo: asignar_palabra_japonesa
% Propósito: Asignar la palabra japonesa "ネコ" a una cadena en formato binario.
%
% Autor: Josue Arenas
% Fecha: 9 de Septiembre de 2024
% Versión: 1.0
%
% Descripción:
% Este módulo define una función que asigna la palabra japonesa "ネコ" (que significa
"gato" en japonés)
% a una variable en formato binario. La palabra se inicializa utilizando
`unicode:characters_to_binary/1`.
%
% Dependencias:
% Ninguna.
%
% Ejemplo de Uso:
% 1. Compilar el módulo:
% c(asignar_palabra_japonesa).
% 2. Llamar a la función:
% asignar_palabra_japonesa:asignar().
%
% Historial de Cambios:
% 09/09/2024 - 1.0 - Creación del módulo para asignar una palabra japonesa a una cadena
binaria.
%
% Notas:
% La función `unicode:characters_to_binary/1` convierte una cadena de texto Unicode a su
representación en binario.
%------------------------------------------------------------------------------
% Definición del módulo
-module(asignar_palabra_japonesa).
% Exportación de la función
-export([asignar/0]).
% Definición de la función que asigna la palabra japonesa "ネコ" a una cadena binaria
% La función convierte la cadena "ネコ" a su representación en binario utilizando Unicode.
-spec asignar() -> binary().
asignar() ->
S = unicode:characters_to_binary("ネコ"),
S.
