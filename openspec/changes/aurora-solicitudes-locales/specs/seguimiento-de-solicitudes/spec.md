# Seguimiento de solicitudes

## Purpose

Consultar el estado de cada caso, atribuir sus actualizaciones y medir el tiempo transcurrido hasta la resolución.

## ADDED Requirements

### Requirement: Selección de perfil local

La aplicación SHALL permitir seleccionar uno de cuatro agentes o el coordinador como perfil activo y exigir esa selección antes de registrar o actualizar una solicitud.

#### Scenario: Cambiar de operador

- **GIVEN** un ticket registrado por un agente
- **WHEN** el coordinador selecciona su perfil y actualiza el ticket
- **THEN** el historial atribuye la actualización al coordinador y conserva la autoría del registro.

### Requirement: Bandeja y detalle

La bandeja SHALL mostrar radicado, cliente, responsable y estado. SHALL permitir buscar por radicado o cliente, filtrar por estado y responsable, y abrir el detalle con su historial.

#### Scenario: Buscar dentro de los filtros activos

- **WHEN** el usuario busca un cliente y filtra por estado y responsable
- **THEN** la bandeja presenta solo solicitudes que coinciden con los tres criterios y permite abrir sus detalles.

### Requirement: Estados e historial

La aplicación SHALL admitir los estados Nuevo, En proceso, Pendiente logística, Pendiente ventas, Resuelto y Cerrado. SHALL registrar cada cambio de estado con fecha y hora, perfil activo, estado anterior, estado nuevo y comentario cuando se capture. SHALL presentar el historial en orden cronológico y en modo de solo lectura.

#### Scenario: Registrar avance en un caso

- **WHEN** el operador cambia un caso de En proceso a Pendiente logística con un comentario
- **THEN** el nuevo estado aparece en la bandeja y el historial incorpora el evento sin alterar los eventos anteriores.

### Requirement: Medición del plazo de resolución

Al pasar a Resuelto por primera vez, la aplicación SHALL registrar la fecha de resolución, calcular el tiempo transcurrido en horas corridas e indicar si es menor o igual a 48 horas. SHALL exigir una resolución registrada antes de cerrar y conservar su medición al cerrar el caso.

#### Scenario: Cumplir justo en el límite

- **WHEN** un caso se resuelve exactamente 48 horas después de la recepción
- **THEN** la aplicación muestra 48 horas y registra que el caso cumple el plazo.

#### Scenario: Superar el límite

- **WHEN** el caso se resuelve un segundo después de cumplirse las 48 horas
- **THEN** la aplicación registra que el caso quedó fuera de plazo aunque la cifra mostrada se redondee.

#### Scenario: Consultar un caso sin resolver

- **WHEN** el usuario abre un caso pendiente de resolución
- **THEN** el detalle indica que aún no tiene tiempo de resolución ni resultado de cumplimiento.
