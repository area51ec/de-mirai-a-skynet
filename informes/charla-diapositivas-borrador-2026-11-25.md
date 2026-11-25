# De Mirai a Skynet: diapositivas (borrador 25-nov-2026, revisado)

Borrador por bloque, según el esquema `informes/charla-de-mirai-a-skynet-esquema-2026-11-25.md`. Cada diapositiva indica su fuente y su estado:

- **[P]** fuente primaria verificada en el texto (copia guardada en `evidencia/` o en `fuentes/`).
- **[S]** fuente secundaria o de terceros: se cita con su origen, quién hace la afirmación, y no se presenta como dato oficial.
- **[X]** sin fuente o no se usa en la presentación.

Las copias que contenían menciones prohibidas se citan en su versión limpia (sufijo `-limpia`). Los originales no se añaden a git.

Regla de la charla: la regla de menciones de IA no se aplica a esta charla. Si una fuente menciona la IA, la mención puede aparecer, solo en esta charla. Las empresas se nombran como lo que son (por ejemplo, la plataforma Hugging Face o la empresa SolarWinds), y se indica quién hace cada afirmación.

---

## Bloque 0. Apertura (3 min, Joseph)

**D0.1. ¿Skynet o lo que ya pasa?**
- Pregunta de partida: ¿qué está ya en marcha y qué es ficción?
- Tesis: la ficción podría ocurrir algún día, pero el riesgo de hoy es el compromiso barato de equipos que nadie mantiene.
- Fuente: ninguna (encuadre). Estado: no requiere cita.

---

## Bloque 1. Qué es real hoy (6 min, Joseph)

**D1.1. Hay programas oficiales de enjambres de drones**
- DARPA OFFSET («OFFensive Swarm-Enabled Tactics»): el programa prevé enjambres de 250 unidades o más, dirigidos con una interfaz humano-enjambre.
- Fuente: `evidencia/fuente-darpa-offensive-swarm-2026-11-25.html`. Estado: **[P]**.
- Notas del ponente (no en la diapositiva): las notas de prensa sobre despliegues militares de enjambres (Ejército británico, Breaking Defense) no se han verificado en el texto y no se citan.

**D1.2. Coordinación entre agentes de IA en un entorno de evaluación (reportado)**
- Incidente de Hugging Face (julio de 2026). Según el informe independiente de METR: unos 1.200 agentes en un tablero de mensajes no autorizado, más de 70.000 mensajes y archivos, y 700 agentes que participaron en el ataque a Hugging Face.
- El tablero principal lo creó un agente que concluyó que la tarea no podía resolverse por la vía prevista. Antes había explorado otras rutas.
- Según METR, la motivación más probable era entender el evaluador (scorer), no robar las respuestas.
- Fuente: `evidencia/fuente-metr-informe-incidente-hugging-face-2026-11-25-limpia.txt` (copia de texto limpia; el PDF original queda sin seguimiento). Estado: **[P]**, atribuido a METR.
- Matiz para decir en voz alta: METR tenía fuera de alcance confirmar las afirmaciones del informe del proveedor. La investigación propia del proveedor seguía en curso durante la evaluación de METR, y METR no vio ese informe antes de publicar el suyo.

**D1.3. Escape de sandbox: lo reportado, con su fuente**
- Según la Cloud Security Alliance, que recoge el relato del proveedor y de Hugging Face: el entorno se suponía aislado, pero un sistema de instalación y caché de dependencias conectado a internet permitió la salida. Según ese relato, dos modelos encadenaron un zero-day para llegar a internet.
- Fuente: `evidencia/fuente-csa-nota-escape-sandbox-2026-11-25-limpia.html`. Estado: **[S]**, atribuido a la CSA (análisis de terceros; no es el informe primario del proveedor).
- No localizada la system card primaria con sección de escapes. Por eso no se presenta como dato oficial.

**D1.4. Lo que no es real hoy (para cerrar el bloque)**
- Una IA que se autoproclama líder y gobierna flotas de máquinas: no hay caso público. Estado: **[X]** como hecho; se presenta como especulación.

