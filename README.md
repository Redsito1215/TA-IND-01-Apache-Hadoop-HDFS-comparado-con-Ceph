# TA-IND-01 Análisis crítico de Apache Hadoop HDFS

Informe académico individual sobre la arquitectura distribuida de Apache Hadoop HDFS y su comparación con Ceph.

- **Estudiante:** Steven Fernando Pozo Castillo
- **Curso:** 7.º semestre, paralelo B
- **Usuario de GitHub:** Redsito1215

## Descripción

El experimento utiliza un NameNode y tres DataNodes en Docker para observar la replicación de un bloque y la lectura de un archivo cuando uno de los nodos deja de responder. El informe relaciona los resultados con transparencia, CAP/PACELC, modelos de comunicación y tolerancia a fallos, y contrasta el diseño de HDFS con Ceph.

## Contenido del repositorio

- `docker-compose.yml`: clúster local de HDFS.
- `hadoop.env`: configuración de replicación y comunicación.
- `comandos_experimento.md`: procedimiento reproducible.
- `evidencias/`: archivo de prueba y resultados.
- `figuras/`: capturas y diagramas.
- `informe/`: fuente LaTeX y bibliografía.

## Compilación del informe

- **Compilador:** pdfLaTeX con Biber.
- **Archivo principal:** `informe/main.tex`.
- **Dependencias:** distribución TeX Live o MiKTeX con `pdflatex`, `biber`, `biblatex`, `babel`, `newtx`, `geometry`, `graphicx`, `booktabs`, `array`, `xcolor`, `tikz`, `hyperref`, `xurl` y `csquotes`.

Desde la carpeta `informe`, ejecutar en este orden:

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

El resultado se genera como `informe/main.pdf`.

## Video de sustentación

El enlace público del video se incorporará aquí antes de la entrega.

