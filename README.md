# Proyecto de Automatización de Pruebas

## Descripción y Estrategia
Este proyecto implementa un pipeline de Integración y Entrega Continua (CI/CD) diseñado para asegurar la calidad de los despliegues. 
La estrategia incluye:
1. **Pruebas Automatizadas:** Uso de JUnit y Selenium mediante Maven para aislar componentes (Unitarias) y validar flujos (Integración).
2. **Acceptance Gates:** Validación de criterios de negocio antes de permitir el paso a entornos superiores.
3. **Despliegue Blue-Green:** Se utiliza para reducir el downtime al derivar el tráfico al entorno "Green" solo cuando está listo.
4. **Mecanismo de Rollback:** Configurado en el bloque `post` del Jenkinsfile. Si el entorno Green falla, el tráfico se devuelve automáticamente al entorno Blue estable.

## Instrucciones de Ejecución
1. Clonar el repositorio y posicionarse en la rama `develop`.
2. Ejecutar pruebas unitarias locales: `mvn clean test`
3. El archivo `Jenkinsfile` contiene la declaración del pipeline y está listo para ser consumido por un servidor CI/CD.