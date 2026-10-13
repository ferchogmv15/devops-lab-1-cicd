# Lab 01: CI/CD con GitHub Actions y Amazon ECS

# Presentado por: Edgar Fernando Vega Morales

## 1. Enlace al repositorio de GitHub compartido con el docente.

[Link a Repositorio en GitHub](https://github.com/ferchogmv15/devops-lab-1-cicd) 

## 2.1 Explicación de la arquitectura de contenedores y los conceptos de CI/CD aplicados al laboratorio.

### Arquitectura del proyecto

El laboratorio tiene como base un proyecto backEnd en python alojado en GitHub, que se implementa con un workflow automatizado que valida buenas prácticas en el código fuente, hace test automatizados, construir una imagen Docker de la aplicación y de sus dependencias, dicha imagen se publica en Amazon Elastic Container Registry (ECR) para finalmente despliegar la aplicación en una IP publica mediante Amazon Elastic Container Service (ECS). 

### Conceptos de CI/CD aplicados: 
**Integración continua (CI):** la cual ejecuta comprobaciones automatizadas cuando se incorporan cambios al repositorio. El objetivo es detectar errores pronto y reducir el riesgo de integrar código defectuoso.

**Entrega continua y despliegue continuo (CD):** estos dos procesos automatizan la entrega al servidor y el despliegue sobre este de los cambios que pasen los controles de calidad establecidos


## 2.2 Ejecución del pipeline deploy todos los jobs ejecutados correctamente
![image.png](https://raw.githubusercontent.com/ferchogmv15/devops-lab-1-cicd/main/assests/ejecucion_deploy.png)

## Verificación del repositorio con la imagen vinculada

![image.png](https://raw.githubusercontent.com/ferchogmv15/devops-lab-1-cicd/main/assests/verificacion_repositorio.png)

## Verificación cluster-ferchogmv15 -> service-greeting-ferchogmv15

estado Activo y 1 tarea en ejecución

![image.png](https://raw.githubusercontent.com/ferchogmv15/devops-lab-1-cicd/main/assests/verificacion_cluster.png)

## Evidencia ejecución workflow Cleanup Student Infrastructure

![image.png](https://raw.githubusercontent.com/ferchogmv15/devops-lab-1-cicd/main/assests/ejecucion_destroy.png)

ya no existe repositorio en nuestra consola de AWS

![image.png](https://raw.githubusercontent.com/ferchogmv15/devops-lab-1-cicd/main/assests/verificacion_destroy.png)

## 2.3 Evidencia visual de la petición HTTP a la IP pública de la instancia EC2 con navegador.

![image.png](https://raw.githubusercontent.com/ferchogmv15/devops-lab-1-cicd/main/assests/evidencia_peticion.png)

## 2.4 Propuestas para mejorar el pipeline

*	Etiquetar las imágenes con el SHA1 del commit, esta estrategia permite mejorar la trazabilidad de las imágenes y ayuda a identificar versiones estables de la aplicación.
*	Verificar la API de Health posterior al despliegue de la aplicación, así se comprueba automáticamente que el despliegue no tuvo inconvenientes y es estable.
*	Agregar reporte de las pruebas automaticas lo cual facilitaría la trazabilidad.
*	En el workflow de destroy seria bueno que la validación del suffix sea automática y no dependa del usuario, esto para evitar malos entendidos o errores.
