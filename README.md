# Manual de sincronización horaria en servidores

## Motivación

Debido a la distribución de los servidores utilizados (tanto en zonas, como en plataforma como AWS o Google Cloud), se hace uso de un script en bash para poder sincronizar todos con la misma hora.

## Configuración en servidor

Una vez dentro de la consola del servidor, se debe proceder a descargar el script relatado.
Primero nos ubicamos en la carpeta /opt:

```
cd /opt
```

Se puede descargar el mismo con:

```
wget https://raw.githubusercontent.com/fnaquira/bash-sync-date/master/sync.sh
```

Luego debemos otorgar permisos de ejecución a dicho archivo:

```
chmod +x /opt/sync.sh
```

Finalmente, lo configuraremos como una tarea programada a ejecutar cada día a la una de la mañana:

```
crontab -e
```

La regla a añadir es:

```
0 1 * * * /opt/sync.sh
```

Para asegurar que el archivo vaya a funcionar, debe estar instalada la herramienta ntpdate:

```
sudo apt-get install ntpdate
```
