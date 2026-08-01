# Ruédalo — Infraestructura de confianza para el alquiler de autos entre particulares en Venezuela

**Documento de concepto — Aplicación a aceleradora**
Ronda solicitada: US$150.000
Versión 1.1 · Julio 2026

---

## 1. Resumen ejecutivo

En Venezuela existe una flota privada significativa subutilizada y una demanda real de alquiler de vehículos que hoy se resuelve por canales informales: grupos de WhatsApp, Instagram y acuerdos de palabra. Ese mercado informal no crece porque le falta lo único que importa en un alquiler: **garantía de que el carro vuelve**.

Ruédalo es un marketplace P2P de alquiler de vehículos que no compite por precio ni por catálogo, sino por **control del activo**. Cada vehículo de la plataforma lleva telemetría con capacidad de inmovilización remota, respaldada por un motor de decisión que ejecuta el bloqueo únicamente en condiciones seguras y contractualmente justificadas.

No somos una app de alquiler con GPS. Somos una **capa de gestión de riesgo** que hace económicamente viable que un particular entregue su carro a un desconocido.

**Modelo:** marketplace asset-light. No somos dueños de la flota.
**Ingreso principal:** comisión de intermediación de 22–25% sobre el valor de la reserva.
**Diferenciador defendible:** motor de inmovilización segura + dataset propietario de telemetría vehicular venezolana.

---

## 2. El problema

El alquiler informal existe, pero está topado por tres fricciones que ninguna de las partes puede resolver sola:

**Para el dueño del vehículo.** Su carro es, en muchos casos, su activo más valioso y difícilmente reemplazable dado el costo de reposición en el mercado local. Entregarlo implica una exposición binaria: o vuelve, o pierde el activo. No existe un mecanismo de recuperación ni un respaldo económico creíble ante daño o no devolución.

**Para el arrendatario.** No hay oferta estructurada ni precios comparables. La transacción depende de confianza personal, lo que restringe el mercado a círculos cerrados y deja fuera al usuario que llega de afuera o no tiene red local.

**Para el ecosistema asegurador.** El mercado venezolano no ofrece hoy un producto de cobertura amplia diseñado para uso P2P de vehículos. La póliza estándar cubre responsabilidad civil, no el escenario de un tercero conduciendo el vehículo bajo contrato de arrendamiento. Sin respaldo económico, la oferta no escala.

El resultado es un mercado que se queda en transacciones aisladas entre conocidos, cuando el activo instalado permitiría un volumen mucho mayor.

---

## 3. Mercado y competencia

### 3.1 Dimensionamiento

No existen cifras oficiales confiables del mercado de alquiler vehicular venezolano. La estimación es bottom-up y se declara como tal — cada supuesto es verificable en el piloto:

| Nivel | Definición | Estimación | Supuestos clave |
|---|---|---|---|
| TAM | Alquiler vehicular en Venezuela (formal + informal) | US$60–100M/año | Parque privado ~4M de vehículos; fracción en condición de alquiler en ciudades principales; tarifa media $35–45/día |
| SAM | Alquiler P2P estructurable en 4 ciudades principales | US$15–25M/año | Caracas, Valencia, Maracaibo, Margarita; dueños dispuestos a listar con telemetría; demanda con capacidad de pago en USD |
| SOM (24 meses) | Objetivo alcanzable con 300+ vehículos | US$1,4–2M GBV/año | 300 vehículos × ~$400 GBV/mes; una ciudad y media |

Lo relevante para una aceleradora no es el tamaño absoluto del mercado local sino dos cosas: (a) la demanda ya existe y se transacciona hoy por canales informales — no hay que crearla, hay que capturarla con menos fricción; y (b) el activo que se construye (motor de inmovilización + dataset de riesgo) es exportable a cualquier mercado de LatAm con seguros débiles e informalidad alta.

### 3.2 Motores de demanda

1. **Diáspora que regresa de visita.** Millones de venezolanos en el exterior visitan el país cada año. Llegan con dólares, sin carro, sin red local de confianza para alquilar, y planifican con antelación — el perfil de cliente ideal: paga en USD desde el exterior, reserva anticipada, estadía de 1–3 semanas.
2. **Viajero corporativo y técnico.** Empresas que movilizan personal entre ciudades sin flota propia.
3. **Demanda local eventual.** Vehículo en taller, viajes intercity, ocasiones puntuales.

### 3.3 Panorama competitivo

