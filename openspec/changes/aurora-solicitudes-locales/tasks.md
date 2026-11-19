# Tareas de implementación

## 1. Interfaz local y radicación

- [x] 1.1 Crear `aurora.html` con formularios, bandeja, panel de detalle y selector de perfil. Verificar que abre con doble clic, sin conexión, y que los controles son utilizables en una pantalla estrecha.
- [x] 1.2 Implementar la carga de directorios JSON y CSV. Verificar con datos ficticios la búsqueda por NIT y la conservación del directorio ante un archivo inválido.
- [x] 1.3 Implementar la validación del formulario, el radicado mensual y la asignación rotativa. Probar cinco registros válidos y un intento inválido intercalado. Comprobar unicidad, orden de asignación y primer evento.

## 2. Seguimiento y resolución

- [x] 2.1 Implementar la búsqueda, los filtros y el detalle. Verificar que el resultado combina los filtros y que el detalle identifica el responsable.
- [x] 2.2 Implementar cambios de estado e historial. Verificar que los eventos distinguen operador y responsable y que los comentarios se muestran como texto.
- [x] 2.3 Implementar fecha de resolución, duración y cumplimiento. Probar el límite exacto, un segundo después, un caso pendiente y el cierre posterior a una resolución.

## 3. Respaldo y prueba integral

- [x] 3.1 Incorporar descarga JSON versionada y un indicador visible de cambios pendientes. Inspeccionar un archivo exportado y verificar que contiene los datos necesarios para recuperar la sesión.
- [x] 3.2 Implementar la recuperación con validación y confirmación. Verificar que un respaldo inválido y una restauración cancelada preservan el estado previo.
- [x] 3.3 Probar en el navegador el flujo completo con datos ficticios. Abrir el HTML, importar clientes, radicar, resolver, exportar, cerrar, reabrir y restaurar. Verificar historial, consecutivo mensual y continuidad de la rotación.
