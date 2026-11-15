# Bitácora de trabajo

## 14 de noviembre de 2026

- **Actividad:** elección de Apache Hadoop HDFS como sistema principal y Ceph como sistema de comparación; preparación del clúster con Docker; ejecución de la prueba de replicación; redacción del informe; revisión de fuentes y organización de anexos.
- **Problema encontrado:** al inicio no estaba claro qué aspecto de HDFS podía comprobarse en un equipo local. Durante la lectura con un DataNode pausado, el cliente esperó a que venciera el tiempo de conexión antes de cambiar de réplica.
- **Solución:** se enfocó el experimento en un archivo con factor de replicación tres. Se configuró un tiempo de espera, se conservó la salida del cambio hacia otra réplica y se comprobó el estado final mediante `fsck`.
- **Tiempo dedicado:** 8 horas.
- **Resultado:** clúster reproducible, experimento documentado, informe comparativo redactado y evidencias visuales incorporadas.

