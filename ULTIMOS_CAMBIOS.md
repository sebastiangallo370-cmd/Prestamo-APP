# Últimos Cambios - 8 de Abril 2026

## 🎨 Mejoras de UI/UX

### 1. **Quitar campo de Teléfono**
- ❌ Eliminado el campo de teléfono del formulario de crear/editar cliente
- ✅ Simplificado el modal para solo capturar información esencial
- Archivos afectados:
  - `index.html`: Removido input de teléfono
  - `src/js/app.js`: Removidas referencias a `f-tel` y `telefono`

### 2. **Agregar Opción 0% de Interés**
- ✅ Nueva opción "0% mensual" en el select de tasa de interés
- Permite crear préstamos sin intereses (o carítativos)
- Ubicación: Modal de nuevo cliente/editar cliente
- Archivos: `index.html`

### 3. **Avatares Más Pequeños**
- Reducción de tamaño:
  - De: `44px × 44px` → A: `32px × 32px` 
  - Fuente: `18px` → `13px`
  - Border: `2px` → `1.5px`
  - Padding de filas: `16px 20px` → `12px 16px`
  - Gap: `16px` → `12px`
- Efecto: Las filas de clientes ahora son más compactas
- Archivos: `src/css/style.css`

---

## 📝 Cambios Técnicos

| Componente | Cambio | Razón |
|-----------|--------|-------|
| `openAddModal()` | Removido `f-tel` del loop | Campo eliminado |
| `openEditModal()` | Removida asignación `f-tel` | Campo eliminado |
| `saveClient()` | Removida variable `telefono` | Campo eliminado |
| `clientData` | Removido `telefono` del objeto | No se guarda |
| `clientRowHTML()` | Removido display de teléfono | Cleaner UI |
| `renderDetail()` | "Cliente activo" en lugar de teléfono | Información relevante |
| `client-avatar` CSS | Tamaño reducido 32px | Compacto |
| `client-row` CSS | Padding/gap reducido | Menos altura |
| Select `f-tasa` | Opción `0.00` agregada | Flexibilidad |

---

## ✅ Verificación

- ✓ Sintaxis JavaScript validada
- ✓ HTML sin errores
- ✓ CSS compilable
- ✓ Todos los cambios aplicados
- ✓ Archivos guardados en workspace

---

**Estado**: Listo para usar  
**Última actualización**: 08/04/2026 22:30