| Competidor | Qué ofrece | Por qué no resuelve el problema |
|---|---|---|
| **Canal informal** (WhatsApp, Instagram) | Precio bajo, cero fricción de entrada | Sin garantía, sin recuperación, sin respaldo económico. Es el competidor real y a la vez el techo que valida la demanda |
| **Rent-a-car tradicional** | Flota propia, atención presencial | Flota pequeña y costosa (capital propio inmovilizado), tarifas altas, exige garantías que excluyen a la mayoría; no escala sin CAPEX |
| **Plataformas P2P internacionales** (Turo, Getaround) | Modelo probado | No operan en Venezuela y estructuralmente no pueden entrar: sin seguros locales que soporten su modelo, sin rieles de pago compatibles, sin apetito por el riesgo país. Barrera natural de entrada |
| **Empresas locales de GPS/rastreo** | Hardware y monitoreo | Tienen el dispositivo pero no el marketplace, ni el contrato, ni el fondo, ni la capa de decisión. Son proveedores potenciales, no competidores |

La posición de Ruédalo: única oferta que combina marketplace + control del activo + respaldo económico. El foso no es la app — es el dataset de riesgo acumulado y la red de dueños con hardware instalado, ambos costosos de replicar y sin valor para un entrante sin operación en el terreno.

---

## 4. La solución

Tres capas de producto que operan sobre la misma transacción:

### 4.1 Marketplace y verificación

Catálogo, disponibilidad, reserva y pago. La verificación del conductor es requisito de entrada, no un extra: identidad validada, licencia vigente, y un historial de comportamiento dentro de la plataforma que se acumula viaje a viaje.

### 4.2 Telemetría e inmovilización

Cada vehículo incorpora un dispositivo con posición en tiempo real, geocerca configurable y corte de arranque. El dueño ve su carro en todo momento. La plataforma tiene la capacidad de impedir el encendido cuando existe causa contractual.

**Restricción técnica no negociable:** el sistema impide el arranque. Nunca apaga un vehículo en movimiento. La validación de velocidad cero sostenida es una condición determinista previa a cualquier ejecución.

### 4.3 Escalera de recuperación graduada

El bloqueo no es el primer recurso, es el último:

| Nivel | Acción | Momento |
|---|---|---|
| 1 | Notificación de vencimiento | Al cumplirse el plazo |
| 2 | Advertencia de cargo por extensión | +1 hora |
| 3 | **Bloqueo diferido** | +N horas |
| 4 | Bloqueo inmediato | Causa grave (salida de geocerca, señal de robo) |

El **bloqueo diferido** es el núcleo del producto: el vehículo sigue operativo, pero al próximo apagado en una ubicación clasificada como segura, no vuelve a encender. El conductor llega a su destino; la plataforma recupera el control. Nadie queda inmovilizado en una vía sola de madrugada.

### 4.4 Protocolo de recuperación física

El bloqueo inmoviliza el activo; recuperarlo es una operación logística que debe estar diseñada antes del primer incidente:

1. **Contacto y resolución voluntaria (0–12 h post-bloqueo).** Canal directo con el arrendatario. La mayoría de los vencimientos son descuido o extensión no comunicada, no mala fe. Se resuelven con pago de la extensión y desbloqueo remoto.
2. **Recuperación asistida (12–48 h).** Equipo de recuperación aliado (servicio de grúa y conductor contratado por evento, no nómina fija) retira el vehículo de la ubicación reportada por telemetría. El mandato del dueño, firmado al ingresar a la plataforma, autoriza expresamente esta gestión.
3. **Vía formal (48 h+ o señal de robo).** Denuncia ante el CICPC con el expediente completo: contrato aceptado, registro de telemetría, comunicaciones. La recuperación con acompañamiento policial nunca se ejecuta por cuenta propia.

**Reglas duras:** ningún miembro del equipo confronta físicamente a un arrendatario; toda recuperación en nivel 2+ queda registrada en video; el costo de recuperación se carga contractualmente al arrendatario y se descuenta de su depósito.

**Métrica objetivo del piloto:** tiempo medio de recuperación < 48 horas y costo medio por evento < $150.

---

## 5. Modelo de negocio

### 5.1 Fuentes de ingreso

**a) Comisión de intermediación (núcleo).**
Take rate de 22–25% del valor de la reserva, dividido entre ambos lados:

- 15% descontado del pago al dueño
- 10% como *service fee* al arrendatario

