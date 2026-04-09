# Cambios Implementados - Prestamo Mora App

## ✅ 1. Resaltar en ROJO cuando tengan cuotas vencidas

### Cambios en `src/js/app.js`:
- **Nueva función `clienteConVencidas(c)`**: Detecta si un cliente tiene cuotas vencidas
- **Nueva función `contarVencidas(c)`**: Cuenta cuántas cuotas están vencidas
- **Modificación en `clientRowHTML()`**: 
  - Agrega borde rojo a la izquierda (4px solid var(--danger))
  - Fondo rojizo semitransparente
  - Avatar se pone rojo cuando hay vencidas
  - Muestra indicador: "🔴 3 cuotas vencidas" (por ejemplo)
  - El monto del capital se muestra en rojo

### Cambios en `index.html`:
- Se agregó opción "Con cuotas vencidas" en el select de estado

---

## ✅ 2. Que se pueda filtrar por fecha de antigüedad

### Cambios en `index.html`:
- Se agregaron dos campos de fecha en la barra de herramientas de clientes:
  - `filter-fecha-desde`: Filtra prestamos a partir de esta fecha
  - `filter-fecha-hasta`: Filtra prestamos hasta esta fecha
- Se agregó botón "Limpiar fechas" para resetear los filtros

### Cambios en `src/js/app.js`:
- **Modificación en `renderClients()`**:
  - Captura los valores de las fechas
  - Filtra clientes por `fechaPrestamo` dentro del rango
  - Soporta filtro de antigüedad combinado con búsqueda y estado
  
- **Nueva función `clearDateFilters()`**:
  - Limpia los campos de fecha
  - Vuelve a renderizar la lista

- **Se exportó `clearDateFilters`** como función global (window.clearDateFilters)

---

## ✅ 3. Que se deje editar después de creado el cliente

### Cambios en `index.html`:
- Se agregó `<div id="edit-note">` para mostrar advertencias cuando hay cuotas pagadas
- El modal ahora soporta tanto creación como edición

### Cambios en `src/js/app.js`:

**Nueva función `openEditModal(id)`**:
- Abre el modal con datos del cliente precargados
- Si el cliente ya tiene cuotas pagadas → bloquea campos financieros (monto, cuotas, fecha, frecuencia, tasa)
- Si no tiene pagos → permite editar todo
- Muestra advertencia en rojo cuando los campos están bloqueados

**Modificación en `openAddModal()`**:
- Ahora siempre habilita todos los campos (para nuevos clientes)
- Oculta el mensaje de advertencia

**Modificación en `saveClient()`**:
- Detecta si está en modo edición CON campos bloqueados
- Si es así: solo actualiza `nombre` y `telefono`
- Si los campos están habilitados: recalcula cuotas y actualiza todo

**Modificación en `renderDetail()`**:
- Agrega botón "✏️ Editar" junto al botón de eliminar
- El botón llama a `openEditModal(clientId)`

**Se exportó `openEditModal`** como función global (window.openEditModal)

---

## 🎯 Resumen de funcionalidades nuevas:

| Cambio | Dónde | Cómo usar |
|--------|-------|-----------|
| **Rojo en vencidas** | Lista de clientes | Filas con vencidas se ven rojo automático + filtro "Con cuotas vencidas" |
| **Filtro fecha** | Toolbar de clientes | Ingresa "Desde" y "Hasta" para filtrar por antigüedad |
| **Editar cliente** | Vista de detalle | Presiona "✏️ Editar" → se abre modal con datos |

---

## 🔒 Protección de datos:

Cuando un cliente tiene **cuotas pagadas**, los campos financieros se bloquean para proteger el historial:
- ❌ No se puede cambiar monto
- ❌ No se puede cambiar número de cuotas  
- ❌ No se puede cambiar fechas
- ❌ No se puede cambiar frecuencia/tasa
- ✅ Sí se puede cambiar nombre y teléfono

Esto previene inconsistencias en el historial de pagos.

---

**Fecha de actualización**: 8 de abril de 2026
**Usuario**: Sebastián Gallo
**Estado**: ✅ Completado y verificado
