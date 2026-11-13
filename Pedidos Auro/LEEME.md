# Tarifa Pedidos — app Android

App Android con la Tarifa 1 (26/10/2026): eliges artículos y cantidades, calcula
el total con el precio tarifa y envía el listado a un chat de WhatsApp.
Funciona sin conexión; solo WhatsApp necesita internet para enviar.

## Cómo obtener la APK

### Opción A — GitHub (sin instalar nada en el ordenador)

1. Entra en https://github.com con tu cuenta (o crea una gratis).
2. Crea un repositorio nuevo, **privado**, por ejemplo `tarifa-pedidos`.
3. Sube **todo el contenido** de esta carpeta al repositorio
   ("Add file" → "Upload files", arrastrando los archivos y carpetas).
   Importante: la carpeta `.github` también tiene que subirse. Si tu
   explorador de archivos no la muestra, activa "ver archivos ocultos".
4. Abre la pestaña **Actions**. La compilación "Compilar APK" arranca sola
   y tarda unos 3-5 minutos.
5. Cuando termine (marca verde), entra en ella y descarga
   **TarifaPedidos-apk** en el apartado "Artifacts". Dentro del zip está
   `app-debug.apk`.

### Opción B — Android Studio (en tu ordenador)

1. Instala Android Studio (https://developer.android.com/studio).
2. "Open" → selecciona esta carpeta y espera a que termine de sincronizar.
3. Menú **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
4. La APK queda en `app/build/outputs/apk/debug/app-debug.apk`.

## Instalar en el móvil

1. Pasa `app-debug.apk` al móvil (cable, Drive, o envíatela por WhatsApp).
2. Ábrela y acepta "instalar aplicaciones de origen desconocido" cuando
   Android lo pida.
3. Aparecerá como **Tarifa Pedidos**.

## Tarifas, clientes e historial (versión 2)

- **Tarifas:** se eligen en el desplegable de arriba. En «Datos» se importan
  o actualizan desde Excel, sin recompilar la app.
- **Clientes:** en «Datos» se importa la base de clientes (Excel o CSV); cada
  importación sustituye a la anterior.
- **Historial:** cada pedido enviado queda guardado, con totales por cliente.
- **Precio y descripción:** el botón ✎ los cambia en la tarifa (desde el
  listado) o solo en el pedido en curso (desde el pedido).

Todo esto se guarda en el propio móvil. Si desinstalas la app o borras sus
datos, se pierde; al instalar una versión nueva encima, se conserva.

## Cambiar la tarifa que viene de fábrica

La tarifa incluida en la app (la que aparece recién instalada) está dentro de
`app/src/main/assets/index.html`. Para cambiarla, sustituye ese archivo, sube
`versionCode` en `app/build.gradle` (2 → 3…) y vuelve a compilar. La APK nueva
se instala encima de la anterior porque el proyecto lleva su propia firma
(`app/tarifa.keystore`).