La división es deliberada. Un 25% cargado a un solo lado empuja al usuario al canal informal — que es el verdadero competidor, no otra aplicación. Dividido, cada parte percibe un costo tolerable y la plataforma captura lo mismo.

*Ejemplo — alquiler de 3 días a US$40/día:*

| Concepto | Monto |
|---|---|
| GBV (valor bruto de reserva) | $120,00 |
| Paga el arrendatario (+10%) | $132,00 |
| Recibe el dueño (−15%) | $102,00 |
| **Ingreso de la plataforma** | **$30,00 (22,7%)** |

**b) Tarifa de protección.**
8–12% de cada reserva, destinada íntegramente al Fondo de Garantía (sección 6). Contablemente es pasivo, no ingreso: no entra al P&L.

**c) Suscripción de telemetría.**
US$5–8/mes por vehículo activo. Ingreso recurrente que ancla al dueño a la plataforma incluso en meses sin alquiler, y financia el costo de conectividad del dispositivo.

**d) Servicios adicionales.**
Entrega a domicilio, conductor adicional, kilometraje extendido, cancelación tardía, alquiler de larga duración.

### 5.2 Pricing por riesgo

El fee del dueño se mantiene fijo y predecible — es una decisión de oferta. El fee del arrendatario es variable según su perfil de riesgo acumulado:

| Perfil del conductor | Service fee |
|---|---|
| Sin historial en plataforma | 14% |
| 1–4 viajes sin incidentes | 11% |
| 5+ viajes sin incidentes | 8% |

Esto convierte el buen comportamiento en un beneficio económico tangible, reduce la siniestralidad del pool y comunica con claridad que el producto real es gestión de riesgo, no reserva de vehículos.

### 5.3 Unit economics por vehículo

*Supuestos a validar con datos de campo en el piloto.*

| Métrica | Valor |
|---|---|
| Tarifa diaria (sedán) | $35–45 |
| Días de utilización / mes | 10 |
| GBV mensual por vehículo | ~$400 |
| Take rate efectivo | 22% |
| **Ingreso neto por vehículo / mes** | **~$88** |
| CAPEX hardware (GPS con corte) | $40–60 (único) |
| OPEX conectividad SIM | $2–4/mes |
| **Recuperación del hardware** | **Mes 1–2** |

**Proyección a 300 vehículos activos:** ~$120.000 de GBV mensual, ~$26.000 de ingreso neto mensual.

### 5.4 Consideraciones cambiarias

Precios denominados en dólares, cobro y liquidación en bolívares al tipo de cambio del día. Dos decisiones que deben estar definidas antes del lanzamiento:

1. **Tratamiento del diferencial cambiario** entre cobro y liquidación: declararlo como ingreso de la plataforma o devolverlo al dueño. Debe ser explícito en los términos.
2. **Float operativo:** la plataforma cobra al reservar y liquida al finalizar el alquiler. Ese desfase genera capital de trabajo que contribuye a la capitalización inicial del Fondo de Garantía.

### 5.5 Infraestructura de cobro

En Venezuela no se puede asumir el stack de pagos de un marketplace estándar. La realidad es multi-riel y la plataforma debe operarlos todos desde el día uno:

| Riel | Usuario típico | Rol en la plataforma |
|---|---|---|
| Pago móvil / transferencia en Bs. | Arrendatario local | Cobro principal doméstico, conversión al tipo de cambio del día |
| Zelle | Diáspora y locales bancarizados en EE. UU. | Cobro en USD sin fricción; conciliación manual → automatizable |
| Tarjeta internacional (pasarela externa) | Diáspora reservando desde el exterior | Único riel con autorización/hold nativo; comisión más alta, se traslada al fee |
| USDT | Usuarios cripto-nativos | Cobro y liquidación instantánea en USD digital |
| Efectivo USD | Último recurso | Solo contra recibo registrado en app; se desincentiva |

**El problema del depósito de garantía.** En mercados con tarjetas de crédito, la garantía es un *hold* no cobrado. En Venezuela eso no existe para la mayoría de los usuarios. Solución: **depósito reembolsable prefondeado** — el arrendatario transfiere el deducible ($300) antes de recibir el vehículo y se le devuelve a las 48 h de la devolución sin incidentes. Es fricción real, y se declara como tal; se mitiga con la escalera de confianza (depósito reducido a partir del quinto viaje sin incidentes) y con hold en tarjeta para quien sí la tiene.

**Decisiones operativas definidas antes del lanzamiento:** custodia de fondos en cuentas separadas por riel; conciliación diaria automatizada; política KYC alineada con la verificación de identidad ya exigida para conducir.

