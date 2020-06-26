

<img src="/repos/recursos-images/logoOadis.png" align="center" alt="logoOadis" style="zoom:100%;" />
​
## CVSS VS CWSS

#### ¿A quién va dirigido este artículo?
Este artículo va dirigido a estudiantes, personas que se encuentren en el mundo de la ciberseguridad y en especial aquellos RedTeamers que requiera información sobre como se maneja la puntuación, el impacto y las características de las vulnerabilidades de TI conforme a CVSS y CWSS
​
## Abstract

En una investigación que realizó el Consejo Asesor Nacional de Infraestructura (CANI) en 2003/2004 llevó al lanzamiento de la versión 1 de CVSS (CVSSv1) en febrero de 2005, con el objetivo de diseñar universalmente un estándar de clasificación de gravedad de las vulnerabilidades del software" Actualmente CVSS se encuentra en su versión 3 lanzado en 2019 y esta bajo la custodia de Forum of Incident Response and Security Teams (FIRST), pero CVSS es completamente abierto, por lo que puede ser utilizado libremente.

El Sistema de puntuación de debilidad común (CWSS) viene de un proyecto que estaba patrocinado por el FFRDC de Seguridad Cibernética Nacional, operado por The MITER Corporation, con el apoyo de US-CERT y la División Nacional de Seguridad Cibernética del Departamento de Seguridad Nacional de los EE. UU. que en un principio viene de Common Weakness Enumeration (CWE). Actualmente se encuentra en la versión 1.0.1 lanzada en Septiembre de 2014

Tanto CWSS como CVSS se crearon en diferentes años con diferentes organizaciones y es desde este punto que se empieza a ver el panorama de hacia donde se fueron dirigiendo cada una.
​
## Introducción

Actualmente, los especialistas de seguridad en TI debe identificar y evaluar vulnerabilidades en diferentes plataformas. Debiendo priorizar las vulnerabilidades que presentan el mayor riesgo por tal motivo, debido a ello el Sistema de puntuación de vulnerabilidad común (CVSS) y el Sistema de puntuación de debilidad comú (CWSS) proporcionan un marco abierto para comunicar las características y los impactos de las vulnerabilidades y debilidades de software de TI. 

EL CVSS consta de 3 grupos: Base, Temporal y Ambiental. Cada grupo produce un puntaje numérico que va de 0 a 10 y un Vector, una representación textual comprimida que refleja los valores utilizados para derivar el puntaje. El grupo Base representa las cualidades porpias de una vulnerabilidad. El grupo temporal refleja las características de una vulnerabilidad que cambian con el tiempo. El grupo ambiental representa las características de una vulnerabilidad que son exclusivas del entorno de cualquier usuario. CVSS permite que los administradores de TI, los proveedores de boletines de vulnerabilidad, los proveedores de seguridad, los proveedores de aplicaciones y los investigadores se beneficien al adoptar este lenguaje común de puntuación de vulnerabilidades de TI.

<img src="/repos/recursos-images/CVSS" align="center" alt="img01" style="zoom:100%;" />

Por otro lado el CWSS está organizado en tres grupos de indicadores: Base Finding, Attack Surface y Environmental. Cada grupo contiene múltiples métricas, también conocidas como factores, que se utilizan para calcular una puntuación CWSS en una debilidad. Proporcionado una medición cuantitativa de las debilidades no fijadas que están presentes dentro de una aplicación de software, un Marco común de análisis de riesgos de debilidad (CWRAF) para priorizar errores de seguridad ("debilidades") que se descubren en aplicaciones de software, los consumidores pueden utilizar CWSS para identificar los tipos más importantes de debilidades para sus dominios comerciales, con el fin de informar sus actividades de adquisición y protección como una parte de la mayor proceso de lograr la garantía del software.

<img src="/repos/recursos-images/CWSS.jpg" align="center" alt="imagen02" style="zoom:100%;" />

