---
title: "Guía de especificaciones de ingeniería para evaluar fabricantes de paneles de alarma comerciales: topología RS-485, comunicación de doble vía e interoperabilidad del receptor CMS"
date: 2026-09-16T09:00:00+08:00
draft: false
type: "posts"
description: "Guía técnica y de compras para evaluar paneles de alarma comerciales mediante la topología del bus RS-485, la Arquitectura de alimentación, la Comunicación de alarma de doble vía, el Protocolo SIA DC-09 de reporte de eventos IP, la Estructura de codificación Contact ID y la Interoperabilidad del receptor CMS."
keywords:
  - "Commercial Alarm Panel Manufacturer"
  - "Commercial Alarm Panel"
  - "RS-485 Alarm Panel"
  - "RS-485 Bus Topology"
  - "SIA DC-09"
  - "CMS Receiver Interoperability"
  - "Multi-Path Alarm Communication"
  - "Intrusion Alarm Panel Manufacturer"
  - "Alarm Panel Procurement"
  - "Alarm System Integrator"
---

La evaluación de un fabricante de paneles de alarma comerciales no debe limitarse al precio del equipo ni al número nominal de zonas. Para un distribuidor, importador, propietario de una marca OEM o integrador de sistemas de seguridad, la cuestión técnica central es si el fabricante puede proporcionar una plataforma documentada y comprobable desde la red de campo hasta el centro de monitoreo.

En un proyecto comercial, un panel puede registrar correctamente un evento y aun así producir un resultado operativo incorrecto si la alimentación del bus no mantiene suficiente margen, si un dispositivo RS-485 queda fuera de línea, si la comunicación de alarma de doble vía no detecta un fallo de sesión, si el protocolo declarado no coincide con la implementación real o si el receptor CMS acepta el mensaje pero el mapeo del evento no coincide con la intención original del panel.

La evaluación debe separar, por tanto, las funciones declaradas de los comportamientos demostrados mediante documentación, cálculo y prueba.