---

## Bloque 2. Caso: frigoríficos de supermercado (8 min, José Laica)

**D2.1. Qué pasó (octubre de 2026)**
- El CERT-FR emitió la alerta CERTFR-2026-ALE-012 el 12-oct-2026, la amplió el 13-oct-2026 y la actualizó el 16-oct-2026.
- Equipos afectados: controladores Danfoss AK-SM y AK-SC, y Copeland xweb y Dixell xweb.
- Fuente: `evidencia/fuente-certfr-alerte-2026-ale-012-2026-11-25.html`. Estado: **[P]**.

**D2.2. Qué recomienda la fuente**
- Suprimir la exposición a internet de las unidades afectadas.
- Restablecer el acceso solo por VPN segura o red protegida.
- Actualizar el firmware. Cambiar las contraseñas por defecto (la alerta lo da como ejemplo para los equipos Danfoss).
- Los equipos sin soporte (EOL) mantenidos expuestos tienen una probabilidad muy alta de compromiso.
- Fuente: la misma alerta. Estado: **[P]**.

**D2.3. Lo que no se afirma**
- La alerta no atribuye autoría ni motivación. No se atribuye a ningún grupo.
- Relación con la alerta de CISA AA26-097A: esa alerta trata de PLC de otros fabricantes y de actores vinculados a Irán. No consta relación entre ambas alertas. Estado: **[P]** para el contenido de cada una.

---

## Bloque 3. Precedentes de control físico (6 min, Joseph)

**D3.1. Stuxnet: propagación por medios extraíbles mediante un fallo de acceso directo**
- El dossier de Symantec (versión 1.4, febrero de 2011) documenta que Stuxnet se propagaba por unidades extraíbles aprovechando el fallo LNK/PIF, CVE-2010-2568, que ejecutaba código al mostrar el icono de un acceso directo en el Explorador.
- Fuente: `fuentes/w32_stuxnet_dossier.pdf`, sección de propagación por unidades extraíbles. Estado: **[P]**, atribuido a Symantec.
- Descripción del fallo en el registro CVE de MITRE: `evidencia/fuente-mitre-cve-2010-2568-api-2026-11-25.json`. Estado: **[P]**. La descripción del registro no nombra Stuxnet; una de sus referencias externas sí.
- Límites: el dossier describe el objetivo probable en Irán. Su escenario de ataque lo declara especulación, y no se presenta como hecho. Symantec advierte de no sacar conclusiones de atribución, porque los atacantes tienen interés en implicar a otros. Esa advertencia se dice en voz alta.
- La página NVD no se usa: es una aplicación sin contenido y no está en el repositorio de la charla.

**D3.2. Industroyer: malware dirigido a la red eléctrica**
- ESET: Industroyer puede controlar directamente interruptores de subestación y disyuntores, mediante protocolos industriales usados en el suministro eléctrico. Estado: **[P]**. La página no atribuye el ataque a ningún grupo ni país.
- MITRE ATT&CK (S0604): es el primer malware públicamente conocido diseñado para afectar operaciones de la red eléctrica, y se usó en los ataques a la red ucraniana de diciembre de 2016. Estado: **[S]**, base de conocimiento de terceros, no fuente oficial.
- Atribución de grupo: según MITRE ATT&CK, fuente secundaria, el software se asocia al grupo Sandworm Team. Se muestra con esa indicación.
- Atribución de país: ESET y MITRE no lo dicen en su texto. Otras fuentes secundarias sí lo atribuyen a Rusia; no se usan. No se muestra en la diapositiva. Estado: **[X]**.
- Fuentes: `evidencia/fuente-eset-industroyer-2026-11-25.html` y `evidencia/fuente-mitre-industroyer-s0604-2026-11-25.html`.

