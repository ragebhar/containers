---

copyright:
  years: 2014, 2018
lastupdated: "2018-02-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Integración de servicios
{: #integrations}

Puede utilizar diversos servicios externos y servicios del catálogo de {{site.data.keyword.Bluemix_notm}} con un clúster estándar en {{site.data.keyword.containershort_notm}}.
{:shortdesc}

<table summary="Resumen de las características de accesibilidad">
<caption>Tabla. Opciones de integración para clústeres y apps en Kubernetes</caption>
<thead>
<tr>
<th>Servicio</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr>
<td>Aqua Security</td>
  <td>Como suplemento a <a href="/docs/services/va/va_index.html" target="_blank">Vulnerability Advisor</a>, puede utilizar <a href="https://www.aquasec.com/" target="_blank">Aqua Security <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> para mejorar la seguridad de los despliegues de contenedores reduciendo las acciones que su app puede realizar. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/06/protecting-container-deployments-bluemix-aqua-security/" target="_blank">Protección de despliegues de contenedores con {{site.data.keyword.Bluemix_notm}} Aqua Security <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Blockchain</td>
<td>Despliegue un entorno de desarrollo disponible a nivel público para IBM Blockchain en un clúster de Kubernetes en {{site.data.keyword.containerlong_notm}}. Utilice este entorno para desarrollar y personalizar su propia red de encadenamiento de bloques (blockchain) para desplegar apps que comparten un libro mayor inalterable para registrar el historial de las transacciones. Para obtener más información, consulte <a href="https://ibm-blockchain.github.io" target="_blank">Desarrollo en una plataforma
IBM Blockchain de recinto de pruebas de nube <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>{{site.data.keyword.cloudcerts_short}}</td>
<td>Puede utilizar <a href="../services/certificate-manager/index.html" target="_blank">{{site.data.keyword.cloudcerts_long}} <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> para almacenar y gestionar certificados SSL para sus apps. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2018/01/use-ibm-cloud-certificate-manager-ibm-cloud-container-service-deploy-custom-domain-tls-certificates/" target="_blank">Uso de {{site.data.keyword.cloudcerts_long_notm}} con {{site.data.keyword.containershort_notm}} para desplegar certificados TLS de dominio personalizados <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Codeship</td>
<td>Puede utilizar <a href="https://codeship.com" target="_blank">Codeship <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> para la integración y entrega continua de contenedores. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/10/using-codeship-pro-deploy-workloads-ibm-container-service/" target="_blank">Utilización de Codeship Pro para desplegar cargas de trabajo en {{site.data.keyword.containershort_notm}} <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>{{site.data.keyword.contdelivery_short}}</td>
<td>Automatice las compilaciones de las apps y los despliegues de los contenedores en clústeres de Kubernetes
utilizando a cadena de herramientas. Para obtener información sobre la configuración, consulte el blog sobre <a href="https://developer.ibm.com/recipes/tutorials/deploy-kubernetes-pods-to-the-bluemix-container-service-using-devops-pipelines/" target="_blank">Despliegue de pods de Kubernetes en {{site.data.keyword.containerlong_notm}} mediante conductos DevOps <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>CoScale</td>
<td>Supervise los nodos trabajadores, contenedores, conjuntos de réplicas, controladores de réplicas y servicios con <a href="https://www.coscale.com/" target="_blank">CoScale <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/06/monitoring-ibm-bluemix-container-service-coscale/" target="_blank">Supervisión de {{site.data.keyword.containershort_notm}} con CoScale <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Datadog</td>
<td>Supervise el clúster y visualice las métricas de rendimiento de las aplicaciones y la infraestructura con <a href="https://www.datadoghq.com/" target="_blank">Datadog <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/07/monitoring-ibm-bluemix-container-service-datadog/" target="_blank">Supervisión de {{site.data.keyword.containershort_notm}} con Datadog <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Helm</td>
<td> <a href="https://helm.sh/" target="_blank">Helm <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> es un gestor de paquetes de Kubernetes. Puede crear Helm Charts para definir, instalar y actualizar aplicaciones Kubernetes complejas que se ejecuten en clústeres de {{site.data.keyword.containerlong_notm}}. Obtenga más información sobre cómo <a href="https://developer.ibm.com/recipes/tutorials/increase-deployment-velocity-with-kubernetes-helm-charts/" target="_blank">aumentar la velocidad del despliegue con Kubernetes Helm Charts <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Instana</td>
<td> <a href="https://www.instana.com/" target="_blank">Instana <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> proporciona la infraestructura y la supervisión de rendimiento de app con una GUI que detecta y correlaciona automáticamente las apps. Instana captura las solicitudes de las apps, permitiéndole resolver problemas y realizar el análisis de la causa raíz para evitar que se repitan los problemas. Consulte la publicación sobre <a href="https://www.instana.com/blog/precise-visibility-applications-ibm-bluemix-container-service/" target="_blank">despliegue de Instana en {{site.data.keyword.containershort_notm}} <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> para obtener más información.</td>
</tr>
<tr>
<td>Istio</td>
<td><a href="https://www.ibm.com/cloud/info/istio" target="_blank">Istio<img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> es un servicio de código fuente abierto que ofrece a los desarrolladores una forma de conectarse, proteger, gestionar y supervisar una red de microservicios, también conocida como malla de servicios, en plataformas de orquestación de nube como Kubernetes. Consulte la publicación sobre <a href="https://developer.ibm.com/dwblog/2017/istio/" target="_blank">cómo IBM cofundó y lanzó Istio<img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> para obtener más información sobre el proyecto de código abierto. Para instalar Istio en el clúster de Kubernetes en {{site.data.keyword.containershort_notm}} y empezar con una app de muestra, consulte la [Guía de aprendizaje: Gestión de microservicios con Istio](cs_tutorials_istio.html#istio_tutorial).</td>
</tr>
<tr>
<td>NeuVector</td>
<td>Proteja los contenedores con un cortafuegos nativo en la nube utilizando <a href="https://neuvector.com/" target="_blank">NeuVector <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. Para obtener más información, consulte <a href="https://www.ibm.com/us-en/marketplace/neuvector-container-security" target="_blank">NeuVector Container Security <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Prometheus</td>
<td>Prometheus es una herramienta de supervisión, registro y generación de alertas de código abierto específicamente diseñada para Kubernetes para recuperar información detallada acerca del clúster, los nodos trabajadores y el estado de despliegue basado en la información de registro de Kubernetes. Se recopila información sobre CPU, memoria, E/S y actividad de red
de todos los contenedores en ejecución de un clúster, que se puede utilizar en consultas personalizadas o en alertas para supervisar el rendimiento y las cargas de trabajo del clúster.

<p>Para utilizar Prometheus, siga las <a href="https://github.com/coreos/prometheus-operator/tree/master/contrib/kube-prometheus" target="_blank">instrucciones de CoreOS <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>.</p>
</td>
</tr>
<tr>
<td>{{site.data.keyword.bpshort}}</td>
<td>{{site.data.keyword.bplong}} es una herramienta de automatización que utiliza Terraform para desplegar la infraestructura como código. Al desplegar su infraestructura como una única unidad, puede reutilizar esas definiciones de recursos en la nube en cualquier número de entornos. Para definir un clúster de Kubernetes como un recurso con {{site.data.keyword.bpshort}}, intente crear un entorno con la [plantilla de contenedor-clúster](https://console.bluemix.net/schematics/templates/details/Cloud-Schematics%2Fcontainer-cluster). Para obtener más información sobre Schematics, consulte [Acerca de {{site.data.keyword.bplong_notm}}](/docs/services/schematics/schematics_overview.html#about).</td>
</tr>
<tr>
<td>Sematext</td>
<td>Visualice métricas y registros para sus aplicaciones contenerizadas utilizando <a href="https://sematext.com/" target="_blank">Sematext <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/09/monitoring-logging-ibm-bluemix-container-service-sematext/" target="_blank">Supervisión y registro de contenedores con Sematext <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Sysdig</td>
<td>Capture métricas de host, statsd, contenedor y app con un único punto de instrumentación utilizando <a href="https://sysdig.com/" target="_blank">Sysdig <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/08/monitoring-ibm-bluemix-container-service-sysdig-container-intelligence/" target="_blank">Supervisión de {{site.data.keyword.containershort_notm}} con Sysdig Container Intelligence <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Twistlock</td>
<td>Como suplemento a <a href="/docs/services/va/va_index.html" target="_blank">Vulnerability Advisor</a>, puede utilizar <a href="https://www.twistlock.com/" target="_blank">Twistlock <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> para gestionar cortafuegos, la protección ante amenazas y la respuesta a incidentes. Para obtener más información, consulte <a href="https://www.ibm.com/blogs/bluemix/2017/07/twistlock-ibm-bluemix-container-service/" target="_blank">Twistlock en {{site.data.keyword.containershort_notm}} <img src="../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>. </td>
</tr>
<tr>
<td>Weave Scope</td>
<td>Weave Scope proporciona un diagrama visual de los recursos de un clúster de Kubernetes, incluidos servicios, pods, contenedores, procesos, nodos, etc. Weave Scope ofrece métricas interactivas correspondientes a CPU y memoria y también herramientas para realizar seguimientos y ejecuciones en un contenedor.<p>Para obtener más información, consulte [Visualización de recursos de clúster de Kubernetes con Weave Scope y {{site.data.keyword.containershort_notm}}](cs_integrations.html#weavescope).</p></li></ol>
</td>
</tr>
</tbody>
</table>

<br />



## Adición de servicios clústeres
{: #adding_cluster}

Añada una instancia de servicio de {{site.data.keyword.Bluemix_notm}} existente a un clúster para permitir a los usuarios del clúster acceder y utilizar el servicio de {{site.data.keyword.Bluemix_notm}} cuando desplieguen una app en el clúster.
{:shortdesc}

Antes de empezar:

1. Defina su clúster como [destino de la CLI](cs_cli_install.html#cs_cli_configure).
2. [Solicite una instancia del servicio {{site.data.keyword.Bluemix_notm}}](/docs/apps/reqnsi.html#req_instance).
   **Nota:** Para crear una instancia de un servicio en la ubicación de Washington DC, debe utilizar la CLI.

**Nota:**
<ul><ul>
<li>Sólo puede añadir servicios de {{site.data.keyword.Bluemix_notm}} que den soporte a claves de servicio. Si el servicio no soporta a las claves del servicio, consulte [Habilitación de apps externas para utilizar servicios de {{site.data.keyword.Bluemix_notm}}](/docs/apps/reqnsi.html#accser_external).</li>
<li>El clúster y los nodos trabajadores deben desplegarse por completo para poder añadir un servicio.</li>
</ul></ul>


Para añadir un servicio:
2.  Lista de servicios disponibles {{site.data.keyword.Bluemix_notm}}.

    ```
    bx service list
    ```
    {: pre}

    Ejemplo de salida de CLI:

    ```
    name                      service           plan    bound apps   last operation
    <service_instance_name>   <service_name>    spark                create succeeded
    ```
    {: screen}

3.  Anote el **nombre** de la instancia de servicio que desea añadir al clúster.
4.  Identifique el espacio de nombres del clúster que desea utilizar para añadir el servicio. Puede elegir entre las siguientes opciones.
    -   Obtenga una lista de los espacios de nombres existentes y elija el espacio de nombres que desea utilizar.

        ```
        kubectl get namespaces
        ```
        {: pre}

    -   Cree un espacio de nombres nuevo en el clúster.

        ```
        kubectl create namespace <namespace_name>
        ```
        {: pre}

5.  Añada el servicio al clúster.

    ```
    bx cs cluster-service-bind <cluster_name_or_id> <namespace> <service_instance_name>
    ```
    {: pre}

    Cuando el servicio se haya añadido correctamente al clúster, se crea un secreto de clúster que contiene las credenciales de la instancia de servicio. Ejemplo de salida de CLI:

    ```
    bx cs cluster-service-bind mycluster mynamespace cleardb
    Binding service instance to namespace...
    OK
    Namespace: mynamespace
    Secret name:     binding-<service_instance_name>
    ```
    {: screen}

6.  Verifique que el secreto se ha creado en el espacio de nombres del clúster.

    ```
    kubectl get secrets --namespace=<namespace>
    ```
    {: pre}


Para utilizar el servicio en un pod desplegado en el clúster, los usuarios del clúster pueden acceder a las credenciales de servicio del servicio de {{site.data.keyword.Bluemix_notm}} mediante el [montaje del secreto de Kubernetes como volumen secreto en un pod](cs_integrations.html#adding_app).

<br />



## Adición de servicios a apps
{: #adding_app}

Se utilizan secretos cifrados de Kubernetes para almacenar detalles de servicios y credenciales de {{site.data.keyword.Bluemix_notm}} y permitir una comunicación segura entre el servicio y el clúster. Como usuario del clúster, puede acceder a este secreto montándolo como un volumen en un pod.
{:shortdesc}

Antes de empezar, seleccione su clúster como [destino de la CLI](cs_cli_install.html#cs_cli_configure). Asegúrese de que el administrador del clúster ha [añadido al clúster](cs_integrations.html#adding_cluster) el servicio de {{site.data.keyword.Bluemix_notm}} que desea utilizar en su app.

Los secretos de Kubernetes constituyen una forma segura de almacenar información confidencial, como nombres de usuario, contraseñas o claves. En lugar de exponer la información confidencial a través de variables de entorno o directamente en Dockerfile, los secretos se deben montar como un volumen secreto en un pod para que resulten accesibles para un contenedor en ejecución en un pod.

Cuando monta un volumen secreto en un pod, se almacena un archivo denominado binding en el directorio de montaje del volumen, que incluye toda la información y las credenciales que necesita para acceder al servicio de {{site.data.keyword.Bluemix_notm}}.

1.  Obtenga una lista de los secretos disponibles en el espacio de nombres del clúster.

    ```
    kubectl get secrets --namespace=<my_namespace>
    ```
    {: pre}

    Salida de ejemplo:

    ```
    NAME                                    TYPE                                  DATA      AGE
    binding-<service_instance_name>         Opaque                                1         3m

    ```
    {: screen}

2.  Busque un secreto de tipo **opaco** y tome nota del **nombre** del secreto. Si existen varios secretos, póngase en contacto con el administrador del clúster para identificar el secreto correcto del servicio.

3.  Abra el editor de texto que desee.

4.  Cree un archivo YAML para configurar un pod que pueda acceder a los detalles del servicio a través de un volumen secreto. Si enlaza más de un servicio, verifique que cada secreto esté asociado al servicio correcto.

    ```
    apiVersion: extensions/v1beta1
    kind: Deployment
    metadata:
      labels:
        app: secret-test
      name: secret-test
      namespace: <my_namespace>
    spec:
      selector:
        matchLabels:
          app: secret-test
      replicas: 1
      template:
        metadata:
          labels:
            app: secret-test
        spec:
          containers:
          - image: nginx
            name: secret-test
            volumeMounts:
            - mountPath: /opt/service-bind
              name: service-bind-volume
          volumes:
          - name: service-bind-volume
            secret:
              defaultMode: 420
              secretName: binding-<service_instance_name>
    ```
    {: codeblock}

    <table>
    <thead>
    <th colspan=2><img src="images/idea.png" alt="Icono Idea"/> Visión general de los componentes del archivo YAML</th>
    </thead>
    <tbody>
    <tr>
    <td><code>volumeMounts/mountPath</code></td>
    <td>El nombre del volumen secreto que desea montar en el contenedor.</td>
    </tr>
    <tr>
    <td><code>volumes/name</code></td>
    <td>Especifique un nombre para el volumen secreto que desea montar en el contenedor de montaje.</td>
    </tr>
    <tr>
    <td><code>secret/defaultMode</code></td>
    <td>Establezca permisos de solo lectura para el secreto del servicio.</td>
    </tr>
    <tr>
    <td><code>secret/secretName</code></td>
    <td>Escriba el nombre del secreto que ha anotado anteriormente.</td>
    </tr></tbody></table>

5.  Cree el pod y monte el volumen secreto.

    ```
    kubectl apply -f <yaml_path>
    ```
    {: pre}

6.  Verifique que se ha creado el pod.

    ```
    kubectl get pods --namespace=<my_namespace>
    ```
    {: pre}

    Ejemplo de salida de CLI:

    ```
    NAME                           READY     STATUS    RESTARTS   AGE
    secret-test-1111454598-gfx32   1/1       Running   0          1m
    ```
    {: screen}

7.  Anote el **NOMBRE** de su pod.
8.  Obtenga los detalles del pod y busque el nombre del secreto.

    ```
    kubectl describe pod <pod_name>
    ```
    {: pre}

    Salida:

    ```
    ...
    Volumes:
      service-bind-volume:
        Type:       Secret (a volume populated by a Secret)
        SecretName: binding-<service_instance_name>
    ...
    ```
    {: screen}

    

9.  Cuando implemente la app, configúrela de modo que encuentre el archivo secreto denominado **binding** en el directorio de montaje, analice el contenido JSON y determine el URL y las credenciales del servicio para acceder al servicio de {{site.data.keyword.Bluemix_notm}}.

Ahora puede acceder a los detalles y credenciales del servicio de {{site.data.keyword.Bluemix_notm}}. Para poder trabajar con el servicio de {{site.data.keyword.Bluemix_notm}}, asegúrese de que la app se haya configurado de modo que busque el archivo secreto del servicio en el directorio de montaje, analice el contenido JSON y determine los detalles del servicio.

<br />



## Visualización de recursos de un clúster de Kubernetes
{: #weavescope}

Weave Scope proporciona un diagrama visual de los recursos de un clúster de Kubernetes, incluidos servicios, pods, contenedores, procesos, nodos, etc. Weave Scope ofrece métricas interactivas correspondientes a CPU y memoria y también herramientas para realizar seguimientos y ejecuciones en un contenedor.
{:shortdesc}

Antes de empezar:

-   Recuerde no exponer la información del clúster en Internet público. Siga estos pasos para desplegar de forma segura Weave Scope y para acceder al mismo localmente desde un navegador web.
-   Si aún no tiene uno, [cree un clúster estándar](cs_clusters.html#clusters_ui). Weave Scope puede consumir mucha CPU, especialmente la app. Ejecute Weave Scope con clústeres de pago grandes, no con clústeres gratuitos.
-   [Defina su clúster como destino de la CLI](cs_cli_install.html#cs_cli_configure) para ejecutar mandatos `kubectl`.


Para utilizar Weave Scope con una clúster:
2.  Despliegue una de los archivos de configuración de permisos RBAC del clúster.

    Para habilitar los permisos de lectura/escritura:

    ```
    kubectl apply -f "https://raw.githubusercontent.com/IBM-Cloud/kube-samples/master/weave-scope/weave-scope-rbac.yaml"
    ```
    {: pre}

    Para habilitar los permisos de solo lectura:

    ```
    kubectl apply --namespace weave -f "https://raw.githubusercontent.com/IBM-Cloud/kube-samples/master/weave-scope/weave-scope-rbac-readonly.yaml"
    ```
    {: pre}

    Salida:

    ```
    clusterrole "weave-scope-mgr" created
    clusterrolebinding "weave-scope-mgr-role-binding" created
    ```
    {: screen}

3.  Despliegue el servicio Weave Acope, al que puede acceder de forma privada con la dirección IP del clúster.

    <pre class="pre">
    <code>kubectl apply --namespace weave -f "https://cloud.weave.works/k8s/scope.yaml?k8s-version=$(kubectl version | base64 | tr -d '&bsol;n')"</code>
    </pre>

    Salida:

    ```
    serviceaccount "weave-scope" created
    deployment "weave-scope-app" created
    service "weave-scope-app" created
    daemonset "weave-scope-agent" created
    ```
    {: screen}

4.  Ejecute un mandato de reenvío de puerto para que aparezca el servicio en el sistema. Ahora que Weave Scope se ha configurado con el clúster, para acceder a él la próxima vez puede ejecutar este mandato de reenvío de puerto sin realizar de nuevo los pasos de configuración anteriores.

    ```
    kubectl port-forward -n weave "$(kubectl get -n weave pod --selector=weave-scope-component=app -o jsonpath='{.items..metadata.name}')" 4040
    ```
    {: pre}

    Salida:

    ```
    Forwarding from 127.0.0.1:4040 -> 4040
    Forwarding from [::1]:4040 -> 4040
    Handling connection for 4040
    ```
    {: screen}

5.  Abra el navegador web en `http://localhost:4040`. Sin los componentes predeterminados desplegados, verá el siguiente diagrama. Seleccione la vista de diagramas o tablas de topología de los recursos de Kubernetes en el clúster.

     <img src="images/weave_scope.png" alt="Ejemplo de topología de Weave Scope" style="width:357px;" />


[Más información sobre las características de Weave Scope ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.weave.works/docs/scope/latest/features/).

<br />

