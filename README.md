# OpenShift Platform Repository Template

Repositorio plantilla para la gestión declarativa de la configuración Day-2 y de los servicios de plataforma de clústeres Red Hat OpenShift.

La plantilla está diseñada para proyectos con uno o varios clústeres, diferentes datacenters y distintos perfiles operativos. Los manifiestos se gestionan mediante Git, OpenShift CLI (`oc`) y Kustomize.

El modelo actual no requiere una plataforma GitOps. No obstante, la estructura está preparada para que los puntos de entrada desplegables puedan ser gestionados posteriormente mediante Red Hat OpenShift GitOps o Argo CD sin reorganizar los manifiestos.

## Objetivos

Este repositorio proporciona una estructura común para:

- Gestionar declarativamente la configuración Day-2 de OpenShift.
- Mantener componentes reutilizables entre proyectos y clústeres.
- Separar la configuración común de las personalizaciones específicas.
- Gestionar diferencias por versión, perfil, datacenter y clúster.
- Evitar la duplicación completa de manifiestos.
- Validar y renderizar los manifiestos antes de desplegarlos.
- Ejecutar despliegues manuales reproducibles mediante `oc` y Kustomize.
- Facilitar una futura adopción de OpenShift GitOps o Argo CD.
- Mantener trazabilidad sobre los cambios aplicados a la plataforma.

## Alcance

La plantilla puede utilizarse para gestionar los siguientes tipos de configuración.

### Configuración del clúster

- OAuth e Identity Providers.
- Ingress Controller.
- Image Registry.
- Cluster Monitoring.
- User Workload Monitoring.
- Alertmanager.
- Configuración de proxy.
- Trusted CA Bundle.
- Certificados.
- MachineConfig.
- Chrony y servidores NTP.
- Configuración de nodos.
- Auditoría.
- Red y DNS.
- Políticas de seguridad.

### Servicios de plataforma

- OpenShift Data Foundation.
- OpenShift Logging.
- Loki Operator y LokiStack.
- Compliance Operator.
- Operadores de backup.
- Kasten K10.
- VolSync.
- Cert-Manager.
- External Secrets.
- Otros operadores y servicios compartidos.

### Fuera de alcance

Este repositorio no debe contener:

- Código fuente de aplicaciones.
- Artefactos funcionales de negocio.
- Imágenes de contenedor.
- Contraseñas o credenciales en texto claro.
- Configuración funcional de productos desplegados sobre OpenShift.
- Instancias de Cloud Paks o middleware, salvo que el proyecto haya decidido expresamente integrarlas en el mismo repositorio.
- Manifiestos de Argo CD mientras el proyecto utilice despliegue manual.

Los productos o plataformas con ciclo de vida independiente, como IBM Cloud Pak for Integration o IBM Cloud Pak for Business Automation, deberían mantenerse preferentemente en repositorios separados.

## Principios de diseño

### Configuración declarativa

Toda configuración persistente de la plataforma debe estar representada mediante manifiestos declarativos y versionada en Git.

No deben realizarse cambios manuales en el clúster sin registrar posteriormente la configuración equivalente en el repositorio.

### Separación entre configuración reutilizable y composición final

La estructura distingue entre:

- **Components**: recursos y configuraciones reutilizables.
- **Variants**: modificaciones reutilizables por versión o perfil.
- **Clusters**: composición final y personalización específica de cada clúster.
- **Documentation**: procedimientos de instalación, validación y operación.
- **Scripts**: utilidades para validar, renderizar, comparar y desplegar.

### Independencia entre dimensiones

Las siguientes dimensiones deben mantenerse separadas siempre que sea posible:

- Versión del componente u operador.
- Perfil de capacidad o disponibilidad.
- Datacenter o ubicación.
- Tipo de entorno.
- Personalización específica del clúster.

Una variante de versión no debe contener nombres, dominios o parámetros exclusivos de un clúster.

Un perfil de producción no debe depender directamente de un clúster concreto.

### Punto de entrada único por clúster

Cada clúster debe disponer de una ruta desplegable que actúe como punto de entrada:

```text
clusters/<cluster-name>/
``