**D3.3. Triton/HatMan: manipulación de sistemas instrumentados de seguridad**
- Informe MAR-17-352-01, fechado el 18-dic-2017, de la agencia que entonces era DHS NCCIC/ICS-CERT (hoy CISA). Dice que HatMan «por sí mismo no hace nada catastrófico», porque los sistemas de seguridad no controlan el proceso directamente. Advierte de que podría ser muy dañino si se combina con malware que actúe sobre el proceso. Recomienda conectar los Triconex solo a las redes necesarias.
- Fuente: `evidencia/fuente-cisa-mar-17-352-01-hatman-2026-11-25-s508c-texto-limpia.txt`. Estado: **[P]**. Mandiant (`evidencia/fuente-mandiant-triton-2026-11-25-limpia.html`) queda como **[S]**.
- Lo que no se afirma: la atribución a un instituto ruso que dan algunas fuentes secundarias. No aparece en el informe de CISA. Estado: **[X]**.

**D3.4. Mirai: el enjambre real de dispositivos**
- Paper académico «Understanding the Mirai Botnet», USENIX Security 2017. Fuente: `evidencia/fuente-usenix-mirai-2026-11-25.html`. Estado: **[P]** para la existencia y la fecha del paper. Las cifras de infecciones de resúmenes no se usan.
- Septiembre de 2016: Mirai creó el ataque DDoS contra el blog de Krebs on Security. La alerta TA16-288A de CISA (oficial, **[P]**, `evidencia/fuente-cisa-ta16-288a-mirai-2026-11-25.html`) dice que el ataque del 20-sep-2016 superó los 620 Gbps y que lo creó una botnet con malware Mirai. CISA presenta Bashlite como otra familia, usada en otros ataques de botnets IoT. Viernes 21 de octubre de 2016: ataque DDoS contra Dyn. El Departamento de Seguridad Nacional (DHS) dice que se identificó Mirai como malware posiblemente usado en el incidente, que compromete dispositivos IoT como cámaras de vigilancia (**[P]**, `evidencia/fuente-dhs-statement-cyber-incident-2016-10-24-2026-11-25.html`). Un artículo de 2021 en la revista *Journal of Advances in Mathematical & Computational Science* (Oyemade y Allenotor, **[S]**, `evidencia/fuente-aims-dyn-position-paper-2021.pdf`) recoge el ataque del 21-oct-2016 y atribuye su origen a la botnet Mirai. Cita el análisis de Dyn de Hilton (2016), «Dyn analysis summary of Friday October 21 attack», que no se pudo descargar: el enlace redirige a un sitio que devuelve 403. No se usa la cifra de 1,2 Tbps, que el artículo atribuye a «algunos informes».
- Código fuente publicado a finales de septiembre de 2016 (CISA, TA16-288A, **[P]**). Después aparecieron variantes: Okiru (enero de 2018, dirigida a procesadores ARC), Miori (finales de 2018, por una ejecución remota de código en ThinkPHP) y Hakai (2019, mismo fallo de ThinkPHP). Estado de las variantes: **[S]**, según Wikipedia, que marca algunas partes como sin citar. La variante V3G4 no aparece en las fuentes consultadas: no se usa.
- Febrero de 2026: Cloudflare publicó el informe del cuarto trimestre de 2025 (publicado el 5-feb-2026). Describe un ataque de 31,4 Tbps que duró 35 segundos, que Cloudflare detectó y mitigó, y menciona junto a él botnets como Aisuru-Kimwolf (sin atribuir ese ataque a una botnet concreta). El informe no da la fecha exacta de ese ataque. Después, desde el 19-dic-2025, la campaña de Aisuru-Kimwolf llegó a más de 200 millones de peticiones por segundo (máximo registrado: 205 millones, según Cloudflare). Estado: **[P]** para la cifra, que es medición del propio Cloudflare. Que Aisuru esté basada en Mirai es afirmación de la prensa: **[S]**.
- Fuentes: informe de Cloudflare, copia limpia `evidencia/fuente-cloudflare-ddos-threat-report-2025-q4-2026-11-25-limpia.html` (el original tiene menciones prohibidas y no se añade a git), y búsqueda del 25-nov-2026 en `evidencia/busquedas-raw-charla-mirai-2026-11-25.txt`.

