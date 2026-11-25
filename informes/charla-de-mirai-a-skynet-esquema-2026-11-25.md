# De Mirai a Skynet: lo que ya es real, lo que no, y qué hacer antes de que sea tarde

Esquema de charla técnica (borrador, 25-nov-2026). Ponentes: Joseph Páez (software y seguridad) y José Laica (electrónica y robótica).

## Carácter de la charla

- Es una tesis de investigación, no una divulgación de hallazgos. Las investigaciones propias solo aparecen, si aportan algo, como idea de tesis, sin detalles que permitan reproducirlas. Nunca se dice que se están haciendo, que se han hecho o que se han resuelto.
- Solo se citan casos con fuente pública: avisos GHSA o CVE, avisos de CISA o del fabricante, informes de fabricantes de seguridad y de organismos oficiales, y casos de explotación reportados públicamente. No se usan hallazgos propios sin publicar.
- Cada atribución indica quién la hace. Si no procede de una fuente oficial, se indica como fuente secundaria.
- Nada de cadenas de ataque ejecutables. Se explica dónde se corta cada cadena (principios de defensa).
- Nada sobre la arquitectura de mando de sistemas militares o nucleares. Solo se menciona como punto de observación, con el principio de que la seguridad total no existe.

## Tesis

La ficción de Skynet podría llegar a ser realidad en algún momento, pero no es el riesgo principal hoy. Lo que ya ocurre es el compromiso masivo y barato de equipos embebidos que nadie mantiene, y la cadena de confianza de proveedores. Las salvaguardas deben llegar antes de que crezca la capacidad de atacar.

## Estructura (suma de bloques: 61 min)

Según Joseph, el tiempo no es una restricción; la suma se deja tal cual.

| Bloque | Tiempo | Responsable | Contenido |
|---|---|---|---|
| 0. Apertura | 3 min | Joseph | La pregunta de Skynet y la tesis. |
| 1. Qué es real hoy | 6 min | Joseph | Con demo (decidido y aprobado por Joseph el 25-nov-2026): simulación local de coordinación de enjambre, sin contenido de ataque. Programas oficiales de enjambres de drones (DARPA OFFSET); coordinación entre agentes de IA en una evaluación, según el informe independiente de METR; escape de sandbox según un análisis de terceros; y lo que no es real hoy (una IA que gobierna flotas, como especulación). |
| 2. Caso: frigoríficos de supermercado (oct. 2026) | 8 min | José Laica | Controladores accesibles desde internet, gestión remota, contraseñas por defecto y equipos sin soporte. Recomendaciones del CERT-FR: suprimir la exposición, acceso solo por VPN, actualizar firmware. |
| 3. Precedentes de control físico | 6 min | Joseph | Stuxnet: propagación por medios extraíbles mediante el fallo LNK/PIF (CVE-2010-2568), documentada en el dossier de Symantec. Industroyer: funciones según ESET; asociación con un grupo según MITRE (fuente secundaria). Triton/HatMan según CISA. Mirai como precedente de dispositivos en botnet: ataque a Krebs (CISA), ataque a Dyn (Wikipedia), variantes tras la publicación del código y el informe de Cloudflare de 2026 (31,4 Tbps). |
| 4. Por qué los equipos embebidos son frágiles | 8 min | José Laica | Ciclos de vida largos y equipos sin soporte, contraseñas por defecto, gestión remota sin mediación y puertos de depuración (MITRE EMB3D, fuente secundaria). |
| 5. IA y coste del ataque | 7 min | Joseph | Caso de IA en el descubrimiento de un bypass de 2FA, según el equipo de inteligencia de amenazas de Google. Cifras autodeclaradas, no usadas. El cuello de botella sigue siendo el acceso, la selección del objetivo y el efecto físico. |
| 6. Punto de observación: proveedores y redes de telefonía | 5 min | Joseph y José Laica | Compromiso de la cadena de suministro (SolarWinds, CISA AA20-352A). Atribución: la hace el Gobierno de EE. UU., según CISA. Equipos conectados por módems celulares, sin detalle técnico. |
| 7. Salvaguardas por capas | 10 min | Ambos | Exposición y servicios de escaneo (CISA AA26-097A), marco IEC 62443 (ISA), acceso remoto mediado, ciclo de vida y parada de emergencia física independiente de la red (propuesta de diseño, con ISO 13850 como referencia secundaria). |
| 8. Llamado a la acción | 3 min | Ambos | Obligaciones de notificación del Reglamento (UE) 2024/2847, art. 14, y compromisos concretos por rol. |
| 9. Preguntas | 5 min | Ambos | |

## Principios sobre la conectividad

- Aislamiento total no basta. Stuxnet se propagaba también por medios extraíbles, según el dossier de Symantec.
- Lo práctico es denegar por defecto y dejar solo las conexiones necesarias, con pasarelas de control estricto.
- Si un equipo no se puede parchear, se aísla y se compensa. (Análisis de la charla.)
- Hay que medir la exposición real antes de decidir qué aislar. (Análisis de la charla.)

## Fuentes (estado)