---

## 6. Fondo de Garantía

### 6.1 Encuadre: no es un seguro

La actividad aseguradora en Venezuela está reservada a empresas autorizadas bajo la Ley de la Actividad Aseguradora, con supervisión de la Sudeaseg. Ofrecer "cobertura", "pólizas" o "seguros" sin autorización constituye ejercicio no autorizado de la actividad aseguradora y representa un riesgo existencial para la empresa.

El encuadre correcto es **contractual, no asegurador** — el mismo que utilizaron Turo y Airbnb en sus primeras etapas:

1. El arrendatario asume **responsabilidad total** por daños al vehículo, por contrato.
2. La plataforma ofrece, a cambio de una tarifa, una **exoneración contractual de cobro** (*damage waiver*): renuncia a ejercer su derecho de cobro por encima de un deducible definido.
3. La plataforma no asegura nada. Renuncia a un derecho de cobro que ya poseía. Es una figura jurídicamente distinta.

**Léxico obligatorio:** Plan de Protección · exoneración de responsabilidad · límite de responsabilidad del conductor · deducible.

**Léxico prohibido en app, web, contratos y material comercial:** seguro · póliza · asegurado · cobertura · siniestro · prima.

**Complementos:**
- El RCV de ley es responsabilidad del dueño y requisito de admisión a la plataforma.
- Objetivo de mediano plazo: negociar una **póliza colectiva** con una aseguradora local donde la plataforma actúe como tomador, añadiendo una capa regulada por encima del fondo.

### 6.2 Estructura de capitalización

| Capa | Fuente | Monto / regla |
|---|---|---|
| Semilla | Ronda de aceleradora | $35.000 en cuenta segregada |
| Flujo | 8–12% de cada reserva | ~$12.000/mes a 300 vehículos |
| Techo de exposición | Definido por política | $10.000 por evento |

Por encima del techo responde el arrendatario mediante garantía y acción de cobro. Ese tramo superior es el que debe migrar a una aseguradora regulada apenas el volumen lo permita.

### 6.3 El deducible como mecanismo de solvencia

Este es el punto donde el modelo se sostiene o quiebra, y debe presentarse con honestidad:

*Escenario a 300 vehículos:*

| Variable | Valor |
|---|---|
| Viajes mensuales | ~1.200 |
| Tasa de reclamos estimada | 4% |
| Daño promedio | $300 |
| **Reclamos mensuales sin deducible** | **~$14.400** |
| Aporte mensual al fondo | ~$12.000 |
| **Resultado** | **Déficit** |

Sin deducible, el fondo se agota con daños menores y queda sin capacidad para el evento que realmente importa. Con un **deducible de $300 a cargo del arrendatario**, entre el 70% y el 80% de los reclamos menores no tocan el fondo, que queda reservado para robo, pérdida total y daño mayor.

La política de deducibles no es un detalle operativo: es la condición de solvencia del modelo.

---

## 7. Estructura jurídica y blindaje

### 7.1 Societaria

- **Holding** en Delaware o Panamá — vehículo de inversión para la aceleradora y jurisdicción de la propiedad intelectual.
- **Operadora venezolana** — contratación local, nómina, relación con usuarios y dispositivos.
- **Fondo de Garantía** en vehículo separado o fideicomiso, aislado del riesgo operativo de la plataforma.

### 7.2 Rol de la plataforma

La plataforma es **intermediario tecnológico**, no arrendador. El contrato de arrendamiento se celebra entre dueño y arrendatario; la plataforma actúa por mandato del dueño para la gestión de cobro, verificación y recuperación del activo.

Esta caracterización es la que separa a la empresa de la responsabilidad civil derivada de accidentes de tránsito y debe ser consistente en contratos, términos de uso, comunicación comercial y estructura de facturación. Una inconsistencia en marketing puede desmontar el encuadre completo ante un tribunal.

### 7.3 Contratos y evidencia

- **Términos de uso como contrato de adhesión**, con aceptación registrada: timestamp, IP, dispositivo y versión del documento aceptado. Sin registro de aceptación no hay nada oponible en juicio.
- **Consentimiento expreso y separado** — dos autorizaciones distintas, firmadas por dueño y arrendatario:
  1. Rastreo continuo de ubicación durante el período de alquiler.
  2. Inmovilización remota, con supuestos taxativos y cerrados: vencimiento del plazo + N horas, salida de geocerca, impago verificado, reporte de robo.

  Ningún supuesto discrecional. Una inmovilización sin causa contractual expresa puede interpretarse como vía de hecho.