Conceptualmente, CVSS y CWSS son muy similares. Sin embargo, hay algunas fortalezas y limitaciones importantes con CVSS. Una de las fortalezas de CVSS radica en su simplicidad. CVSS divide el puntaje general en 14 características separadas dentro de tres grupos métricos: Base, Temporal y Ambiental. Cada característica se descompone en dos o más valores distintos. Por ejemplo, el Vector de acceso refleja la ubicación desde la cual un atacante debe explotar una vulnerabilidad, con posibles valores de Local (autenticado en el sistema local), Remoto (a través de la red) o Red adyacente (en la misma red física o lógica). Además, de la puntuación CVSS proporciona un vector que identifica los valores seleccionados para cada característica.

Con la documentación asociada, la puntuación CVSS es bastante repettitiva, es decir, diferentes analistas generarán la misma puntuación para una vulnerabilidad. Sin embargo, se pueden generar diferentes puntajes cuando la información es incompleta, y es posible una variación significativa si un analista no sigue de cerca la documentación. Si bien el modelo simplificado de Confidencialidad / Integridad / Disponibilidad no proporciona la profundidad y flexibilidad deseadas por algunos expertos en seguridad, CVSS proporciona la consistencia que es útil para los administradores de redes y sistemas no expertos para priorizar las vulnerabilidades. CVSS ha sido ampliamente adoptado, especialmente el uso de puntajes base del grupo métrico Base. Algunas organizaciones usan las porciones Temporal y Ambiental de CVSS, pero esto es relativamente raro, por lo que estos grupos métricos pueden no haber sido suficientemente investigados en el mundo real.

### Escenarios para CVSS vs CWSS

Los escenarios de uso para CVSS difieren de CWSS en las siguientes formas: 

-CVSS asume que una vulnerabilidad ya ha sido descubierta y verificada; CWSS se puede aplicar antes en el proceso, antes de que se demuestre cualquier vulnerabilidad. CVSS no es escalable a la evaluación de seguridad de un solo paquete de software. Una evaluación detallada, como un escaneo de código automatizado, puede informar miles de hallazgos de debilidad. Debido al alto volumen, estos hallazgos a menudo deben puntuarse y priorizarse antes de que puedan examinarse más de cerca para determinar si conducen a vulnerabilidades. CWSS admite explícitamente valores "desconocidos" cuando hay información incompleta.

-La puntuación CVSS no tiene en cuenta la información incompleta, pero la puntuación CWSS tiene soporte incorporado para la información incompleta. Dentro de CWSS, la puntuación puede ser necesaria incluso antes de que se sepa que la debilidad contribuye a una vulnerabilidad. Por ejemplo, la entidad de calificación, ya sea un ser humano o una máquina, puede no conocer el entorno operativo esperado o los requisitos de autenticación durante la calificación inicial de CWSS. En CVSS, la información incompleta a veces es un problema porque muchos informes de vulnerabilidad no contienen todos los detalles relevantes necesarios para la puntuación. Cuando falta información, un enfoque conservador es seleccionar valores que generarán la mayor puntuación CVSS. Este enfoque es utilizado por la National Vulnerability Database y otros, pero puede inflar artificialmente los puntajes. La puntuación conservadora es viable, siempre que la mayoría de los informes de vulnerabilidad contengan información suficiente. Dentro de un contexto de puntuación de debilidad, un alto porcentaje de hallazgos de debilidad no contará con una información crítica, ya que algunas técnicas de detección no podrán determinar de manera confiable si un atacante puede explotar una debilidad sin un análisis más detallado. Como resultado, CWSS proporciona una forma de registrar explícitamente cuando la información no está disponible.

-La puntuación CVSS tiene un gran obstaculo hacia el impacto en el sistema físico; CWSS tiene un pequeño obstaculo a favor de la aplicación que contiene la debilidad. En algunos contextos, los usuarios pueden preferir calificar los problemas en función de su impacto en los datos o la funcionalidad críticos del negocio, lo que podría tener implicaciones limitadas para el impacto en el sistema físico general. Por ejemplo, la puntuación máxima posible para CVSS es a menudo 7.0 para productos Oracle, ya que estos productos generalmente se ejecutan con privilegios limitados. CVSSv3 eliminará este obstaculo hacia el sistema, pero su modelo aún difiere del modelo que utiliza CWSS.

