# Matriz inicial de riesgos de sistemas

**Integrantes:**

- Manuela Castaño García
- Juan Pablo Orozco Motta

Docente: Juan Guillermo Duque

## 1. Caso y contexto actualizado

El análisis se enfoca en el proceso de control de acceso y gestión de identidades en los equipos del área de recepción del laboratorio clínico del Centro Policlínico del Olaya (CPO). Se evaluará el uso compartido de cuentas de Windows y el acceso a los sistemas de facturación, Tharsis (registro de exámenes) y el aplicativo de autorizaciones de Salud Total por parte de auxiliares y bacteriólogas fuera del horario principal.

## 2. Supuestos

- Cuentas de usuario de Windows en los computadores del área del front.
- Contraseñas y credenciales de acceso del personal
- Sistema Tharsis para el registro y gestión de exámenes de laboratorio.
- Aplicativo de autorizaciones de la EPS Salud Total.
- Módulo de facturación (Caja) del laboratorio.
- Proceso de validación y registro de resultados por parte de auxiliares y bacteriólogas.
- Malos procedimientos en la mesa de ayuda con tickets; esto debe verificarse con las evidencias de ITIL y COBIT.

## 3. Activos y procesos analizados

| **ID** | **Activo o proceso** | **Tipo** |
| --- | --- | --- |
| A1 | Cuentas de usuario de Windows de los computadores del front | Proceso / infraestructura |
| A2 | Contraseñas y credenciales de acceso del personal | Información |
| A3 | Tharsis: registros de exámenes y resultados | Aplicación / información |
| A4 | Aplicativo de autorizaciones de Salud Total (órdenes, fórmulas, historias clínicas) | Aplicación / información |
| A5 | Proceso de bajas y rotación de personal (accesos) | Proceso |
| A6 | Computadores del front, caja y agenda (servicio en la franja 6:00–10:00 a.m.) | Infraestructura / servicio |
| A7 | Gobierno y políticas de control de acceso de TI en CPO | Proceso de gestión |

## 4. Resumen priorizado de la matriz

Orden por nivel de riesgo (probabilidad × impacto); en empate, primero el de mayor impacto.

| **ID** | **Riesgo** | **Prob.** | **Impacto** | **Nivel** | **Clasif.** | **Marco relacionado** |
| --- | --- | --- | --- | --- | --- | --- |
| R-01 | Cuentas de Windows compartidas | 5 | 4 | **20** | Crítico | ISO/IEC 27001 (control de acceso) |
| R-02 | Contraseñas visibles en el puesto de trabajo | 4 | 4 | **16** | Alto | ISO/IEC 27001 (gestión de credenciales) |
| R-03 | Alteración de resultados sin responsable identificable | 3 | 5 | **15** | Alto | ISO/IEC 27001 (registros y trazabilidad) |
| R-04 | Consulta indebida de historias clínicas | 3 | 5 | **15** | Alto | ISO/IEC 27001 (mínimo privilegio) |
| R-05 | Falla de sistemas sin gestión formal de incidentes | 3 | 4 | **12** | Medio | ITIL (gestión de incidentes) |

## 5. Matriz de riesgos (una tabla por riesgo)

### R-01 · Cuentas de Windows compartidas

| Campo | Detalle |
| --- | --- |
| **Activo o proceso afectado** | Cuentas de usuario de Windows de los computadores del front. |
| **Amenaza** | Auxiliares y bacteriólogas o cualquier persona con acceso al equipo, operan con la cuenta de un transcriptor. |
| **Vulnerabilidad** | Auxiliares y bacteriólogas no tienen usuarios propios; la práctica habitual es usar las cuentas de los transcriptores. |
| **Riesgo** | Un dato de paciente, un resultado o un movimiento de caja podría ser consultado o modificado sin que se pueda saber quién lo hizo. Esto impide investigar incidentes y asignar responsabilidades. |
| **Probabilidad** | 5 |
| **Impacto** | 4 |
| **Nivel de riesgo** | **20 (Crítico)** |
| **Control actual o evidencia** | Existe un usuario de Windows por transcriptor, pero no uno por persona que usa el equipo. No se conoce un control que compense esta debilidad. |
| **Control propuesto** | Crear una cuenta individual de Windows para cada auxiliar y bacterióloga con permisos según su rol, y emitir una política escrita que prohíba usar cuentas ajenas. |
| **Justificación de la prioridad** | Es el riesgo principal del caso; afecta críticamente el principio de trazabilidad y confidencialidad requerido por ISO/IEC 27001. |

### R-02 · Contraseñas visibles en el puesto de trabajo