- **Inspección fotográfica obligatoria** con timestamp y geolocalización en entrega y devolución. Sin registro de entrega, no hay reclamo admisible. Este mecanismo es lo que hace ejecutable la responsabilidad contractual del arrendatario.

### 7.4 Validación pendiente

Este documento presenta estructura estratégica, no asesoría legal. Antes del lanzamiento se requiere validación por abogado venezolano especializado en societario y seguros sobre: (a) el encuadre del *damage waiver* frente a la Sudeaseg, (b) la redacción del mandato de intermediación, y (c) los supuestos de inmovilización frente a la normativa de tránsito y protección de datos. Está presupuestado en el uso de fondos.

---

## 8. Capa de decisión: inmovilización segura

### 8.1 Principio de autoridad asimétrica

El sistema de decisión **nunca autoriza un bloqueo; solo puede vetarlo o posponerlo.**

El derecho a inmovilizar nace exclusivamente del contrato. La capa algorítmica no crea ese derecho ni adelanta su ejercicio. Su única función es diferir la ejecución cuando las condiciones del momento o del lugar son inseguras.

La consecuencia jurídica es determinante: el sistema nunca bloqueó de más — solo bloqueó de menos por prudencia. Esa asimetría es defendible. La inversa transfiere responsabilidad a la empresa por cada decisión automatizada.

### 8.2 Arquitectura de cuatro capas

| Capa | Función | Naturaleza |
|---|---|---|
| 1. Disparador contractual | ¿Existe causa legítima? | Regla dura. Sin IA. |
| 2. Compuerta de seguridad | ¿Vehículo detenido y apagado? | **Determinista.** Velocidad 0 sostenida. Nunca probabilístico. |
| 3. Evaluación contextual | ¿Es seguro este lugar y momento? | Modelo predictivo |
| 4. Supervisión humana | Casos ambiguos | Operador |

La capa 2 no admite modelos probabilísticos bajo ninguna circunstancia. Determinar si un vehículo está detenido es una condición lógica, no una inferencia.

Durante los primeros meses de operación, **todos los bloqueos pasan por operador humano**, sin excepción. La automatización se habilita progresivamente por tipo de causa y solo con evidencia acumulada.

### 8.3 Roadmap honesto del componente predictivo

Sin datos propios no hay modelo. La progresión declarada:

- **v1 (meses 0–12):** motor de reglas determinista + mapa de riesgo zonal construido manualmente con fuentes locales + operador humano en el 100% de los casos.
- **v2 (meses 12+):** con 6–12 meses de telemetría propia, el modelo aprende de dónde y cuándo la flota real se detiene sin incidentes, y ajusta la clasificación de ubicación segura con datos observados.

### 8.4 Integridad del dispositivo

El hardware es el punto físico de falla y debe tratarse con la misma honestidad que el fondo:

- **Instalación profesional oculta**, no visible desde el habitáculo, realizada por técnico aliado en la incorporación del vehículo.
- **Heartbeat con alerta de desconexión:** la pérdida de señal del dispositivo es en sí misma un evento de riesgo. Silencio > N minutos durante un alquiler activo dispara protocolo de contacto y, sostenido, causal contractual de bloqueo/recuperación.
- **Batería de respaldo** interna: desconectar la alimentación del vehículo no apaga el dispositivo de inmediato.
- **Dispositivo señuelo opcional** en vehículos de mayor valor: uno visible que absorbe el intento de manipulación, uno oculto que sigue reportando. Práctica estándar en flotas de la región.
- **Honestidad del límite:** un atacante determinado con tiempo y herramientas puede neutralizar cualquier dispositivo. La defensa no es un hardware infalible sino la defensa en profundidad: verificación de identidad real, depósito prefondeado, contrato ejecutable, historial en plataforma que se pierde, y denuncia formal con expediente completo. El dispositivo eleva el costo del robo; el sistema completo lo hace irracional.

### 8.5 Auditabilidad

Cada decisión registra entrada, versión del modelo, score, resultado y operador responsable, en log inmutable. Sin ese registro, la capa algorítmica no protege a la empresa: la expone.

### 8.6 Activo estratégico y línea B2B

El dataset resultante — comportamiento vehicular real, patrones de detención y zonas de riesgo verificadas en territorio venezolano — no existe hoy en manos de ningún actor y no es replicable sin operar una flota.