### Otras diferencias entre CWSS y CVSS

Las puntuaciones CWSS y CVSS no son necesariamente comparables. Incluso si los puntajes CWSS (con un máximo de 100) se "normalizan" a un rango CVSS dividiendo por 10 (lo que produciría puntajes equivalentes CVSS dentro del rango de 0 a 10), esto no significa que un puntaje CWSS de 7 es equivalente a un CVSS 7. 

Esta podría ser una característica deseable por algunos consumidores, pero dado que CWSS a menudo mide características completamente diferentes que CVSS, la equivalencia de puntuación podría no ser factible. Además, en la práctica, los puntajes CVSS no siguen una distribución regular, generalmente con un sesgo hacia puntajes altos; Es posible que CWSS tenga una mejor distribución. Algunas organizaciones intentaron modificar CVSS para abordar algunos de los requisitos únicos del análisis de seguridad de software. Los grupos métricos en CWSS son diferentes a los de CVSS, por diseño. Algunos revisores de las primeras versiones de CWSS sugirieron que CWSS adoptara el mismo conjunto de grupos métricos que utiliza CVSS: Base, Temporal y Ambiental. Sin embargo, dado que los puntajes de CWSS se pueden calcular en escenarios tempranos de poca información, muchos factores son de naturaleza "temporal", independientemente del grupo en el que se encuentren; Además, es probable que estos puntajes cambien a medida que un análisis posterior arroje más información sobre la debilidad. CWSS admite el uso de valores como "Desconocido" o "Predeterminado", que se pueden completar más adelante. Un aspecto de CVSS que no está modelado explícitamente en CWSS es la noción de impactos "parciales". Sin embargo, los privilegios adquiridos, la capa de privilegios, el impacto técnico y el impacto comercial son más o menos equivalentes, con un poder más expresivo.

Entendiendo el objetivo que desempeña cada sistema, CVSS y CWSS  se pueden usar juntas al evaluar una amenaza de seguridad para tener un pamorama más aplio a la hora de vizualizar el impacto que tiene una amenaza en una organización y poder tener entregables más robustos que nos permitan dar prioriedad en la remediacion a las amenazas de seguridad más criticas. 


​
### Ejemplo

Tomando el error de Heartbleed bug, que es una vulnerabilidad grave en la popular biblioteca de software criptográfico OpenSSL. Esta debilidad permite robar la información protegida, en condiciones normales, por el cifrado SSL / TLS utilizado para proteger Internet.

Esta vulnerabilidad ya se encuentra clasifica en el CWE-200: Exposure of Sensitive Information to an Unauthorized Actor, lo que nos permite llenar con más precisión el puntaje de CVSS que por lo regurar es de 6.4. Este puntaje puede variar dependiendo de impacto que pueda tener encontrar esta vulnerabildiad dentro de una organización y en que sistema se encuentre. 

<img src="/repos/recursos-images/ejemploCVSS01.jpg" align="center" alt="imagen03" style="zoom:100%;" />

<img src="/repos/recursos-images/ejemploCVSS02.jpg" align="center" alt="imagen04" style="zoom:100%;" />

​
## Referencias
- https://cwe.mitre.org/cwss/cwss_v0.8.html 
- https://cwe.mitre.org/cwss/cwss_v1.0.1.html
- https://es.qwe.wiki/wiki/Common_Vulnerability_Scoring_System
- https://www.first.org/cvss/v2/guide#3-2-Equations
- https://www.welivesecurity.com/la-es/2014/08/04/vulnerabilidades-que-es-cvss-como-utilizarlo/
- https://infosec-handbook.eu/blog/cvss-cve-cwe-capec/
- https://www.oasis-open.org/committees/download.php/62624/Ranking weakness findings.pdf
- https://infosec-handbook.eu/blog/cvss-cve-cwe-capec/