Leyenda: [P] primaria verificada en el texto; [S] secundaria o de terceros, con su origen indicado; [X] sin fuente o no se usa.

| Fuente | Bloques | Estado |
|---|---|---|
| CISA y partners, aviso AA26-097A (publicado el 7-abr-2026, actualizado el 22-jul-2026) sobre PLC expuestos a internet. Copia: `evidencia/fuente-cisa-aa26-097a-2026-11-25.html` | 2, 4, 6, 7 | [P]. Retirar los PLC de la exposición directa a internet mediante pasarela segura y cortafuegos; cambiar contraseñas por defecto; atacantes asociados a un actor afiliado a Irán. |
| CERT-FR, alerta CERTFR-2026-ALE-012 (12-oct-2026; ampliada el 13-oct; actualizada el 16-oct) sobre controladores Danfoss AK-SM y AK-SC, y Copeland xweb y Dixell xweb. Copia: `evidencia/fuente-certfr-alerte-2026-ale-012-2026-11-25.html` | 2, 4, 7 | [P]. Suprimir la exposición a internet, acceso solo por VPN o red protegida, actualizar firmware y cambiar contraseñas por defecto (ejemplo para Danfoss). Los equipos fuera de soporte expuestos tienen probabilidad muy alta de compromiso. No atribuye autoría. |
| Google GTIG, «Adversaries Leverage AI for Vulnerability Exploitation, Augmented Operations, and Initial Access» (11-may-2026). Copia limpia: `evidencia/fuente-gtig-ai-vulnerability-exploitation-2026-11-25-limpia.html` | 5 | [P]. Caso de bypass de 2FA en una herramienta de administración web de código abierto. Requiere credenciales válidas. Alta confianza de que se usó un modelo de IA. |
| Reglamento (UE) 2024/2847, DO L de 20.11.2024. Texto: `fuentes/L00001-00081.pdf`. Copia del BOE: `evidencia/fuente-boe-doue-reglamento-2024-2847-2026-11-25.pdf` | 8 | [P]. Comparado el 25-nov-2026: el PDF del BOE es idéntico al de `fuentes/` (sha256 e219b1cf…2db8261). Art. 71.2: aplicación general el 11-dic-2027; art. 14 desde el 11-sep-2026. Art. 14.2: alerta temprana en 24 horas, notificación en 72 horas e informe final en 14 días desde que hay medida correctora o paliativa. Página de la Comisión: `evidencia/fuente-cra-comision-reporting-2026-11-25.html`. |
| CISA, alerta AA20-352A (SolarWinds, Orion). Copia: `evidencia/fuente-cisa-aa20-352a-solarwinds-2026-11-25.html` | 6 | [P]. Campaña que comprometió la cadena de suministro de Orion; es un vector de la alerta, que menciona otros. La atribución al SVR ruso viene de la nota de CISA (actualizada el 15-abr-2021) y es del Gobierno de EE. UU., no de CISA. |
| ISA, página oficial de la serie IEC 62443. Copia limpia: `evidencia/fuente-isa-iec-62443-series-2026-11-25-limpia.html` | 7 | [P] para la existencia de la serie y sus partes (62443-1-1, 62443-2-1). Zonas y conductos no aparecen en la copia; no se usan. |
| Dossier de Symantec, «W32.Stuxnet Dossier», v1.4 (febrero de 2011). `fuentes/w32_stuxnet_dossier.pdf` (sha256 9149e107…63ecd7) | 3 | [P]. Stuxnet se propagaba por unidades extraíbles mediante el fallo LNK/PIF (CVE-2010-2568) y tenía como objetivo probable instalaciones en Irán. El escenario de ataque es especulación declarada de Symantec: no se usa como hecho. Symantec advierte de no sacar conclusiones de atribución. |
| CISA, alerta TA16-288A (Mirai y ataque a Krebs, 20-sep-2016). `evidencia/fuente-cisa-ta16-288a-mirai-2026-11-25.html` | 3 | [P]. Ataque a Krebs de más de 620 Gbps, creado por una botnet con malware Mirai. No menciona a Dyn. |
| Cloudflare, informe DDoS del cuarto trimestre de 2025 (publicado el 5-feb-2026). Copia limpia: `evidencia/fuente-cloudflare-ddos-threat-report-2025-q4-2026-11-25-limpia.html` | 3 | [P]. Ataque de 31,4 Tbps de 35 segundos, que Cloudflare menciona junto a botnets como Aisuru-Kimwolf, sin atribuirlo a una botnet concreta. Campaña de Aisuru-Kimwolf desde el 19-dic-2025, con más de 200 millones de peticiones por segundo (máximo, 205 millones). Que la botnet esté basada en Mirai es de la prensa: [S]. |
| DHS, comunicado del 24-oct-2016 sobre el ataque a Dyn. `evidencia/fuente-dhs-statement-cyber-incident-2016-10-24-2026-11-25.html` | 3 | [P]. Ataque DDoS contra Dyn el 21-oct-2016; Mirai, «potentially used». |
| Oyemade y Allenotor (2021), «Dyn DDoS Cyberattack: A Position Paper», Journal of Advances in Mathematical & Computational Science. `evidencia/fuente-aims-dyn-position-paper-2021.pdf` | 3 | [S]. Ataque del 21-oct-2016 a Dyn, con origen en la botnet Mirai. Cita el análisis de Dyn de Hilton (2016), que no se pudo descargar (403). |
| CVE-2010-2568, registro de MITRE. `evidencia/fuente-mitre-cve-2010-2568-api-2026-11-25.json` | 3 | [P] para la descripción del fallo LNK/PIF. El registro no nombra Stuxnet. |
| ESET, análisis de Industroyer. `evidencia/fuente-eset-industroyer-2026-11-25.html` | 3 | [P] para las funciones (control de interruptores y disyuntores mediante protocolos industriales). La página no atribuye el ataque a ningún grupo ni país. |
| MITRE ATT&CK, S0604 (Industroyer). `evidencia/fuente-mitre-industroyer-s0604-2026-11-25.html` | 3 | [S], base de conocimiento de terceros, no oficial. Primer malware públicamente conocido diseñado para afectar la red eléctrica; usado en Ucrania en diciembre de 2016; asocia el software al grupo Sandworm Team (G0034). La página no menciona a Rusia ni a ningún Estado. |
| CISA, informe MAR-17-352-01 (HatMan, 18-dic-2017). `evidencia/fuente-cisa-mar-17-352-01-hatman-2026-11-25-s508c-texto-limpia.txt` | 3 | [P]. Advierte que HatMan no causa daño catastrófico por sí mismo, pero sí si se combina con malware que actúe sobre el proceso. Mandiant: `evidencia/fuente-mandiant-triton-2026-11-25-limpia.html`, [S]. |
| Paper USENIX Security 2017, «Understanding the Mirai Botnet». `evidencia/fuente-usenix-mirai-2026-11-25.html` | 3 | [P] para la existencia y la fecha. Las cifras de resúmenes no se usan. |
| DARPA OFFSET. `evidencia/fuente-darpa-offensive-swarm-2026-11-25.html` | 1 | [P]. |
| METR, informe independiente sobre el incidente de Hugging Face. `evidencia/fuente-metr-informe-incidente-hugging-face-2026-11-25-limpia.txt` | 1 | [P], con el matiz de que METR no pudo confirmar el informe del proveedor. |
| Cloud Security Alliance, nota sobre el escape de sandbox. `evidencia/fuente-csa-nota-escape-sandbox-2026-11-25-limpia.html` | 1 | [S], análisis de terceros. |
| ISO 13850:2015, función de parada de emergencia en máquinas. Búsqueda web del 25-nov-2026 (`evidencia/busquedas-raw-charla-parada-y-debug-2026-11-25.txt`). No se leyó el texto de la norma. | 7 | [S]. Confirma que existen requisitos funcionales de la parada. No confirma la independencia respecto de la red: esa parte es propuesta de diseño. |
| MITRE EMB3D, MID-057 (puertos de desarrollo y depuración). Misma búsqueda. | 4 | [S]. Recomienda desactivar o retirar esos puertos en equipos de producción. |
| OWASP IoT Security Verification Standard, 5.1.1. Misma búsqueda. | 4 | [S]. Pide proteger o desactivar el acceso a JTAG, SWD y UART. |
| Cifras de descubrimiento asistido por IA (autodeclaradas por fabricantes) | 5 | [X]. No se usan. |
| Aviso de CISA sobre scripts de IA contra PLC de Siemens | 5 | [X]. Solo aparece en resúmenes. No se usa. |

