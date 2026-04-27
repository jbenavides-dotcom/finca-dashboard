# Centro de Control · Finca La Palma y el Tucán

Dashboard general que centraliza el acceso a todos los tableros operativos de la finca, con monitoreo automático 24/7.

**Live (cuando se publique):** https://jbenavides-dotcom.github.io/finca-dashboard/
**Repo:** jbenavides-dotcom/finca-dashboard
**Pedido por:** Felipe Sardi — 2026-04-27

---

## Dashboards integrados

| # | Dashboard | URL | Estado |
|---|-----------|-----|--------|
| 1 | 🌱 Huerto Inteligente (Ecowitt) | https://jbenavides-dotcom.github.io/huerto-dashboard/ | ✅ Operativo |
| 2 | 🧪 Laboratorio Fermentación | local hoy → publicar como `dashboard-fermentacion` | ⏳ Pendiente publicar |
| 3 | ✅ Actividades Equipo Huerta | https://huerta-lpet-dashboard-ajwgtqv2pv4nux5letsibx.streamlit.app/ | ✅ Operativo |
| 4 | 🐓 Inventario Animal | https://jbenavides-dotcom.github.io/inventario-animales/ | ✅ Operativo |

> Más dashboards (analítica, inventario/trazabilidad, clima, etc.) se irán añadiendo a medida que existan. Para sumarlos basta con agregar un objeto al array `DASHBOARDS` en `index.html`.

---

## Cómo añadir un dashboard nuevo

Editar `index.html` y agregar un objeto al array `DASHBOARDS`:

```js
{
  id: 'nuevo',
  icon: '🆕',
  title: 'Nombre del dashboard',
  desc: 'Una línea de descripción.',
  url: 'https://...',
  css: 'huerto',                  // reusar accent o crear nueva clase
  metrics: [
    { label: 'KPI 1', value: 'X' },
    { label: 'KPI 2', value: 'Y' }
  ],
  check: 'fetch'                  // 'fetch' | 'local' | 'soon'
}
```

---

## Stack

- HTML5 + CSS3 + JS vanilla, sin build step.
- Fonts: Baskervville (serif) + Jost (sans).
- Paleta LP&ET: gold #CB9F5B · pink #ED728B · dark #2C2D2E · light #FCF7EC.
- Healthcheck heurístico vía favicon-image probe (esquiva CORS).
- Auto-refresh cada 60 s.
- Mobile-first.

## Monitoreo 24/7

Un cron en el cerebro hace ping HEAD a todos los dashboards cada hora y registra en `healthcheck.log`. Si alguno cae, se notifica.

## Mantenimiento (responsabilidad permanente)

- Verificar que cada dashboard del array siga online.
- Actualizar URLs cuando cambien.
- Añadir nuevos dashboards al array.
- Mantener este README sincronizado en cada cambio.