| Campo | Detalle |
| --- | --- |
| **Activo o proceso afectado** | Contraseñas y credenciales de acceso del personal |
| **Amenaza** | Persona no autorizada (paciente, acompañante o personal ajeno al laboratorio) que ve la contraseña y la utiliza. |
| **Vulnerabilidad** | La contraseña está escrita en un papel pegado a la pantalla y no existe otro mecanismo para que otra persona ingrese cuando el titular termina su turno. |
| **Riesgo** | Alguien sin autorización podría ingresar a un equipo del front y ver órdenes, historias clínicas o resultados, porque la contraseña está expuesta de forma permanente, lo que implicaría exposición de datos personales de salud. |
| **Probabilidad** | 4 |
| **Impacto** | 4 |
| **Nivel de riesgo** | **16 (Alto)** |
| **Control actual o evidencia** | Las contraseñas están escritas en un papel y pegadas en cada pantalla de los computadores |
| **Control propuesto** | Retirar las contraseñas escritas, usar contraseñas personales, definir una política de contraseñas y configurar bloqueo automático de pantalla de Windows. Realizar capacitación se la importancia del buen manejo de las contraseñas |
| **Justificación de la prioridad** | Probabilidad e impacto altos y control de bajo costo. Su corrección es rápida y reduce la exposición inmediata. |

### R-03 · Alteración de resultados sin responsable identificable

| Campo | Detalle |
| --- | --- |
| **Activo o proceso afectado** | Tharsis: registros de exámenes y resultados |
| **Amenaza** | Usuario con acceso a Tharsis (propio o ajeno) que modifica o elimina un resultado por error o con intención. |
| **Vulnerabilidad** | Las acciones quedan registradas bajo cuentas compartidas y no se conoce una revisión periódica de los registros de actividad. |
| **Riesgo** | Un resultado de examen podría ser alterado o registrado erróneamente sin poder identificar al responsable, afectando la integridad de resultados que la EPS usa para decisiones médicas. |
| **Probabilidad** | 3 |
| **Impacto** | 5 |
| **Nivel de riesgo** | **15 (Alto)** |
| **Control actual o evidencia** | Los computadores continúan en uso después de las 10:00 a.m. sin requerir nuevas autenticaciones para el sistema de laboratorio |
| **Control propuesto** | Configurar bloqueo automatico de sesión en Tharsis, verificar o activar el registro de usuario, fecha y acción sobre creación y modificación de resultados. Procedimiento escrito para corregir resultados dejando constancia del motivo y de quién lo hizo. |
| **Justificación de la prioridad** | Probabilidad media por no haber incidentes conocidos, pero impacto máximo por afectar la integridad de datos clínicos. |

### R-04 · Consulta indebida de historias clínicas

| Campo | Detalle |
| --- | --- |
| **Activo o proceso afectado** | Aplicativo de autorizaciones de Salud Total (órdenes, fórmulas, historias clínicas) |
| **Amenaza** | Personal del laboratorio sin necesidad de consultar historias clínicas que accede a ellas desde una sesión ajena. |
| **Vulnerabilidad** | Los permisos del aplicativo se asignan a la cuenta del transcriptor y, al compartir la sesión, cualquier usuario del equipo hereda esos privilegios; no se aplica el principio de mínimo privilegio. |
| **Riesgo** | Historias clínicas y fórmulas podrían ser consultadas por personas cuyo rol no lo requiere, generando exposición de datos de pacientes y posible incumplimiento de las obligaciones de confidencialidad frente a la EPS y de la Ley 1581 de 2012. |
| **Probabilidad** | 3 |
| **Impacto** | 5 |
| **Nivel de riesgo** | **15 (Alto)** |
| **Control actual o evidencia** | No se conoce una revisión de usuarios ni de perfiles del aplicativo (a verificar). |
| **Control propuesto** | Solicitar a Salud Total credenciales individuales con perfil según el rol de cada persona. |
| **Justificación de la prioridad** | La probabilidad se mantiene en 3 porque depende de decisiones de la EPS y de que alguien intente la consulta. |

### R-05 · Falla de sistemas sin gestión formal de incidentes

| Campo | Detalle |
| --- | --- |
| **Activo o proceso afectado** | Computadores del front, caja y agenda (servicio en la franja 6:00–10:00 a.m.) |
| **Amenaza** | Falla de un equipo, de Tharsis o de caja, o bloqueo de acceso, durante la franja de atención de pacientes. |
| **Vulnerabilidad** | Aunque existe un proceso de gestión de incidentes (tickets) No es común utilizarlo, se prefiere escribir directamente a los técnicos por whatsapp y esto implica que no haya registro de incidentes. |
| **Riesgo** | Si un sistema falla en la franja de atención, la facturación y el paso de pacientes a toma de muestras podrían retrasarse y la entrega de resultados a la EPS verse afectada, porque las fallas se atienden de forma informal y sin tiempos definidos. |
| **Probabilidad** | 3 |
| **Impacto** | 4 |
| **Nivel de riesgo** | **12 (Medio)** |
| **Control actual o evidencia** | No se conoce evidencia de tickets ni del acuerdo de nivel de servicio aplicado (a verificar con las evidencias de ITIL). |
| **Control propuesto** | Procedimiento de incidentes que registre cada falla en un ticket con prioridad, responsable y tiempo objetivo alineado con el nivel de servicio pactado con Salud Total. |
| **Justificación de la prioridad** | Prioridad media: afecta la continuidad del servicio, no la confidencialidad, que es la principal preocupación del caso. |