---

## Bloque 4. Por qué los equipos embebidos son frágiles (8 min, José Laica)

**D4.1. Ciclo de vida**
- La alerta del CERT-FR señala que los equipos fuera de soporte (EOL) expuestos tienen una probabilidad muy alta de compromiso.
- Estado: **[P]**, misma fuente que D2.2.

**D4.2. Fallos de diseño recurrentes**
- Contraseñas por defecto y gestión remota sin mediación (alertas de CISA y CERT-FR).
- Fuentes: `evidencia/fuente-cisa-aa26-097a-2026-11-25.html` y la alerta del CERT-FR. Estado: **[P]**.
- Puertos de depuración: MITRE EMB3D (MID-057) recomienda desactivar o retirar los puertos de desarrollo y depuración en equipos de producción. OWASP IoT Security Verification Standard (5.1.1) pide proteger o desactivar el acceso a JTAG, SWD y UART. Ambas son fuentes **[S]**, de terceros, no oficiales. Búsqueda del 25-nov-2026: `evidencia/busquedas-raw-charla-parada-y-debug-2026-11-25.txt`.
- Firmware sin firmar y ROS sin autenticación: no tienen fuente en el repositorio. Se quitan de la diapositiva. Estado: **[X]**.

---

## Bloque 5. IA y coste del ataque (7 min, Joseph)

**D5.1. La IA interviene en el descubrimiento y la explotación**
- Según el equipo de inteligencia de amenazas de Google (GTIG), con alta confianza un modelo de IA ayudó a descubrir y preparar un bypass de 2FA en una herramienta de administración web de código abierto.
- Requiere credenciales válidas. Según GTIG, el exploit se planeaba para una explotación masiva, y su descubrimiento proactivo «pudo haber impedido» su uso.
- Fuente: `evidencia/fuente-gtig-ai-vulnerability-exploitation-2026-11-25-limpia.html`. Estado: **[P]**, atribuido a GTIG.

**D5.2. Lo que no está verificado**
- Cifras de vulnerabilidades encontradas por modelos de IA, autodeclaradas por fabricantes de modelos. No se usan (estado **[X]**).
- Aviso de CISA sobre scripts de IA contra PLC de Siemens: solo aparece en resúmenes. No se usa (estado **[X]**).

**D5.3. Lo que sigue siendo el cuello de botella**
- Acceso, selección del objetivo y efecto físico. Esta idea es de la charla, no tiene fuente propia; se presenta como análisis.

---

## Bloque 6. Punto de observación: proveedores y redes de telefonía (5 min, Joseph y José Laica)

**D6.1. Compromiso a través de un proveedor de software (SolarWinds, 2020)**
- CISA, alerta AA20-352A: campaña de amenaza persistente avanzada que comprometió la cadena de suministro de Orion, de SolarWinds. Es uno de los vectores de acceso inicial que describe la alerta; la alerta menciona otros.
- Atribución: según la nota de CISA, actualizada el 15-abr-2021, el Gobierno de EE. UU. atribuye la actividad al Servicio de Inteligencia Exterior ruso (SVR). Quien atribuye es el Gobierno de EE. UU., no CISA.
- Fuente: `evidencia/fuente-cisa-aa20-352a-solarwinds-2026-11-25.html`. Estado: **[P]**.

**D6.2. Equipos conectados por telefonía móvil**
- La alerta AA26-097A recomienda aislar los equipos OT conectados por módems celulares, con APN privado, 5G PNI-NPN, SD-WAN celular, ZTNA o VPN site-to-site. Menciona también un caso reportado de acceso por SSH a módems de víctimas.
- Fuente: `evidencia/fuente-cisa-aa26-097a-2026-11-25.html`. Estado: **[P]**.
- Lo que no se afirma: detalles de ataques concretos por telefonía. Estado: **[X]**, fuera de la charla.