Sobre él se construye una segunda línea de negocio: **licenciamiento del motor de inmovilización segura** a financiadoras de vehículos, empresas de leasing y operadores de flota, que hoy ejecutan bloqueos sin ninguna capa de evaluación de contexto. Es un mercado B2B con ciclo de venta más largo pero márgenes superiores y menor exposición operativa que el marketplace.

---

## 9. Uso de fondos — US$150.000

| Partida | Monto | % | Detalle |
|---|---|---|---|
| Producto e ingeniería | $40.000 | 27% | App, backend, integración de telemetría, motor de reglas |
| Fondo de Garantía (semilla) | $35.000 | 23% | Cuenta segregada. No disponible para operación |
| Hardware de telemetría | $25.000 | 17% | ~450–500 dispositivos con corte de arranque + SIM |
| Legal y constitución | $15.000 | 10% | Holding + operadora, contratos, validación Sudeaseg, protección de datos |
| Adquisición de oferta y demanda | $20.000 | 13% | Incentivos a dueños fundadores, adquisición de conductores |
| Operación y reserva | $15.000 | 10% | Equipo de soporte, atención de reclamos, contingencia |
| **Total** | **$150.000** | **100%** | |

**Runway estimado:** 15–18 meses con equipo reducido.

Nota sobre la asignación: el Fondo de Garantía se presenta como partida separada y restringida precisamente porque no es capital operativo. Consumirlo para operación destruye la promesa central del producto.

---

## 10. Hoja de ruta y adquisición

### 10.1 Fases

| Fase | Período | Objetivo |
|---|---|---|
| **0 — Fundación** | Meses 1–3 | Estructura societaria, contratos validados, selección de proveedor de hardware, MVP funcional |
| **1 — Piloto cerrado** | Meses 4–6 | 25–40 vehículos en una ciudad. Validar utilización real, tasa de reclamos y costo de recuperación. Operador humano al 100% |
| **2 — Densidad** | Meses 7–12 | 150 vehículos. Ajuste de deducible y take rate con datos reales. Primera negociación con aseguradora local |
| **3 — Expansión** | Meses 13–18 | 300+ vehículos, segunda ciudad. v2 del motor contextual. Prototipo de licenciamiento B2B |

**Estrategia de ciudad inicial:** concentrar oferta y demanda en un solo mercado hasta alcanzar densidad. Un marketplace disperso no funciona; la disponibilidad percibida es función de la densidad local, no del total de vehículos. Criterios de selección: densidad de parque privado, aeropuerto internacional con tráfico de diáspora, actividad turística/corporativa, y red de contactos fundadora en el terreno. Con esos criterios, el Área Metropolitana de Caracas es la candidata por defecto; la decisión final se toma con los compromisos de dueños fundadores en mano.

### 10.2 Adquisición de oferta (primero)

En un marketplace con garantía, la oferta es el cuello de botella y se recluta a mano:

- **Dueños fundadores (25–40):** reclutados directamente de los grupos informales donde ya alquilan — es decir, dueños que ya aceptaron el riesgo y entienden el problema. Incentivo: hardware e instalación sin costo + 0% de comisión los primeros 3 meses + estatus fundador permanente (comisión preferencial).
- **Objetivo pre-capital:** cartas de compromiso de dueños fundadores antes del cierre de la ronda. Es la evidencia de tracción más barata y más creíble que puede presentar este proyecto.

### 10.3 Adquisición de demanda

- **Diáspora (canal principal de lanzamiento):** campañas digitales segmentadas a venezolanos en el exterior que planifican visita. Reservan con antelación, pagan en USD con tarjeta o Zelle, y son el perfil de menor riesgo de no devolución (vínculos familiares verificables, boleto de retorno).
- **Alianzas locales:** talleres (cliente sin carro temporal), posadas y operadores turísticos, empresas sin flota.
- **El canal informal como embudo:** presencia activa en los mismos grupos de WhatsApp e Instagram donde hoy ocurre la transacción, con un mensaje único: «alquila con garantía».

---

## 11. Proyección financiera

*Escenario base. Todos los supuestos operativos provienen de las secciones 5 y 6 y se validan en Fase 1.*

| | Mes 6 | Mes 12 | Mes 18 | Mes 24 |
|---|---|---|---|---|
| Vehículos activos | 40 | 150 | 300 | 450 |
| GBV mensual | $16.000 | $60.000 | $120.000 | $180.000 |
| Ingreso neto mensual (comisión + suscripción) | $3.800 | $14.100 | $28.200 | $42.300 |
| OPEX mensual (equipo, soporte, infraestructura) | $9.000 | $13.000 | $17.000 | $22.000 |
| **Resultado operativo mensual** | **−$5.200** | **+$1.100** | **+$11.200** | **+$20.300** |

