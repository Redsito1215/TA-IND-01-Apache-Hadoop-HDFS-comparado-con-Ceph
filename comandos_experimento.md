# Comandos del experimento HDFS

Este procedimiento permite levantar un clúster local compuesto por un NameNode y tres DataNodes. La prueba utiliza un archivo identificado con los datos del estudiante y un factor de replicación 3.

## 1. Mostrar los datos de la sesión

Antes de las capturas se ejecutan estos comandos para mostrar el usuario, el equipo, la fecha y la hora reales:

```powershell
whoami
hostname
Get-Date
```

## 2. Iniciar el clúster

```powershell
docker compose up -d
docker compose ps
```

## 3. Verificar los DataNodes activos

```powershell
docker exec hdfs-steven-namenode hdfs dfsadmin -report
```

El reporte debe mostrar tres DataNodes activos antes de continuar.

## 4. Crear el directorio y subir el archivo

```powershell
docker exec hdfs-steven-namenode hdfs dfs -mkdir -p /ta-ind-01
docker exec hdfs-steven-namenode hdfs dfs -put -f /evidencias/archivo_estudiante.txt /ta-ind-01/
docker exec hdfs-steven-namenode hdfs dfs -ls /ta-ind-01
```

## 5. Comprobar el factor de replicación

```powershell
docker exec hdfs-steven-namenode hdfs fsck /ta-ind-01/archivo_estudiante.txt -files -blocks -locations
```

## 6. Simular un DataNode sin respuesta

```powershell
docker pause hdfs-steven-datanode1
docker ps --filter "name=hdfs-steven" --format "table {{.Names}}\t{{.Status}}"
docker exec hdfs-steven-namenode hdfs dfs -cat /ta-ind-01/archivo_estudiante.txt
```

## 7. Recuperar el DataNode

```powershell
docker unpause hdfs-steven-datanode1
docker exec hdfs-steven-namenode hdfs fsck /ta-ind-01/archivo_estudiante.txt -files -blocks -locations
```

## Evidencias que deben obtenerse

1. Los cuatro contenedores iniciados.
2. El reporte con tres DataNodes activos.
3. El bloque del archivo almacenado con tres réplicas.
4. El primer DataNode en estado pausado.
5. La lectura correcta del archivo mientras el nodo no responde.
6. El estado final del archivo después de recuperar el nodo.