Como referencia documental de una plataforma de fabricante, puede consultarse la [documentación publicada del Athenalarm AS-9000](https://athenalarm.com/burglar-alarm/intrusion-alarm-panel/alarm-control-panel/).

![Sistema de monitoreo de alarmas en red con panel, comunicación y centro de monitoreo](https://files.athenalarm.com/images/Athenalarm-network-alarm-monitoring-system-1-1024.jpg)

## Topología y dimensionamiento del bus RS-485

El bus RS-485 debe evaluarse como una capa física de expansión dentro de un sistema de alarma comercial. La existencia de una interfaz RS-485 no demuestra, por sí sola, que el sistema sea adecuado para la instalación prevista. La evaluación debe partir de la relación entre topología, carga de dispositivos, alimentación, características del cable, direccionamiento, terminación, interferencia electromagnética y comportamiento de diagnóstico.

En una arquitectura comercial, la Topología del bus RS-485 determina cómo se distribuyen los dispositivos y módulos de expansión alrededor del panel. La topología exacta debe proceder del fabricante, porque las condiciones de funcionamiento dependen de la implementación concreta del panel, de los módulos y de las condiciones eléctricas especificadas.

### La distancia de RS-485 debe interpretarse como un problema eléctrico

Una especificación aislada de distancia máxima no es suficiente para aprobar un diseño.

La distancia de comunicación y la distancia de entrega de alimentación deben evaluarse por separado. Un recorrido puede conservar capacidad de comunicación mientras la tensión disponible en el dispositivo remoto cae por debajo del margen necesario para mantener un funcionamiento estable.

La relación básica de la Caída de tensión puede expresarse como:

`Vdrop = I × Rtotal`

Para un circuito de alimentación de dos conductores:

`Rtotal = Rwire × Lround-trip`

La longitud eléctrica del circuito incluye el conductor de ida y el conductor de retorno. La carga total debe considerar todos los dispositivos que utilizan la Arquitectura de alimentación asociada al recorrido.

La evaluación debe conservar la siguiente relación causal:

`carga de dispositivos, demanda de corriente, resistencia del conductor, Caída de tensión, tensión disponible en el extremo remoto y estabilidad de comunicación`

Un valor nominal de distancia no debe tratarse como una garantía independiente del resto de las variables.

Para aprobar una instalación comercial deben solicitarse, como mínimo, los datos siguientes:

- Tipo y sección del conductor utilizados en la especificación del fabricante.
- Carga máxima de dispositivos admitida en la configuración prevista.
- Consumo de los dispositivos y módulos RS-485 conectados al mismo recorrido.
- Método de distribución de alimentación.
- Tensión mínima requerida en el extremo remoto.
- Supuestos de longitud y resistencia del cable.
- Topología aprobada por el fabricante.
- Requisitos de terminación.
- Restricciones de ramificación.
- Método de direccionamiento.
- Condiciones ambientales relevantes para la instalación.
- Procedimiento de diagnóstico cuando un dispositivo aparece fuera de línea.

### La carga del bus no debe evaluarse solamente por número de dispositivos

Dos instalaciones con el mismo número de módulos pueden presentar condiciones eléctricas diferentes.

La demanda total depende del consumo de los dispositivos, del consumo del panel, de teclados, comunicadores, sirenas, módulos RS-485 y salidas auxiliares. La condición de alarma puede modificar la carga respecto del estado normal.

La especificación de capacidad debe distinguir, cuando corresponda:

- Carga de comunicación.
- Carga de dispositivos alimentados.
- Consumo continuo.
- Consumo durante alarma.
- Carga máxima simultánea.
- Distribución de la alimentación entre recorridos.

La relación entre cantidad de dispositivos y corriente debe evaluarse antes de interpretar la distancia disponible.

### La Topología del bus RS-485 debe proceder del fabricante

El diseño debe identificar claramente la topología de bus principal y las limitaciones de ramificación.

No debe asumirse que cualquier configuración física es equivalente. La presencia de una interfaz RS-485 no convierte automáticamente una topología arbitraria en una arquitectura aprobada.

La documentación de ingeniería debería permitir responder a las siguientes preguntas:

- ¿Cuál es la topología aprobada para el panel?
- ¿Qué límites de ramificación deben respetarse?
- ¿Dónde se ubica la terminación?
- ¿Qué condiciones de direccionamiento deben cumplirse?
- ¿Qué número de dispositivos puede operar bajo la configuración propuesta?
- ¿Qué distribución de alimentación se exige?
- ¿Qué comportamiento presenta el sistema cuando un módulo queda fuera de línea?

La terminación debe evaluarse como parte de la implementación concreta. No debe transformarse una práctica habitual de una determinada arquitectura RS-485 en una regla universal independiente de la documentación del fabricante.

### La interferencia electromagnética puede convertir una puesta en marcha estable en una instalación intermitente

Un bus RS-485 puede funcionar durante la puesta en marcha y volverse intermitente cuando aumentan la distancia, la carga eléctrica, la capacitancia del cable, los problemas de puesta a tierra o la Interferencia electromagnética.

Por eso, la evaluación de una instalación comercial debe considerar:

- Apantallamiento del cable cuando la especificación del sistema lo requiera.
- Separación y disposición física de cableado de señal y fuentes de perturbación.
- Condiciones de puesta a tierra.
- Protección física del cable.
- Estado de conectores y terminaciones.
- Condiciones de interferencia presentes en el emplazamiento.
- Comportamiento del sistema durante las pruebas de campo.

La protección no debe entenderse como una característica aislada del producto. La estabilidad del bus depende también de las condiciones de instalación.

La fuente de referencia incluye la referencia documental [IEC 61000-4-5](https://webstore.iec.ch/en/publication/4223), que debe conservarse como enlace documental del material de origen.

### Diagnóstico de dispositivo fuera de línea del bus

Cuando un módulo RS-485 queda fuera de línea, el diagnóstico debe aislar primero la capa en la que aparece la alteración.

Un procedimiento de diagnóstico basado en evidencia debe comprobar, en este orden lógico:

1. Confirmar la presencia de alimentación en el dispositivo afectado.
2. Verificar la tensión disponible en el extremo del recorrido bajo la carga real.
3. Revisar continuidad y estado físico del cableado.
4. Comparar la instalación real con la Topología del bus RS-485 aprobada.
5. Verificar terminación y condiciones de ramificación.
6. Comprobar direccionamiento y posibles conflictos de dirección.
7. Revisar las condiciones de puesta a tierra y apantallamiento.
8. Evaluar la Interferencia electromagnética presente en el entorno.
9. Confirmar el comportamiento del módulo individual después de aislar las causas del recorrido.

Este enfoque permite distinguir entre una incidencia de alimentación, una incidencia de cableado, una incidencia de topología, una incidencia de terminación, una incidencia de direccionamiento y una incidencia de interferencia.

El Diagnóstico de dispositivo fuera de línea del bus debe servir también para detectar un Fallo silencioso. El objetivo no es solamente devolver un módulo a estado operativo, sino producir evidencia suficiente para identificar la causa y evitar la repetición del problema.

![Panel de alarma comercial utilizado como referencia de arquitectura de control e integración](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel.jpg)

### Evidencia que debe solicitarse al fabricante

Antes de aprobar una instalación comercial, el distribuidor o integrador debería solicitar:

| Área de evaluación | Evidencia requerida |
| --- | --- |
| Topología del bus RS-485 | Esquema de instalación aprobado y límites de configuración |
| Carga | Capacidad máxima de dispositivos y supuestos eléctricos |
| Alimentación | Datos de corriente, distribución y tensión mínima |
| Cableado | Características de conductor y supuestos de recorrido |
| Terminación | Ubicación y condiciones especificadas por el fabricante |
| Direccionamiento | Método de asignación y restricciones |
| Interferencia electromagnética | Requisitos de instalación y apantallamiento |
| Diagnóstico | Método para identificar dispositivos fuera de línea |
| Prueba de campo | Resultados bajo la topología y carga reales |

La evidencia debe permitir recuperar una respuesta independiente a dos preguntas: qué condiciones se necesitan antes de aprobar el bus y qué síntomas obligan a revisar primero la capa eléctrica.

## Arquitectura de alimentación y batería de respaldo

La Arquitectura de alimentación debe evaluarse como una función independiente de la capacidad nominal de zonas.

El número de zonas no determina por sí solo la capacidad eléctrica del sistema. La demanda total incluye el panel, detectores, módulos RS-485, teclados, comunicadores, sirenas y salidas auxiliares. También debe distinguirse el consumo normal del consumo durante alarma.

Una plataforma con más zonas puede presentar una demanda eléctrica menor o mayor que otra con menos zonas, dependiendo de los dispositivos conectados y de la carga prevista.

### La capacidad de alimentación debe calcularse con la carga real

La evaluación debe comenzar con una lista de cargas conectadas.

| Elemento | Estado normal | Estado de alarma | Consideración de diseño |
| --- | --- | --- | --- |
| Panel | Registrar consumo nominal | Registrar comportamiento en alarma | Base de la demanda |
| Detectores | Determinar consumo individual y total | Según condición de alarma | Impacto acumulado |
| Módulos RS-485 | Determinar consumo total | Según dispositivos asociados | Relación con el recorrido |
| Teclados | Determinar consumo | Según actividad prevista | Parte de la carga continua |
| Comunicadores | Determinar consumo | Considerar transmisión y recuperación | Puede afectar la demanda durante fallo |
| Sirenas | Determinar consumo | Considerar activación | Puede elevar significativamente la carga |
| Salidas auxiliares | Determinar carga conectada | Considerar cargas en alarma | Revisar simultaneidad |

La relación de dimensionamiento debe conservarse como una secuencia de cálculo:

1. Identificar todos los dispositivos conectados.
2. Determinar la corriente de cada carga.
3. Sumar la corriente total en estado normal.
4. Calcular la corriente total en estado de alarma.
5. Evaluar la distribución de corriente por cada recorrido.
6. Comprobar la tensión disponible en los dispositivos remotos.
7. Determinar la capacidad de batería necesaria.
8. Verificar el comportamiento durante fallo de red eléctrica.

### La distribución de alimentación afecta al bus RS-485

La relación entre alimentación y bus RS-485 no debe romperse durante la evaluación.

Una distribución de alimentación aparentemente suficiente en el panel puede producir una tensión insuficiente al final de un recorrido largo debido a la resistencia del conductor y a la demanda de los dispositivos.

La evaluación debe comprobar:

- Fuente de alimentación utilizada.
- Corriente disponible.
- Longitud de los recorridos.
- Demanda acumulada.
- Distribución de carga entre recorridos.
- Tensión disponible en los puntos remotos.
- Condición de máxima carga simultánea.
- Comportamiento durante alarma.

Cuando se utiliza una técnica de inyección o distribución auxiliar, esta debe evaluarse conforme a la arquitectura concreta del fabricante y al escenario de instalación previsto. No debe convertirse una técnica específica en una regla universal fuera de su contexto.

### La batería de respaldo debe calcularse a partir de carga y autonomía

Una relación preliminar puede expresarse como:

`Cbatería ≈ (Icarga × tautonomía) / η`

La expresión sirve como modelo inicial. La capacidad real debe considerar el comportamiento de la batería, el envejecimiento, la temperatura, la eficiencia del sistema, el consumo durante alarma y las condiciones de carga.

La fuente de referencia enlaza [BS EN 50131-6:2017+A1:2021](https://knowledge.bsigroup.com/products/alarm-systems-intrusion-and-hold-up-systems-power-supplies-3) y [BS EN 50131-3:2026](https://knowledge.bsigroup.com/products/alarm-systems-intrusion-and-hold-up-systems-control-and-indicating-equipment). Estos enlaces deben conservarse como referencias documentales del contenido de origen.

La documentación de compra no debería limitarse a una cifra de horas de autonomía. Debe identificar el modelo de carga utilizado para determinar esa autonomía y las condiciones bajo las cuales la capacidad sigue siendo válida.

### La autonomía debe verificarse bajo el escenario de carga definido

Una prueba de aceptación debe reproducir, en la medida definida por el proyecto, la carga normal y las condiciones de alarma relevantes.

El comprador debería solicitar:

- Consumo del panel.
- Capacidad de alimentación auxiliar.
- Consumo de módulos RS-485.
- Consumo de comunicadores.
- Consumo de sirenas.
- Demanda durante alarma.
- Capacidad de batería.
- Condiciones de carga de batería.
- Modelo de autonomía utilizado.
- Condiciones ambientales consideradas.
- Evidencia de la prueba de respaldo.

La finalidad es comprobar que la Arquitectura de alimentación sigue siendo válida con la topología física y la carga real del proyecto.

### Criterio de compra

Una especificación de “X zonas” no sustituye a una especificación eléctrica verificable.

El distribuidor o integrador debe exigir una correspondencia verificable entre:

`carga conectada, distribución de alimentación, tensión disponible, consumo en alarma, capacidad de batería y autonomía requerida`

Cuando esta cadena no está documentada, el riesgo de campo permanece oculto hasta la puesta en marcha o durante un fallo de alimentación.

## Resiliencia de comunicaciones de doble vía

La Comunicación de alarma de doble vía no debe definirse como la simple presencia de dos interfaces.

La cuestión técnica es si las rutas son realmente independientes, cómo se detectan sus fallos, cómo se produce la conmutación y cómo se confirma la recuperación.

Dos interfaces pueden compartir procesador, alimentación, configuración de cuenta y otros elementos comunes del panel. Por ello, contar interfaces no equivale automáticamente a contar rutas independientes.

### Las rutas deben evaluarse por dependencia real

La evaluación debe distinguir las dependencias de cada ruta.

| Ruta | Dependencias que deben identificarse | Condición de evaluación |
| --- | --- | --- |
| Ethernet | LAN, proveedor, encaminamiento, cortafuegos y sesión de aplicación | Confirmar que la sesión de reporte sigue operativa |
| Celular | Operador, cobertura, SIM, APN y congestión | Confirmar que la ruta permite el intercambio operativo con el receptor |
| Elementos comunes | Procesador, alimentación y configuración del panel | Determinar si un fallo común puede afectar a ambas rutas |

La disponibilidad física del enlace no demuestra por sí sola la disponibilidad de la aplicación.

Una interfaz Ethernet puede mostrar enlace disponible mientras la sesión de aplicación con el receptor deja de progresar.

Una ruta celular puede mostrar registro de comunicación y aun así no completar la sesión necesaria para el reporte del evento.

### La detección de fallos debe definirse por condición

La especificación de failover debe distinguir entre distintas condiciones de fallo.

- Pérdida física del enlace.
- Pérdida de sesión de aplicación.
- Fallo de supervisión.
- Ausencia del reconocimiento esperado.
- Reintentos de transmisión.
- Restauración del servicio.
- Estados transitorios durante la reconexión.
- Posible duplicación de eventos.

Estas condiciones no deben agruparse en una sola definición de “fallo de comunicación”.

Cada condición puede producir una respuesta diferente del sistema.

### El Latido de supervisión permite detectar fallos que no aparecen como pérdida física del enlace

El Latido de supervisión debe evaluarse como mecanismo para verificar que la ruta de comunicación sigue siendo operativa a nivel de aplicación.

Su función debe relacionarse con:

- Periodicidad de supervisión.
- Respuesta esperada.
- Temporización de pérdida.
- Reconocimiento del receptor.
- Reintentos.
- Estado informado al centro de monitoreo.
- Recuperación después de restauración.
- Comportamiento frente a duplicados.

Una ruta aparentemente disponible no debe considerarse operativa si el intercambio supervisado con el receptor ya no progresa.

### La conmutación debe definirse por estado de fallo

La especificación debería indicar, para cada ruta:

| Condición | Detección | Conmutación | Evidencia de recuperación |
| --- | --- | --- | --- |
| Pérdida física del enlace | Estado de interfaz | Según lógica del fabricante | Reanudación del servicio |
| Pérdida de sesión | Supervisión de aplicación | Según temporización definida | Sesión restablecida |
| Ausencia de reconocimiento | Falta de ACK esperado | Según política de reintento | ACK recibido |
| Fallo de supervisión | Latido de supervisión no confirmado | Según temporización | Supervisión restaurada |
| Restauración | Confirmación de ruta recuperada | Retorno según lógica definida | Registro de recuperación |

La detección del fallo, la conmutación posterior y la recuperación del servicio deben documentarse como comportamientos separados.

### La prueba debe simular cada ruta de forma independiente

La validación debe incluir, como mínimo:

1. Operación normal de la ruta primaria.
2. Fallo de la ruta primaria.
3. Detección del fallo.
4. Inicio de la condición de respaldo.
5. Transmisión por la ruta secundaria.
6. Confirmación mediante reconocimiento del receptor.
7. Registro del estado de fallo.
8. Restauración de la ruta primaria.
9. Comportamiento durante la reconexión.
10. Verificación de posibles eventos duplicados.

La prueba debe producir registros, no solamente una observación verbal de que el sistema “cambia automáticamente”.

### La independencia de las rutas es una cuestión arquitectónica

El comprador debe identificar las dependencias comunes.

La siguiente matriz resulta útil:

| Elemento común | Ruta Ethernet | Ruta celular | Riesgo a evaluar |
| --- | --- | --- | --- |
| Alimentación del panel | Sí | Sí | Un fallo común puede afectar a ambas rutas |
| Procesador del panel | Sí | Sí | Una incidencia de procesamiento puede comprometer ambas rutas |
| Cuenta de monitoreo | Sí | Sí | Configuración incorrecta puede afectar al reporte |
| Receptor | Sí | Sí | Un problema del receptor puede afectar a ambas rutas |
| Medio de transmisión | LAN | Celular | Permite evaluar independencia de infraestructura |

La Comunicación de alarma de doble vía debe entenderse como resiliencia de arquitectura y no como cantidad de interfaces físicas.

![Panel de alarma utilizado como referencia de plataforma de comunicaciones y control](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel-2.jpg)

La fuente de referencia incluye además un recurso audiovisual relacionado con monitorización de alarmas. Se conserva el enlace y su miniatura para mantener la trazabilidad del material de origen:

[![Monitorización de alarmas y arquitectura de comunicación](https://img.youtube.com/vi/cIBxzrVTb4A/0.jpg)](https://www.youtube.com/watch?v=cIBxzrVTb4A)

### Evidencia de fabricante para la Comunicación de alarma de doble vía

Antes de aprobar la arquitectura, el fabricante debería aportar:

- Diagrama lógico de las rutas.
- Dependencias de cada ruta.
- Condiciones de fallo detectadas.
- Condiciones exactas de conmutación.
- Temporizaciones.
- Política de reintentos.
- Comportamiento de reconocimiento.
- Comportamiento de restauración.
- Configuración del Latido de supervisión.
- Registros de pruebas.
- Compatibilidad con el receptor y CMS seleccionados.

## SIA DC-09, Contact ID y evidencia de implementación

La existencia de una declaración de compatibilidad con un protocolo no demuestra por sí sola una implementación interoperable.

La compra debe distinguir entre:

`protocolo declarado, implementación concreta y resultado observado en la prueba`

El Protocolo SIA DC-09 de reporte de eventos IP debe evaluarse mediante una matriz concreta que identifique versión, transporte, eventos, reconocimiento, seguridad, receptor y firmware.

### Qué debe verificarse en una implementación SIA DC-09

La evaluación debe identificar:

- Versión exacta implementada.
- Método de transporte.
- Clases de eventos soportadas.
- Receptor objetivo.
- Configuración de seguridad.
- Comportamiento de reconocimiento.
- Reintentos.
- Versión de firmware del panel.
- Versión de firmware del comunicador.
- Configuración de cuenta.
- Mapeo de eventos.
- Registro de interoperabilidad.

Una frase genérica como “admite SIA” no proporciona suficiente evidencia para aprobar una implementación en un proyecto comercial.

El [contenido de referencia de SIA DC-09-2026](https://www.securityindustry.org/industry-standards/dc-09-2026/) debe conservarse como enlace documental del material de origen. La revisión concreta que se contrate debe quedar identificada en la documentación del proyecto.

### Contact ID debe mantenerse conceptualmente separado

La Estructura de codificación Contact ID debe tratarse como una estructura diferenciada y no como un sinónimo del Protocolo SIA DC-09 de reporte de eventos IP.

La documentación de compra debe indicar claramente:

- Si Contact ID es compatible.
- Qué función cumple dentro de la arquitectura.
- Cómo se transporta.
- Cómo se reconoce.
- Qué receptor lo interpreta.
- Cómo se representa el evento en el CMS.
- Qué firmware interviene.

La fuente de referencia enlaza la documentación [DC-05-2016 de SIA](https://www.securityindustry.org/industry-standards/dc-05-2016/). El enlace debe mantenerse como referencia del contenido original sin sustituir la documentación contractual que corresponda al proyecto.

### La declaración de protocolo no equivale a interoperabilidad

Una implementación puede declarar un protocolo y aun así presentar diferencias de comportamiento según:

- Receptor.
- Configuración de cuenta.
- Firmware.
- Transporte.
- Seguridad.
- Reconocimiento.
- Mapeo de eventos.

Por eso la prueba debe seguir una cadena observable:

1. El panel genera el evento.
2. El evento queda registrado en el panel.
3. El comunicador procesa el evento.
4. Se establece la transmisión.
5. El receptor recibe y procesa el mensaje.
6. El receptor devuelve el reconocimiento esperado.
7. El CMS interpreta el evento.
8. El mapeo del evento coincide con la intención original.

La prueba debe distinguir aceptación, reconocimiento, decodificación y mapeo.

### La matriz de implementación debe ser reproducible

Una matriz de compra puede utilizar el siguiente formato:

| Parámetro | Valor que debe documentarse |
| --- | --- |
| Protocolo | Protocolo SIA DC-09 de reporte de eventos IP o Estructura de codificación Contact ID, según la función evaluada |
| Versión | Revisión exacta |
| Transporte | Método utilizado |
| Seguridad | Configuración aplicada |
| Eventos | Clases de eventos soportadas |
| Receptor | Modelo y versión |
| Panel | Modelo y versión de firmware |
| Comunicador | Modelo y versión de firmware |
| Cuenta | Configuración usada en prueba |
| Reconocimiento | Comportamiento esperado y observado |
| Mapeo | Correspondencia entre evento y representación en CMS |
| Evidencia | Registro reproducible de interoperabilidad |

La documentación debería permitir reconstruir la prueba sin depender de una explicación verbal del proveedor.

## Interoperabilidad del receptor CMS de extremo a extremo

La Interoperabilidad del receptor CMS debe validarse como una prueba de extremo a extremo.

No es suficiente demostrar que el panel genera un evento ni que el receptor acepta un mensaje.

La cadena completa debe considerar:

1. Generación del evento en el panel.
2. Registro del evento.
3. Procesamiento por el comunicador.
4. Transmisión por la red correspondiente.
5. Recepción del mensaje.
6. Decodificación del protocolo.
7. Aplicación de la configuración de cuenta.
8. Reconocimiento.
9. Mapeo del evento.
10. Presentación final en el CMS.

El objetivo es comprobar que el estado operativo final coincide con la intención original del panel.

### La aceptación del receptor no es el final de la prueba

Un receptor puede aceptar un mensaje y el resultado operacional seguir siendo incorrecto.

La prueba debe distinguir:

- Recepción.
- Aceptación.
- Reconocimiento.
- Decodificación.
- Mapeo.
- Presentación en CMS.

Un evento puede llegar al receptor y aparecer asociado a una zona incorrecta, a una cuenta incorrecta o a una condición operativa que no corresponde al evento original.

Por eso la prueba debe finalizar en la representación del evento para el operador.

![Panel de alarma y entorno de control utilizado como referencia documental de integración](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel-1.jpg)

### Variables que deben congelarse durante la prueba

La interoperabilidad debe probarse con una configuración específica.

| Variable | Debe quedar identificada |
| --- | --- |
| Panel | Modelo exacto |
| Firmware del panel | Versión utilizada |
| Comunicador | Modelo exacto |
| Firmware del comunicador | Versión utilizada |
| Receptor | Modelo y versión |
| Transporte | Configuración aplicada |
| Seguridad | Configuración aplicada |
| Cuenta | Identificación y parámetros de prueba |
| Protocolo | Versión implementada |
| Mapeo | Matriz utilizada |
| Reconocimiento | Condición esperada |
| CMS | Configuración específica usada por el operador |

La palabra “compatible” no debería aceptarse como sustituto de esta información.

### Casos de prueba para la Interoperabilidad del receptor CMS

El registro de integración debe incluir condiciones normales y de fallo.

Como base de aceptación, deben probarse:

- Alarma.
- Restauración.
- Pérdida de comunicación.
- Recuperación de comunicación.
- Fallo de alimentación de CA.
- Fallo de batería.
- Fallo de la ruta primaria.
- Conmutación a la ruta secundaria.
- Reinicio del panel.
- Reinicio o pérdida del receptor cuando el proyecto lo requiera.
- Ausencia de reconocimiento.
- Reintentos.
- Eventos duplicados.
- Mapeo incorrecto o no esperado.
- Estado final visible para el operador.

La prueba debe generar un registro de integración reproducible.

### El receptor y el CMS deben permanecer conceptualmente separados

El receptor procesa o acepta la comunicación recibida.

El CMS interpreta y presenta el evento operativo.

La evaluación debe conservar esta separación porque una prueba satisfactoria en el receptor no demuestra automáticamente una interpretación correcta en el CMS.

Una plataforma solo puede considerarse interoperable para un proyecto determinado cuando la cadena completa ha sido comprobada con el modelo, la versión y la configuración reales.

### Evidencia que el fabricante debería aportar

El expediente de integración debería incluir:

| Evidencia | Objetivo |
| --- | --- |
| Modelo de receptor | Identificar el entorno real de prueba |
| Versión de receptor | Evitar equivalencias genéricas |
| Firmware de panel | Mantener trazabilidad |
| Firmware de comunicador | Mantener trazabilidad |
| Configuración de transporte | Reproducir la prueba |
| Configuración de seguridad | Reproducir el entorno |
| Cuenta de prueba | Asociar los eventos al entorno correcto |
| Matriz de eventos | Verificar mapeo |
| Registros de ACK | Confirmar reconocimiento |
| Registros de fallo | Validar comportamiento ante pérdida |
| Resultado de CMS | Confirmar representación final |

La Interoperabilidad del receptor CMS debe expresarse como una cadena verificable de componentes y estados observables.

## Validación transversal para distribuidores e integradores

Los cinco dominios anteriores deben convertirse en evidencia de compra.

La documentación no debe limitarse a declaraciones de producto. Debe permitir que ingeniería, compras y servicio técnico utilicen la misma base de aceptación.

### Matriz de evaluación técnica

| Área | Pregunta técnica | Evidencia requerida | Validación |
| --- | --- | --- | --- |
| Bus RS-485 | ¿La topología del proyecto coincide con la topología aprobada? | Documentación de instalación | Prueba de campo |
| Bus RS-485 | ¿La carga eléctrica está dentro del supuesto del fabricante? | Datos de corriente y carga | Cálculo y prueba |
| Bus RS-485 | ¿Existe margen de tensión en el dispositivo remoto? | Datos de cable y tensión | Medición bajo carga |
| Alimentación | ¿La Arquitectura de alimentación cubre la demanda normal y de alarma? | Especificación eléctrica | Prueba de carga |
| Batería | ¿La autonomía se basa en el escenario real de carga? | Método de cálculo | Prueba de respaldo |
| Comunicación | ¿Las rutas son realmente independientes? | Arquitectura de dependencias | Fallo de cada ruta |
| Comunicación | ¿Se supervisa la sesión de aplicación? | Configuración de Latido de supervisión | Prueba de supervisión |
| Failover | ¿La conmutación está definida por condición de fallo? | Lógica de estados | Prueba de fallo y recuperación |
| SIA DC-09 | ¿La implementación concreta está identificada? | Versión y configuración | Prueba con receptor |
| Contact ID | ¿La Estructura de codificación Contact ID está correctamente integrada? | Declaración de implementación | Prueba cuando sea requerida |
| CMS | ¿El receptor procesa correctamente el evento? | Registro de integración | Prueba de extremo a extremo |
| CMS | ¿El CMS presenta correctamente el evento? | Matriz de mapeo | Verificación del operador |
| Diagnóstico | ¿El sistema expone un Fallo silencioso? | Registros de diagnóstico | Simulación de pérdida |
| RS-485 | ¿Un módulo fuera de línea puede aislarse por causa? | Procedimiento diagnóstico | Prueba de campo |

### Regla de evidencia

Toda especificación importante debería tener al menos una de estas formas de respaldo:

- Evidencia documental.
- Evidencia de cálculo.
- Evidencia de prueba.
- Supuesto de proyecto claramente definido.

Cuando una especificación no dispone de ninguna de estas formas de respaldo, debe considerarse una afirmación pendiente de validación.

### Diagnóstico de un dispositivo RS-485 fuera de línea

El Diagnóstico de dispositivo fuera de línea del bus debe comenzar por la alimentación y no por la sustitución inmediata del módulo.

El procedimiento puede documentarse así:

1. Medir la tensión disponible en el dispositivo.
2. Confirmar la tensión con la carga real conectada.
3. Revisar el recorrido de cableado.
4. Comparar la instalación con la Topología del bus RS-485 aprobada.
5. Verificar terminación.
6. Comprobar direccionamiento.
7. Revisar puesta a tierra.
8. Revisar apantallamiento.
9. Comprobar Interferencia electromagnética.
10. Sustituir el módulo solamente después de aislar la condición del recorrido.

Este método separa un problema del dispositivo de un problema de instalación.

### Diagnóstico de pérdida de comunicación

Cuando una ruta parece disponible pero el receptor deja de reconocer los mensajes, el diagnóstico debe separar:

1. Estado físico del enlace.
2. Conectividad.
3. Sesión de aplicación.
4. Latido de supervisión.
5. Temporización de fallo.
6. Conmutación.
7. Registro en el receptor.
8. Reconocimiento.
9. Recuperación.

Una conexión física disponible no debe considerarse equivalente a una sesión de reporte funcional.

### Diagnóstico de eventos duplicados

Los eventos duplicados pueden estar relacionados con reintentos, pérdida de reconocimiento, comportamiento durante recuperación o condiciones transitorias entre rutas.

El análisis debe distinguir entre:

- Evento original.
- Reintento.
- Entrega duplicada.
- Restauración.

La lógica del receptor y del CMS debe verificarse para asegurar que una única condición física no se convierta indebidamente en múltiples incidencias operativas.

## Preguntas frecuentes técnicas

### ¿Qué debe documentar un fabricante para demostrar que un Panel de alarma RS-485 es adecuado para proyectos comerciales grandes?

Debe documentar la Topología del bus RS-485, el direccionamiento, la carga máxima, los supuestos de cableado, la distribución de alimentación, la terminación y los métodos de diagnóstico. La presencia de una interfaz RS-485 por sí sola no demuestra que el bus sea adecuado para la instalación prevista.

### ¿Cómo debe definirse la conmutación de una Comunicación de alarma de doble vía?

Debe definirse por condición de fallo y no solo por la existencia de dos interfaces. La especificación debe distinguir pérdida física del enlace, pérdida de sesión, fallo de supervisión, ausencia de reconocimiento, tiempo de conmutación, reintentos y restauración. Cada ruta debe probarse de forma independiente.

### ¿Qué debe comprobarse antes de aceptar una implementación del Protocolo SIA DC-09 de reporte de eventos IP?

Debe comprobarse la versión implementada, el transporte, las clases de eventos, el receptor objetivo, la configuración de seguridad, el comportamiento de reconocimiento y las versiones de firmware del panel y del comunicador. Una afirmación genérica de soporte SIA no sustituye la evidencia de implementación.

### ¿Por qué la Interoperabilidad del receptor CMS debe validarse de extremo a extremo?

Porque un evento puede generarse correctamente en el panel y aun así no llegar, ser rechazado o interpretarse incorrectamente. La validación debe cubrir comunicador, red, receptor, protocolo, cuenta, reconocimiento, mapeo del evento y representación final en el CMS.

## Referencias enlazadas conservadas del material técnico de origen

La documentación y los recursos enlazados en el material de referencia deben mantenerse para preservar la trazabilidad documental:

- [Documentación del Athenalarm AS-9000](https://athenalarm.com/burglar-alarm/intrusion-alarm-panel/alarm-control-panel/)
- [Sistema de monitoreo de alarmas en red](https://files.athenalarm.com/images/Athenalarm-network-alarm-monitoring-system-1-1024.jpg)
- [Panel de alarma comercial](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel.jpg)
- [Vídeo de referencia sobre monitorización de alarmas](https://www.youtube.com/watch?v=cIBxzrVTb4A)
- [Miniatura del vídeo de referencia](https://img.youtube.com/vi/cIBxzrVTb4A/0.jpg)
- [IEC 61000-4-5](https://webstore.iec.ch/en/publication/4223)
- [BS EN 50131-6:2017+A1:2021](https://knowledge.bsigroup.com/products/alarm-systems-intrusion-and-hold-up-systems-power-supplies-3)
- [BS EN 50131-3:2026](https://knowledge.bsigroup.com/products/alarm-systems-intrusion-and-hold-up-systems-control-and-indicating-equipment)
- [SIA DC-09-2026](https://www.securityindustry.org/industry-standards/dc-09-2026/)
- [SIA DC-05-2016](https://www.securityindustry.org/industry-standards/dc-05-2016/)
- [Vídeo adicional de referencia sobre monitorización](https://www.youtube.com/watch?v=FouMQpGDZNk)
- [Miniatura del vídeo adicional](https://img.youtube.com/vi/FouMQpGDZNk/0.jpg)
- [Panel de alarma, referencia visual de integración](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel-1.jpg)
- [Panel de alarma, referencia visual adicional](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel-2.jpg)
- [Panel de alarma, referencia visual adicional](https://files.athenalarm.com/images/Athenalarm-alarm-control-panel-3.jpg)

## Criterio final de calificación técnica

Un fabricante de paneles de alarma comerciales debe evaluarse mediante una cadena de evidencia que comience en la capa física y termine en el evento presentado al operador.

La evaluación del bus debe demostrar la relación entre Topología del bus RS-485, carga, alimentación, Caída de tensión, terminación, direccionamiento e Interferencia electromagnética.

La evaluación energética debe demostrar que la Arquitectura de alimentación mantiene la tensión y la capacidad necesarias bajo la carga definida por el proyecto y durante el escenario de respaldo.

La evaluación de comunicaciones debe demostrar que la Comunicación de alarma de doble vía identifica los fallos de ruta de forma supervisada, ejecuta la conmutación definida y permite verificar la restauración.

La evaluación de protocolo debe demostrar que el Protocolo SIA DC-09 de reporte de eventos IP y la Estructura de codificación Contact ID están implementados en la configuración concreta que se pretende utilizar.

La evaluación del centro de monitoreo debe demostrar la Interoperabilidad del receptor CMS mediante una prueba completa que incluya transmisión, recepción, reconocimiento, decodificación, configuración de cuenta, mapeo y representación final del evento.

La presencia de características aisladas no sustituye esta validación.

Un sistema puede declarar RS-485 y presentar una implementación eléctricamente inadecuada para la carga real.

Puede declarar dos rutas de comunicación y seguir dependiendo de elementos comunes.

Puede declarar soporte SIA y no haber demostrado la combinación concreta de protocolo, transporte, firmware y receptor requerida.

Puede declarar compatibilidad CMS y presentar un mapeo de eventos incorrecto.

Por ello, la evidencia de compra debe responder de forma verificable a estas preguntas:

- ¿Está definida la Topología del bus RS-485 y son conocidos sus límites eléctricos?
- ¿Está documentada la Arquitectura de alimentación para la carga normal y de alarma?
- ¿Se ha calculado la Caída de tensión en los recorridos relevantes?
- ¿Se ha validado el comportamiento del bus cuando un dispositivo queda fuera de línea?
- ¿Está documentada la independencia real de las rutas de la Comunicación de alarma de doble vía?
- ¿Está definido el comportamiento del Latido de supervisión?
- ¿Se han probado fallo, conmutación y restauración?
- ¿Está identificada la implementación concreta del Protocolo SIA DC-09 de reporte de eventos IP?
- ¿Está claramente separada la Estructura de codificación Contact ID de SIA DC-09?
- ¿Se ha probado la Interoperabilidad del receptor CMS con el modelo y la configuración reales?
- ¿Se ha verificado el mapeo final del evento en el CMS?
- ¿Existen registros reproducibles para los principales estados normales y de fallo?

Cuando estas preguntas pueden responderse mediante documentación, cálculos y pruebas reproducibles, el fabricante puede evaluarse como una plataforma técnica con condiciones de despliegue observables.

Cuando las respuestas dependen únicamente de afirmaciones comerciales, la calificación técnica todavía no está completa.