- **Punto de equilibrio operativo:** ~140–160 vehículos activos, proyectado para el mes 11–13.
- **Estructura de OPEX:** equipo reducido en Venezuela (4–6 personas: ingeniería, operaciones/recuperación, soporte), infraestructura cloud, conectividad de flota. El costo laboral local es una ventaja estructural del modelo.
- **Sensibilidad honesta:** la variable que quiebra el escenario no es la utilización sino la **siniestralidad**. A 8% de tasa de reclamos (el doble de lo estimado), el fondo requiere subir la tarifa de protección o el deducible — por eso ambos parámetros se declaran ajustables por contrato desde el día uno y el piloto existe para medirlos antes de escalar.
- La ronda de $150.000 cubre el déficit acumulado pre-equilibrio (~$45.000–55.000) con margen, además del CAPEX de hardware y la semilla del fondo.

---

## 12. Métricas de seguimiento

**Salud del marketplace**
- Vehículos activos y días de utilización por vehículo
- GBV mensual y take rate efectivo
- Tasa de conversión de búsqueda a reserva
- Ratio de reincidencia de dueños y de arrendatarios

**Salud del riesgo (las que definen la viabilidad)**
- Tasa de reclamos por cada 100 viajes
- Severidad promedio por reclamo
- Ratio de aportes al fondo sobre pagos del fondo
- Eventos de no devolución y tiempo medio de recuperación
- Tasa de bloqueos ejecutados sobre bloqueos disparados
- Incidentes de bloqueo en condiciones inseguras — **objetivo: cero**

---

## 13. Riesgos y mitigación

| Riesgo | Impacto | Mitigación |
|---|---|---|
| Reclasificación regulatoria del *damage waiver* como actividad aseguradora | Existencial | Validación legal previa; léxico controlado; migración a póliza colectiva con aseguradora regulada |
| Siniestralidad superior a la proyectada | Alto | Deducible; pricing por riesgo; techo de exposición; piloto cerrado antes de escalar |
| Robo o pérdida total del vehículo | Alto | Telemetría; geocerca; protocolo de recuperación; verificación estricta de conductor |
| Manipulación o desconexión del dispositivo | Alto | Instalación oculta; heartbeat con alerta; batería de respaldo; señuelo; depósito y expediente ejecutable (sección 8.4) |
| Incidente derivado de una inmovilización | Existencial (reputacional y penal) | Compuerta determinista; bloqueo diferido; supervisión humana; consentimiento expreso |
| Fuga de transacciones fuera de la plataforma | Alto | El Plan de Protección y la telemetría solo operan dentro; sin plataforma no hay garantía |
| Fricción del depósito prefondeado deprime la conversión | Medio | Hold en tarjeta para quien la tiene; depósito decreciente por historial; medir conversión por riel en el piloto |
| Disponibilidad y costo de conectividad para los dispositivos | Medio | Multi-operador; almacenamiento local y sincronización diferida en el dispositivo |
| Volatilidad cambiaria | Medio | Denominación en dólares; ventana corta entre cobro y liquidación; política de spread definida |
| Concentración en una sola ciudad | Medio | Deliberada en Fases 0–2 (densidad primero); segunda ciudad en Fase 3 con playbook validado |

---

## 14. Por qué ahora y por qué este equipo

### 14.1 Por qué ahora

Cuatro condiciones que no existían hace cinco años coinciden hoy:

1. **Dolarización de facto.** Los precios en USD son estables y socialmente aceptados. Un marketplace con pricing en dólares y liquidación multi-riel es operable; en la era de control cambiario estricto no lo era.
2. **Hardware commoditizado.** Un dispositivo GPS con corte de arranque cuesta $40–60. La telemetría con inmovilización dejó de ser tecnología de flota corporativa para ser un CAPEX recuperable en el primer mes de alquiler.
3. **Demanda visible y creciente.** El flujo de visitas de la diáspora y la reactivación parcial del turismo y la actividad comercial generan demanda de movilidad que el parque de rent-a-car formal, diezmado, no puede atender.
4. **Vacío competitivo estructural.** Los incumbentes globales del P2P no pueden entrar (sin seguros, sin rieles de pago, sin apetito de riesgo país) y los actores locales tienen piezas sueltas (hardware sin marketplace, flota sin tecnología). La ventana es real pero no permanente: el primero que acumule el dataset de riesgo y la red de dueños instalada construye el foso.

