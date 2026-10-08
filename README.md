# Ivan ADSB Radar — Releases

Binarios del firmware para las actualizaciones OTA de **Ivan ADSB Radar** (ESP32-2432S028 "CYD").

Código fuente: [Suiah98/Ivan-ADSB-Radar](https://github.com/Suiah98/Ivan-ADSB-Radar) (privado).

## Archivos

| Archivo | Contenido |
|---------|-----------|
| `firmware.bin` | Firmware actual, listo para flashear por OTA |
| `version.json` | Versión publicada, URL del binario y su MD5 |

```json
{
  "version": "1.2",
  "url": "https://raw.githubusercontent.com/Suiah98/Ivan-ADSB-Radar-releases/main/firmware.bin",
  "md5": "..."
}
```

## Cómo funciona

Las placas descargan `version.json` al arrancar y cada 6 horas. Si `version` es mayor que la que ejecutan, descargan `firmware.bin`, comprueban el MD5, instalan y se reinician. Si el firmware nuevo no consigue datos de aviones en 3 arranques, la placa vuelve a la versión anterior.

**No edites estos archivos a mano.** Se generan con `release.ps1` desde el repo del proyecto.

## Flashear a mano

```bash
pio run -e cyd -t upload --upload-port COM3
```

o con esptool, usando `firmware.bin` en la dirección `0x10000` (sobre una placa que ya tenga bootloader y tabla de particiones).
