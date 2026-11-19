# Respaldo local

## Purpose

Conservar la continuidad del piloto mediante respaldos portables que el equipo pueda exportar y recuperar desde el navegador.

## ADDED Requirements

### Requirement: Apertura autónoma

La aplicación SHALL operar en un solo equipo mediante un archivo HTML que reúna la interfaz, los estilos y la lógica. El flujo principal SHALL funcionar sin conexión, abriendo el archivo con doble clic.

#### Scenario: Abrir el piloto sin conexión

- **WHEN** el usuario abre el archivo HTML local en el navegador sin conexión
- **THEN** puede usar la interfaz, cargar un directorio o respaldo y registrar solicitudes.

### Requirement: Exportación de respaldo

La aplicación SHALL permitir descargar un JSON versionado con el directorio, los perfiles, las solicitudes, los historiales y los datos necesarios para continuar consecutivos y rotación. SHALL indicar que los cambios en memoria requieren exportación para conservarse al cerrar.

#### Scenario: Obtener un respaldo de la sesión

- **WHEN** el usuario exporta un respaldo después de registrar y actualizar una solicitud
- **THEN** el navegador descarga un JSON que contiene la solicitud, sus eventos y el estado de asignación.

### Requirement: Recuperación de respaldo

La aplicación SHALL validar el respaldo antes de sustituir la sesión en memoria. SHALL pedir confirmación antes de reemplazar datos de una sesión en uso y conservarla si el archivo es inválido o el usuario cancela.

#### Scenario: Continuar después de reabrir

- **GIVEN** un respaldo válido exportado después de varias radicaciones
- **WHEN** el usuario reabre el HTML, importa el respaldo y registra una solicitud en el mismo mes
- **THEN** se recuperan los tickets y sus historiales, el nuevo radicado no coincide con uno ya emitido y la asignación continúa en el siguiente agente.

#### Scenario: Rechazar un respaldo incompatible

- **WHEN** el usuario carga un respaldo con versión incompatible, datos incompletos o referencias inválidas
- **THEN** la aplicación explica el rechazo y conserva íntegramente el estado anterior.