**Y por qué es venture-scale:** el marketplace venezolano es el campo de prueba, no el techo. El activo exportable es la infraestructura de confianza — motor de inmovilización segura + playbook de garantía contractual sin asegurador — replicable en cualquier mercado de LatAm con informalidad alta y seguros débiles, y licenciable B2B a financiadoras y flotas (sección 8.6).

### 14.2 Por qué este equipo

*Sección a completar con perfiles del equipo fundador.*

Elementos a desarrollar:
- Experiencia técnica en desarrollo de producto e integración de hardware
- Conocimiento del contexto operativo, regulatorio y cambiario venezolano
- Evidencia de la demanda informal existente (capturas de grupos, transacciones observadas, entrevistas a dueños y arrendatarios)
- Compromiso de dueños fundadores para el piloto — la métrica más persuasiva para una aceleradora es oferta comprometida antes del capital

---

## Anexo — Preguntas previsibles del comité

**¿Quién absorbe la pérdida cuando un vehículo no aparece?**
La plataforma, hasta el techo de $10.000 por evento, con cargo al Fondo de Garantía. Por encima de ese monto responde el arrendatario por vía contractual. El fondo está diseñado para ese escenario, no para daños menores — que es exactamente la función del deducible.

**¿Cómo se capitaliza un fondo de garantía con $150.000?**
No se capitaliza completo con la ronda. Se siembra con $35.000 y se alimenta con el 8–12% de cada reserva. La restricción real durante los primeros meses es de escala: el fondo solo soporta un volumen limitado de vehículos, y por eso el crecimiento se limita deliberadamente hasta que el flujo mensual cubra la exposición proyectada.

**¿Qué impide que dueño y arrendatario cierren por fuera después del primer contacto?**
La garantía y la telemetría no son transferibles fuera de la plataforma. El dueño que cierra por fuera renuncia al respaldo económico, al rastreo y a la capacidad de recuperación. Es el mismo mecanismo de retención que sostiene a Turo y Airbnb.

**¿Qué pasa si el arrendatario desconecta el dispositivo?**
La desconexión es en sí misma un evento: el heartbeat la detecta en minutos y constituye causal contractual inmediata. El dispositivo tiene batería de respaldo e instalación oculta, y en vehículos de mayor valor se instala un señuelo. Pero la respuesta honesta es que el hardware solo eleva el costo del robo — lo que lo vuelve irracional es el sistema completo: identidad verificada, depósito de $300 ya entregado, contrato ejecutable y denuncia con expediente de telemetría (sección 8.4).

**¿Cómo cobran en un país sin infraestructura de tarjetas de crédito?**
Operando todos los rieles reales del mercado: pago móvil en bolívares, Zelle, USDT y tarjeta internacional para la diáspora (sección 5.5). El depósito de garantía no depende de un hold de tarjeta: es prefondeado y reembolsable. Es más fricción que en un mercado desarrollado, y es exactamente la fricción que impide que un competidor global entre.

**¿Por qué no lo hace un rent-a-car tradicional o una empresa local de GPS?**
El rent-a-car tiene flota propia: su modelo es CAPEX-intensivo y su incentivo es proteger su utilización, no habilitar la de terceros. La empresa de GPS tiene el dispositivo pero no el contrato, ni el fondo, ni el marketplace, ni la relación con ambos lados de la transacción. La barrera no es ninguna pieza aislada — es la integración de las cinco (marketplace, hardware, contrato, fondo, motor de decisión) y el dataset que solo genera operarlas juntas.

**¿Es realmente IA o es un motor de reglas?**
En v1 es un motor de reglas determinista con supervisión humana, y se presenta como tal. El componente predictivo entra en v2, cuando exista telemetría propia suficiente para entrenarlo. Declararlo de otro modo sería insostenible ante la primera pregunta técnica.

**¿Por qué Venezuela y no un mercado con mejor infraestructura?**
Porque la fricción es máxima y la solución es defendible. En un mercado con seguros funcionales, esto es una app de reservas. Aquí, el activo diferencial es la capa de control y recuperación — y el dataset que genera no es replicable sin operar en el terreno.

---

*Documento de trabajo. Las cifras de utilización, siniestralidad y tarifa son supuestos a validar en el piloto cerrado de la Fase 1.*
