# Emeset
 
## Emeset el "framework" per alumnes de 2n de DAW
 
Emeset és un framework dissenyat per ser utilitzat en el mòdul professional 7 Desenvolupament d'aplicacions Web en entorn de servidor del cicle de grau superior en desenvolupament d'aplicacions web (DAW).
 
L'objectiu del framework és proveir l'estructura mínima per què l'alumnat de DAW s'introdueixi en l'arquitectura MVC, sense els artificis i facilitats dels frameworks professionals. Per aquest motiu el Framework Emeset té dues versions, Emeset Lite i Emeset.
 
Però, per què ens cal el model vista controlador? Quan comencem programar amb PHP la intuïció ens porta a posar el codi incrustat en l'HTML, així si he de fer un llistat d'usuaris, just davant de la taula d'usuaris puc afegir un bloc de codi PHP on faig la consulta SQL dels usuaris i a partir d'aquí generar la taula amb un foreach.  En molts casos per no obrir i tancar tants blocs de codi pot semblar més còmode generar la taula amb comandes echo. El problema ve quan l'aplicació creix, ens cal afegir més funcionalitats o l'equip de programadors creix. Amb aquesta estructura ens és molt difícil saber en quins fitxers hi ha consultes SQL o quins fitxers tenen codi per restringir l'accés i si hem d'introduir canvis la cosa es complica.

Ens cal una estratègia per organitzar el codi "millor" i així simplificar el manteniment i la llegibilitat del codi, el model-vista-controllador, amb un frontcontroller que permeti utilitzar middleware, és una bona estratègia per crear aplicacions més ben estructurades i més fàcils de mantenir. 

💡 La clau està a separar les responsabilitats. 

Els models tenen la responsabilitat d'accedir a les dades. Qualsevol accés a dades de l'aplicació s'ha de fer a través d'un model. Això ens simplifica el manteniment de l'accés a dades. Si fem algun canvi a la taula d'usuaris, sabem on és el codi que fa les consultes SQL a la taula d'usuaris. També afavoreix la reutilització, hi ha consultes molt habituals, com ara accedir a un element concret o fer un llistat, amb el model aquestes consultes només les haurem d'implementar una vegada.

Els controladors tenen la responsabilitat d'interpretar la petició i generar una resposta adequada, fent servir els models per consultar la informació que els calgui.

Les vistes tenen la responsabilitat de mostrar la informació que ha preparat el controlador amb el format preestablert al client. Una vista pot generar una pàgina HTML, una redirecció, un JSON, un XML, de fet qualsevol cosa que enviem al client (que generalment serà un navegador, però que també pot ser una aplicació consumint una API).

El frontcontroller ha de decidir quin controlador s'executa a partir de la petició i ha d'executar el middleware que tingui assignat abans d'executar-lo.

El middleware és una funció que embolcalla l'execució del controlador i pot executar codi abans de l'execució del controlador o després. El middleware ens permet extreure codi que s'hauria de repetir en molts controladors i que de fet no és una responsabilitat directa d'aquests. L'exemple més clar és el middleware d'autenticació.
 

 
# Emeset Lite
 
Aquesta versió només facilita tres classes (Petició, Resposta, Contenidor) i una estructura base per desenvolupar una aplicació amb l'arquitectura MVC.
 
 
# Emeset
 
Aquesta versió, ja incorpora un FrontController, gestiona l'encaminament i permet assignar més d'un middleware a cada controlador. L'objectiu d'aquesta versió és permetre estructurar més el codi de les aplicacions i introduir el concepte d'encaminador.  És un pas previ al salt a frameworks professionals. 
