# Diseño del piloto

## Context

El repositorio contiene el flujo OpenSpec y su CLI. La aplicación será el primer entregable ejecutable. El piloto usará una sola sesión activa en el navegador del equipo de atención.

## Goals / Non-Goals

**Goals**

- Distribuir un HTML autónomo y permitir recuperar la sesión mediante JSON.
- Mantener la coherencia entre solicitudes, historial, consecutivos y rotación.
- Poder probar el flujo con clientes ficticios y marcas de tiempo controladas.

**Non-Goals**

- Sincronización entre sesiones, control de acceso y auditoría resistente a alteraciones.

## Decisions

- Integrar HTML5, CSS3 y JavaScript estándar en `aurora.html`. Los formularios, estilos y acciones estarán disponibles desde `file://`. El CSS adaptará la bandeja a pantallas estrechas sin impedir la consulta del detalle.
- Mantener el estado en objetos y arreglos. Preparar y validar los cambios antes de aplicarlos para que un registro inválido no consuma un consecutivo ni avance la rotación. Usar el mes local del equipo en el radicado y marcas de tiempo ISO 8601 en el respaldo. Si se agotara el consecutivo de cuatro dígitos del mes, rechazar la radicación con un mensaje explícito.
- Separar el operador activo del responsable del ticket. El primer evento registra la radicación con el operador seleccionado. Los siguientes eventos conservan los estados anterior y nuevo y se agregan al final del historial.
- Comparar el tiempo transcurrido en milisegundos con el umbral exacto. Redondear solo para mostrar el valor. Mantener como referencia la primera resolución. Ante un reloj que sitúe la resolución antes de la recepción, rechazar ese cambio y pedir verificar la hora.
- Leer archivos seleccionados por el usuario y descargar el respaldo con las capacidades estándar del navegador. El respaldo versionado conserva perfiles, clientes, tickets, eventos, consecutivos por mes e índice circular. Validar en memoria la estructura, unicidad y referencias antes de sustituir la sesión. Para los clientes de prueba, usar campos `nit` y `razon_social` en JSON y CSV, con NIT como texto.
- Mostrar el estado pendiente de exportación cuando la sesión cambie. Tratar los nombres y comentarios importados como texto al mostrarlos en la interfaz.

## Risks / Trade-offs

- Cerrar con cambios pendientes puede perder datos. Mostrar un aviso visible y ofrecer la descarga del respaldo en la interfaz principal.
- La hora depende del equipo y el perfil activo lo declara el operador. Usar estos datos como trazabilidad del piloto.
- Restaurar un respaldo antiguo recupera su estado completo. Mostrar la fecha del respaldo disponible en el archivo antes de confirmar el reemplazo de una sesión en uso.