**Notas.** Las copias de GTIG, METR, CSA, ISA y HatMan/Mandiant tienen versión limpia; los originales con menciones prohibidas por la regla de Joseph no se citan ni se añaden a git. Los tres intentos de descargar el Reglamento desde EUR-Lex devolvieron archivos vacíos (0 bytes) y no se usan.

## Imágenes para diapositivas

- Diagramas propios, en SVG, sobre las cadenas de decisión de cada bloque. No se reutilizan imágenes de terceros.
- Cada diagrama cita su fuente en el pie.

## Decisiones pendientes

1. Formato: con demo en el bloque 1, simulación local sin contenido de ataque (aprobado por Joseph el 25-nov-2026).
1b. Mirai: Krebs tiene fuente primaria (CISA TA16-288A). Dyn: el DHS (oficial) menciona Mirai como malware posiblemente usado; la declaración de Dyn queda como [S] porque su post no se pudo descargar.
1c. Nombres de empresas: resuelto. Se nombran como lo que son, sin atribuirles autoría.
1d. Regla de IA: no se aplica a esta charla. Si una fuente menciona la IA, puede aparecer, solo en esta charla.
2. Consultas a sitios oficiales: autorizadas y hechas para el BOE y el dossier de Symantec. Las búsquedas web de este esquema (ISO 13850, MITRE EMB3D, OWASP) son secundarias. Falta confirmar si se quiere más verificación directa de CISA o de la ISA.
3. Mandiant y MITRE: decidir si se citan solo como [S] (estado actual) o se busca su fuente primaria.
