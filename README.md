# 🔌 Estudio de Latches

App web interactiva para estudiar **latches digitales** (SR, JK, Enable, D). Incluye simulador paso a paso, generador de cronogramas, ejercicios prácticos y teoría fundamental. Funciona completamente **offline** como PWA.

## 🧠 Conceptos cubiertos

| Latch | Compuertas | Entradas |
|-------|-----------|----------|
| SR-NOR | NOR | S (Set), R (Reset) — activas en alta |
| SR-NAND | NAND | S̅, R̅ — activas en baja |
| JK-NAND | NAND | J, K — activas en alta |
| JK-NOR | NOR | J, K — activas en alta |
| SR+Enable | NOR + AND | E (Enable), S, R |
| D (Delay) | NAND + Inversor | EN (Enable), D (Data) |

## ✨ Funcionalidades

- **📖 Teoría interactiva:** retroalimentación, circuito SR cruzado (SVG), metaestabilidad, carrera 0-0, comparativa de todos los latches, glosario.
- **📋 Tablas de verdad:** todas las tablas en una pestaña para referencia rápida.
- **🎮 Simulador paso a paso:** seleccioná entradas, aplicá, y vê Q/Q̅ actualizarse en tiempo real con historial completo.
- **📈 Generador de cronogramas:** definí secuencias de entradas y generá diagramas de tiempos en canvas.
- **✏️ Ejercicios prácticos:** 2-3 ejercicios por latch con respuesta oculta y波形 de verificación.

## 🚀 Cómo usar online

La app está publicada en GitHub Pages:

```
https://maxnik98.github.io/
```

Abrila, agregala a la pantalla de inicio (PWA) y funciona offline.

## 💻 Cómo lanzar localmente

### Requisitos

- Python 3, Node.js (cualquier versión), o cualquier servidor HTTP estático.

### Opción 1: Python (recomendado)

```bash
cd latch-app
python3 -m http.server 8000
# Abrí http://localhost:8000
```

### Opción 2: Node.js (http-server)

```bash
npm install -g http-server
cd latch-app
http-server -p 8000
# Abrí http://localhost:8000
```

### Opción 3: VS Code Live Server

1. Abrí la carpeta `latch-app` en VS Code
2. Hacé clic derecho en `index.html`
3. Seleccioná "Open with Live Server"

## 📱 Generar APK (Android)

Usar [PWABuilder](https://pwabuilder.com/) con la URL del sitio:

1. Ingresá `https://maxnik98.github.io/` en PWABuilder
2. Personalizá splash screen, iconos, etc.
3. Descargá el ZIP con el Android Package
4. Firmalo con `apksigner`:

```bash
apksigner sign --ks latches.keystore --ks-key-alias latches --ks-pass pass:latches123 \
  --v1-signing-enabled true --v2-signing-enabled true --v3-signing-enabled true \
  app-release-unsigned.apk
```

## 📁 Estructura del proyecto

```
latch-app/
├── index.html        # App completa (HTML + CSS + JS inline, ~1700 líneas)
├── sw.js             # Service Worker (cache offline, network-first para HTML)
├── manifest.json     # PWA manifest
├── icon-192.png      # Icono 192×192
├── icon-512.png      # Icono 512×512
├── README.md         # Esta guía
└── Latches/          # (carpeta local con keystore y credenciales)
```

## 🧪 Verificar ejercicios

Cada latch tiene 2-3 ejercicios. Todos los answers fueron verificados paso a paso simulando el `next()` de cada uno. Los 16 ejercicios en total dan correctos.

## 📄 Licencia

Uso educativo libre.