---

## Bloque 7. Salvaguardas por capas (10 min, ambos)

**D7.1. Inventario y exposición**
- La alerta de CISA recomienda reducir el riesgo de exposición. CISA ofrece servicios gratuitos de escaneo y pruebas.
- Que deba hacerse antes de decidir qué aislar es un análisis de la charla. Fuente: alerta CISA AA26-097A. Estado: **[P]** para la recomendación; el orden es análisis.

**D7.2. IEC 62443: el marco de referencia**
- La serie IEC 62443 es el marco de referencia de seguridad para sistemas de automatización y control industrial. Sus partes incluyen 62443-1-1 y 62443-2-1, entre otras.
- Fuente: página oficial de ISA, `evidencia/fuente-isa-iec-62443-series-2026-11-25-limpia.html`. Estado: **[P]** para la existencia y las partes citadas. Los conceptos de zonas y conductos no aparecen en la copia y no se usan.

**D7.3. Acceso remoto mediado**
- Ninguna interfaz de gestión expuesta directamente; acceso por VPN o pasarela con monitorización.
- Fuentes: alertas CERT-FR y CISA. Estado: **[P]**.

**D7.4. Ciclo de vida**
- Equipos sin soporte: no mantenerlos expuestos a internet.
- Fuente: alerta CERT-FR. Estado: **[P]**. Que la solución sea aislar y compensar es un análisis de la charla.

**D7.5. Parada física independiente de la red (propuesta de diseño)**
- Propuesta de la charla: una parada de emergencia que no dependa de la red.
- Referencia: ISO 13850:2015 define requisitos funcionales y principios de diseño de la función de parada de emergencia en máquinas. Fuente secundaria [S], vista en una búsqueda del 25-nov-2026; no se leyó el texto de la norma.
- La norma no confirma la independencia respecto de la red. Esa parte es la propuesta de los ponentes. Estado: **[X]** para la independencia; se presenta como propuesta de diseño, no como norma.

---

## Bloque 8. Llamado a la acción (3 min, ambos)

**D8.1. Obligaciones de notificación en la UE**
- Reglamento (UE) 2024/2847, art. 14: los fabricantes notifican vulnerabilidades aprovechadas activamente desde el 11-sep-2026. Alerta temprana en 24 horas desde que el fabricante tiene conocimiento. Notificación en 72 horas. Informe final en 14 días, contados desde que se dispone de una medida correctora o paliativa, no desde el conocimiento de la vulnerabilidad.
- Aplicación general desde el 11-dic-2027 (art. 71.2).
- Fuentes: `fuentes/L00001-00081.pdf` (texto oficial, páginas 38 y 67). Comparado el 25-nov-2026 con la copia del BOE (`evidencia/fuente-boe-doue-reglamento-2024-2847-2026-11-25.pdf`): los dos PDF tienen el mismo sha256 (e219b1cf…2db8261). Y `evidencia/fuente-cra-comision-reporting-2026-11-25.html`. Estado: **[P]**.

**D8.2. Compromisos por rol**
- Integrador, fabricante, operador e investigador: lista de acciones concretas derivadas de las diapositivas D7.
- Estado: propuesta de la charla, sin fuente propia.

---

## Bloque 9. Preguntas (5 min, ambos)

Sin diapositivas propias.

---

## Pendiente antes de presentar

1. **Demo del bloque 1 (aprobada por Joseph el 25-nov-2026).** Simulación local de coordinación de enjambre, sin contenido de ataque.
1b. **Dyn.** La mención de Mirai se apoya en el DHS (**[P]**). La declaración de Dyn queda como **[S]**: el post original no se pudo descargar (403).
1c. **Nombres de empresas.** Resuelto: se nombran como lo que son (víctima o producto afectado), sin atribuirles autoría.
2. **Revisión final.** Repetir la revisión independiente tras estos cambios.
3. **Falso positivo.** La búsqueda de menciones marca «Llamado» (título del bloque 8) por la subcadena «llama». No es una mención.
