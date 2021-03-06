---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 日志记录和监视集群
{: #health}

在 {{site.data.keyword.containerlong}} 中设置日志记录和监视可帮助您对问题进行故障诊断，并提高 Kubernetes 集群和应用程序的运行状况和性能。
{: shortdesc}


## 配置日志转发
{: #logging}

通过 {{site.data.keyword.containershort_notm}} 中的标准 Kubernetes 集群，可以将来自不同源的日志转发到 {{site.data.keyword.loganalysislong_notm}} 和/或外部 syslog 服务器。
{: shortdesc}

如果要将来自一个源的日志同时转发到这两个收集器服务器，那么必须创建两个日志记录配置。
{: tip}

查看下表以获取有关不同日志源的信息。

<table><caption>日志源特征</caption>
  <thead>
    <tr>
      <th>日志源</th>
      <th>特征</th>
      <th>日志路径</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>container</code></td>
      <td>在 Kubernetes 集群中运行的容器的日志。</td>
      <td>记录到容器中 STDOUT 或 STDERR 的任何内容。</td>
    </tr>
    <tr>
      <td><code>application</code></td>
      <td>在 Kubernetes 集群中运行的自己应用程序的日志。</td>
      <td>可以设置路径。</td>
    </tr>
    <tr>
      <td><code>worker</code></td>
      <td>Kubernetes 集群中虚拟机工作程序节点的日志。</td>
      <td><code>/var/log/syslog</code>、<code>/var/log/auth.log</code></td>
    </tr>
    <tr>
      <td><code>Kubernetes</code></td>
      <td>Kubernetes 系统组件的日志。</td>
      <td><code>/var/log/syslog</code>、<code>/var/log/auth.log</code></td>
    </tr>
    <tr>
      <td><code>ingress</code></td>
      <td>用于管理进入集群的网络流量的 Ingress 应用程序负载均衡器的日志。</td>
      <td><code>/var/log/alb/ids/&ast;.log</code>、<code>/var/log/alb/ids/&ast;.err</code>、<code>/var/log/alb/customerlogs/&ast;.log</code>、<code>/var/log/alb/customerlogs/&ast;.err</code></td>
    </tr>
  </tbody>
</table>

通过 UI 配置日志记录时，必须指定组织和空间。如果要在帐户级别启用日志记录，可以通过 CLI 执行此操作。
{: tip}


### 开始之前

1. 验证许可权。如果在创建集群或日志记录配置时指定了空间，那么帐户所有者和 {{site.data.keyword.containershort_notm}} 密钥所有者需要该空间的“管理员”、“开发者”或“审计员”许可权。
  * 如果您不知道谁是 {{site.data.keyword.containershort_notm}} 密钥所有者，请运行以下命令。
      ```
      bx cs api-key-info <cluster_name>
      ```
      {: pre}
  * 要立即应用您对许可权所做的任何更改，请运行以下命令。
      ```
      bx cs logging-config-refresh <cluster_name>
      ```
      {: pre}

  有关更改 {{site.data.keyword.containershort_notm}} 访问策略和许可权的更多信息，请参阅[管理集群访问权](cs_users.html#managing)。
  {: tip}

2. [设定 CLI 的目标](cs_cli_install.html#cs_cli_configure)为日志源所在的集群。

  如果使用的是 Dedicated 帐户，那么必须登录到公共 {{site.data.keyword.cloud_notm}} 端点并将公共组织和空间设定为目标，才能启用日志转发。
  {: tip}

3. 要将日志转发到 syslog，请通过以下两种方式之一来设置接受 syslog 协议的服务器：
  * 设置和管理自己的服务器，或者让提供者为您管理服务器。如果提供者为您管理服务器，请从日志记录提供者获取日志记录端点。
  * 从容器运行 syslog。例如，可以使用此[部署 .yaml 文件 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://github.com/IBM-Cloud/kube-samples/blob/master/deploy-apps-clusters/deploy-syslog-from-kube.yaml) 来访存在 Kubernetes 集群中运行容器的 Docker 公共映像。该映像在公共集群 IP 地址上发布端口 `514`，并使用此公共集群 IP 地址来配置 syslog 主机。

### 启用日志转发

1. 创建日志转发配置。
    * 将日志转发到 {{site.data.keyword.loganalysisshort_notm}}：
      ```
      bx cs logging-config-create <my_cluster> --logsource <my_log_source> --namespace <kubernetes_namespace> --hostname <ingestion_URL> --port <ingestion_port> --space <cluster_space> --org <cluster_org> --type ibm --app-containers <containers> --app-paths <paths_to_logs>
      ```
      {: pre}

      ```
      $ cs logging-config-create zac2 --logsource application --app-paths '/var/log/apps.log' --app-containers 'zac1,zac2,zac3'
      Creating logging configuration for application logs in cluster zac2...
      OK
      Id                                     Source        Namespace   Host                                    Port    Org   Space   Protocol   Application Containers   Paths
      aa2b415e-3158-48c9-94cf-f8b298a5ae39   application   -           ingest.logging.stage1.ng.bluemix.net✣   9091✣   -     -       ibm        zac1,zac2,zac3           /var/log/apps.log
      ```
      {: screen}

    * 将日志转发到 syslog：
      ```
      bx cs logging-config-create <my_cluster> --logsource <my_log_source> --namespace <kubernetes_namespace> --hostname <log_server_hostname_or_IP> --port <log_server_port> --type syslog --app-containers <containers> --app-paths <paths_to_logs>
      ```
      {: pre}

  <table>
    <caption>了解此命令的组成部分</caption>
  <thead>
    <th colspan=2><img src="images/idea.png" alt="“构想”图标"/> 了解此命令的组成部分</th>
  </thead>
  <tbody>
    <tr>
      <td><code><em>&lt;my_cluster&gt;</em></code></td>
      <td>集群的名称或标识。</td>
    </tr>
    <tr>
      <td><code><em>&lt;my_log_source&gt;</em></code></td>
      <td>要从中转发日志的源。接受的值为 <code>container</code>、<code>application</code>、<code>worker</code>、<code>kubernetes</code> 和 <code>ingress</code>。</td>
    </tr>
    <tr>
      <td><code><em>&lt;kubernetes_namespace&gt;</em></code></td>
      <td>可选：要从中转发日志的 Kubernetes 名称空间。<code>ibm-system</code> 和 <code>kube-system</code> Kubernetes 名称空间不支持日志转发。此值仅对 <code>container</code> 日志源有效。如果未指定名称空间，那么集群中的所有名称空间都将使用此配置。</td>
    </tr>
    <tr>
      <td><code><em>&lt;ingestion_URL&gt;</em></code></td>
      <td><p>对于 {{site.data.keyword.loganalysisshort_notm}}，请使用[数据获取 URL](/docs/services/CloudLogAnalysis/log_ingestion.html#log_ingestion_urls)。如果未指定数据获取 URL，那么将使用在其中创建集群的区域的端点。</p>
      <p>对于 syslog，请指定日志收集器服务的主机名和 IP 地址。</p></td>
    </tr>
    <tr>
      <td><code><em>&lt;port&gt;</em></code></td>
      <td>数据获取端口。如果未指定端口，那么将使用标准端口 <code>9091</code>。<p>对于 syslog，请指定日志收集器服务器的端口。如果未指定端口，那么将使用标准端口 <code>514</code>。</td>
    </tr>
    <tr>
      <td><code><em>&lt;cluster_space&gt;</em></code></td>
      <td>可选：要向其发送日志的 Cloud Foundry 空间的名称。将日志转发到 {{site.data.keyword.loganalysisshort_notm}} 时，会在数据获取点中指定空间和组织。如果未指定空间，日志将发送到帐户级别。</td>
    </tr>
    <tr>
      <td><code><em>&lt;cluster_org&gt;</em></code></td>
      <td>该空间所在 Cloud Foundry 组织的名称。如果指定了空间，那么此值是必需的。</td>
    </tr>
    <tr>
      <td><code><em>&lt;type&gt;</em></code></td>
      <td>要转发日志的位置。选项为 <code>ibm</code>（将日志转发到 {{site.data.keyword.loganalysisshort_notm}}）和 <code>syslog</code>（将日志转发到外部服务器）。</td>
    </tr>
    <tr>
      <td><code><em>&lt;paths_to_logs&gt;</em></code></td>
      <td>其容器上应用程序要将日志记录到的路径。要转发源类型为 <code>application</code> 的日志，必须提供路径。要指定多个路径，请使用逗号分隔列表。示例：<code>/var/log/myApp1/*/var/log/myApp2/*</code></td>
    </tr>
    <tr>
      <td><code><em>&lt;containers&gt;</em></code></td>
      <td>可选：转发来自应用程序的日志时，可以指定包含应用程序的容器的名称。可以使用逗号分隔列表来指定多个容器。如果未指定任何容器，那么会转发来自包含所提供路径的所有容器中的日志。</td>
    </tr>
  </tbody>
  </table>

2. 通过以下两种方式中的一种来验证配置是否正确：

    * 列出集群中的所有日志记录配置：
      ```
    bx cs logging-config-get <my_cluster>
    ```
      {: pre}

      输出示例：

      ```
      Id                                    Source       Namespace     Host                          Port   Org      Space      Protocol     Paths
      f4bc77c0-ee7d-422d-aabf-a4e6b977264e  kubernetes   -             172.30.162.138                5514   -        -          syslog       /var/log/kubelet.log,/var/log/kube-proxy.log
      5bd9c609-13c8-4c48-9d6e-3a6664c825a9  application  -             ingest.logging.ng.bluemix.net 9091   my_org   my_space   ibm          /var/log/apps/**/*.log,/var/log/apps/**/*.err
      8a284f1a-451c-4c48-b1b4-a4e6b977264e  containers   my-namespace  myhostname.common             5514   -        -          syslog       -
      ```
      {: screen}

    * 列出一种类型日志源的日志记录配置：
      ```
      bx cs logging-config-get <my_cluster> --logsource worker
      ```
      {: pre}

      输出示例：

      ```
      Id                                    Source    Namespace   Host                            Port   Org    Space     Protocol    Paths
      f4bc77c0-ee7d-422d-aabf-a4e6b977264e  worker    -           ingest.logging.ng.bluemix.net   9091   -      -         ibm         /var/log/syslog,/var/log/auth.log
      5bd9c609-13c8-4c48-9d6e-3a6664c825a9  worker    -           172.30.162.138                  5514   -      -         syslog      /var/log/syslog,/var/log/auth.log
      ```
      {: screen}

要对配置进行更新，请执行相同的步骤，但将 `bx cs logging-config-create` 替换为 `bx cs logging-config-update`。请确保验证更新。
{: tip}

<br />


## 查看日志
{: #view_logs}

要查看集群和容器的日志，可以使用标准的 Kubernetes 和 Docker 日志记录功能。
{:shortdesc}

### {{site.data.keyword.loganalysislong_notm}}
{: #view_logs_k8s}

可以通过 Kibana 仪表板查看转发到 {{site.data.keyword.loganalysislong_notm}} 的日志。
{: shortdesc}

如果使用缺省值来创建配置文件，那么可以在创建集群的帐户或者组织和空间中找到日志。如果在配置文件中指定了组织和空间，那么可以在该空间中找到日志。有关日志记录的更多信息，请参阅 [{{site.data.keyword.containershort_notm}} 的日志记录](/docs/services/CloudLogAnalysis/containers/containers_kubernetes.html#containers_kubernetes)。

要访问 Kibana 仪表板，请转至以下某个 URL，然后选择在其中创建了集群的 {{site.data.keyword.Bluemix_notm}} 帐户或空间。
- 美国南部和美国东部：https://logging.ng.bluemix.net
- 英国南部：https://logging.eu-gb.bluemix.net
- 欧洲中部：https://logging.eu-fra.bluemix.net
- 亚太南部：https://logging.au-syd.bluemix.net

有关查看日志的更多信息，请参阅[通过 Web 浏览器导航至 Kibana](/docs/services/CloudLogAnalysis/kibana/launch.html#launch_Kibana_from_browser)。

### Docker 日志
{: #view_logs_docker}

可以利用内置 Docker 日志记录功能来查看标准 STDOUT 和 STDERR 输出流上的活动。有关更多信息，请参阅[查看在 Kubernetes 集群中运行的容器的容器日志](/docs/services/CloudLogAnalysis/containers/containers_kubernetes.html#containers_kubernetes)。

<br />


## 停止日志转发
{: #log_sources_delete}

可以停止集群的一个或全部日志记录配置的日志转发。
{: shortdesc}

1. [设定 CLI 的目标](cs_cli_install.html#cs_cli_configure)为日志源所在的集群。

2. 删除日志记录配置。
<ul>
<li>删除一个日志记录配置：</br>
  <pre><code>bx cs logging-config-rm &lt;my_cluster&gt; --id &lt;log_config_id&gt;</pre></code>
  <table>
    <caption>了解此命令的组成部分</caption>
      <thead>
        <th colspan=2><img src="images/idea.png" alt="“构想”图标"/> 了解此命令的组成部分</th>
      </thead>
        <tbody>
        <tr>
          <td><code><em>&lt;my_cluster&gt;</em></code></td>
          <td>日志记录配置所在的集群的名称。</td>
        </tr>
        <tr>
          <td><code><em>&lt;log_config_id&gt;</em></code></td>
          <td>日志源配置的标识。</td>
        </tr>
        </tbody>
  </table></li>
<li>删除所有日志记录配置：</br>
  <pre><code>bx cs logging-config-rm <my_cluster> --all</pre></code></li>
</ul>

<br />


## 为 Kubernetes API 审计日志配置日志转发
{: #app_forward}

可以通过 Kubernetes API 服务器配置 Webhook，以捕获来自集群的任何调用。通过启用 Webhook，可将日志发送到远程服务器。
{: shortdesc}

有关 Kubernetes 审计日志的更多信息，请参阅 Kubernetes 文档中的<a href="https://kubernetes.io/docs/tasks/debug-application-cluster/audit/" target="blank">审计主题 <img src="../icons/launch-glyph.svg" alt="外部链接图标"></a>。

* 仅 Kubernetes V1.7 和更高版本支持 Kubernetes API 审计日志的转发。
* 目前，缺省审计策略用于具有此日志记录配置的所有集群。
* 审计日志只能转发到外部服务器。
{: tip}

### 启用 Kubernetes API 审计日志转发
{: #audit_enable}

开始之前：

1. 设置可以转发日志的远程日志记录服务器。例如，您可以[将 Logstash 用于 Kubernetes ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://kubernetes.io/docs/tasks/debug-application-cluster/audit/#use-logstash-to-collect-and-distribute-audit-events-from-webhook-backend) 以收集审计事件。

2. [设定 CLI 的目标](cs_cli_install.html#cs_cli_configure)为要从中收集 API 服务器审计日志的集群。**注**：如果使用的是 Dedicated 帐户，那么必须登录到公共 {{site.data.keyword.cloud_notm}} 端点并将公共组织和空间设定为目标，才能启用日志转发。


转发 Kubernetes API 审计日志：

1. 配置 Webhook。如果未在标志中提供任何信息，那么将使用缺省配置。

    ```
    bx cs apiserver-config-set audit-webhook <my_cluster> --remoteServer <server_URL_or_IP> --caCert <CA_cert_path> --clientCert <client_cert_path> --clientKey <client_key_path>
    ```
    {: pre}

    <table>
    <caption>了解此命令的组成部分</caption>
    <thead>
    <th colspan=2><img src="images/idea.png" alt="“构想”图标"/> 了解此命令的组成部分</th>
    </thead>
    <tbody>
    <tr>
    <td><code><em>&lt;my_cluster&gt;</em></code></td>
    <td>集群的名称或标识。</td>
    </tr>
    <tr>
    <td><code><em>&lt;server_URL&gt;</em></code></td>
    <td>要向其发送日志的远程日志记录服务的 URL 或 IP 地址。如果提供了不安全的服务器 URL，那么将忽略证书。</td>
    </tr>
    <tr>
    <td><code><em>&lt;CA_cert_path&gt;</em></code></td>
    <td>用于验证远程日志记录服务的 CA 证书的文件路径。</td>
    </tr>
    <tr>
    <td><code><em>&lt;client_cert_path&gt;</em></code></td>
    <td>用于向远程日志记录服务进行认证的客户机证书的文件路径。</td>
    </tr>
    <tr>
    <td><code><em>&lt;client_key_path&gt;</em></code></td>
    <td>用于连接到远程日志记录服务的相应客户机密钥的文件路径。</td>
    </tr>
    </tbody></table>

2. 通过查看远程日志记录服务的 URL 来验证是否已启用日志转发。

    ```
    bx cs apiserver-config-get audit-webhook <my_cluster>
    ```
    {: pre}

    输出示例：
    ```
    OK
    Server:			https://8.8.8.8
    ```
    {: screen}

3. 通过重新启动 Kubernetes 主节点来应用配置更新。

    ```
    bx cs apiserver-refresh <my_cluster>
    ```
    {: pre}

### 停止 Kubernetes API 审计日志转发
{: #audit_delete}

您可以通过禁用集群的 API 服务器的 Webhook 后端配置来停止转发审计日志。

开始之前，请将[设定 CLI 的目标](cs_cli_install.html#cs_cli_configure)设置为要从中停止收集 API 服务器审计日志的集群。

1. 禁用集群 API 服务器的 Webhook 后端配置。

    ```
    bx cs apiserver-config-unset audit-webhook <my_cluster>
    ```
    {: pre}

2. 通过重新启动 Kubernetes 主节点来应用配置更新。

    ```
    bx cs apiserver-refresh <my_cluster>
    ```
    {: pre}

<br />


## 配置集群监视
{: #monitoring}

度量值可帮助您监视集群的运行状况和性能。可以配置工作程序节点的运行状况监视，以自动检测并更正进入已降级或非运行状态的任何工作程序。**注**：仅标准集群支持监视功能。
{:shortdesc}

## 查看度量值
{: #view_metrics}

您可以使用标准 Kubernetes 和 Docker 功能来监视集群和应用程序的运行状况。
{:shortdesc}

<dl>
  <dt>{{site.data.keyword.Bluemix_notm}} 中的集群详细信息页面</dt>
    <dd>{{site.data.keyword.containershort_notm}} 提供了有关集群的运行状况和容量以及集群资源使用情况的信息。可以使用此 GUI 通过 {{site.data.keyword.Bluemix_notm}} 服务绑定来向外扩展集群、使用持久性存储器以及向集群添加更多功能。要查看集群详细信息页面，请转至 **{{site.data.keyword.Bluemix_notm}} 仪表板**，然后选择集群。</dd>
  <dt>Kubernetes 仪表板</dt>
    <dd>Kubernetes 仪表板是一个管理 Web 界面，可以在其中查看工作程序节点的运行状况，查找 Kubernetes 资源，部署容器化应用程序，以及使用日志记录和监视信息对应用程序进行故障诊断。有关如何访问 Kubernetes 仪表板的更多信息，请参阅[启动 {{site.data.keyword.containershort_notm}} 的 Kubernetes 仪表板](cs_app.html#cli_dashboard)。</dd>
  <dt>{{site.data.keyword.monitoringlong_notm}}</dt>
    <dd>标准集群的度量值位于创建 Kubernetes 集群时登录到的 {{site.data.keyword.Bluemix_notm}} 帐户中。如果在创建集群时指定了 {{site.data.keyword.Bluemix_notm}} 空间，那么度量值将位于该空间中。将为集群中部署的所有容器自动收集容器度量值。这些度量值会通过 Grafana 发送并使其可用。有关度量值的更多信息，请参阅[监视 {{site.data.keyword.containershort_notm}}](/docs/services/cloud-monitoring/containers/monitoring_containers_ov.html#monitoring_bmx_containers_ov)。<p>要访问 Grafana 仪表板，请转至以下某个 URL，然后选择在其中已创建集群的 {{site.data.keyword.Bluemix_notm}} 帐户或空间。<ul><li>美国南部和美国东部：https://metrics.ng.bluemix.net
</li><li>英国南部：https://metrics.eu-gb.bluemix.net</li><li>欧洲中部：https://metrics.eu-de.bluemix.net</li></ul></p></dd>
</dl>

### 其他运行状况监视工具
{: #health_tools}

可以配置其他工具来执行更多监视功能。
<dl>
  <dt>Prometheus</dt>
    <dd>Prometheus 是一个开放式源代码监视、日志记录和警报工具，专为 Kubernetes 而设计。该工具基于 Kubernetes 日志记录信息来检索有关集群、工作程序节点和部署运行状况的详细信息。有关设置信息，请参阅[将服务与 {{site.data.keyword.containershort_notm}} 集成](cs_integrations.html#integrations)。</dd>
</dl>

<br />


## 使用自动恢复为工作程序节点配置运行状况监视
{: #autorecovery}

可以将 {{site.data.keyword.containerlong_notm}} 自动恢复系统部署到 Kubernetes V1.7 或更高版本的现有集群中。
{: shortdesc}

自动恢复系统会使用各种检查来查询工作程序节点的运行状态。如果自动恢复根据配置的检查，检测到运行状况欠佳的工作程序节点，那么自动恢复会触发更正操作，例如在工作程序节点上重装操作系统。一次只会对一个工作程序节点执行更正操作。该工作程序节点必须成功完成更正操作后，才能对其他任何工作程序节点执行更正操作。
有关更多信息，请参阅此[自动恢复博客帖子 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/12/autorecovery-utilizes-consistent-hashing-high-availability/)。**注**：自动恢复至少需要一个正常运行的节点才能有效运行。仅在具有两个或两个以上工作程序节点的集群中，将自动恢复配置为执行主动检查。

开始之前，请[设定 CLI 的目标](cs_cli_install.html#cs_cli_configure)为要检查其工作程序节点状态的集群。

1. 创建配置映射文件以通过 JSON 格式定义检查。例如，以下 YAML 文件定义了三项检查：一项 HTTP 检查和两项 Kubernetes API 服务器检查。</br>
   **提示**：将每项检查定义为配置映射中 data 部分中的唯一键。

   ```
    kind: ConfigMap
    apiVersion: v1
    metadata:
      name: ibm-worker-recovery-checks
      namespace: kube-system
    data:
      checkhttp.json: |
        {
          "Check":"HTTP",
          "FailureThreshold":3,
          "CorrectiveAction":"REBOOT",
          "CooloffSeconds":1800,
          "IntervalSeconds":180,
          "TimeoutSeconds":10,
          "Port":80,
          "ExpectedStatus":200,
          "Route":"/myhealth",
          "Enabled":false
        }
      checknode.json: |
        {
          "Check":"KUBEAPI",
          "Resource":"NODE",
          "FailureThreshold":3,
          "CorrectiveAction":"RELOAD",
          "CooloffSeconds":1800,
          "IntervalSeconds":180,
          "TimeoutSeconds":10,
          "Enabled":true
        }
      checkpod.json: |
        {
          "Check":"KUBEAPI",
          "Resource":"POD",
          "PodFailureThresholdPercent":50,
          "FailureThreshold":3,
          "CorrectiveAction":"RELOAD",
          "CooloffSeconds":1800,
          "IntervalSeconds":180,
          "TimeoutSeconds":10,
          "Enabled":true
      }
    ```
   {:codeblock}

   <table summary="了解配置映射的组成部分">
   <caption>了解配置映射的组成部分</caption>
   <thead>
   <th colspan=2><img src="images/idea.png" alt="“构想”图标"/> 了解配置映射的组成部分</th>
   </thead>
   <tbody>
   <tr>
   <td><code>name</code></td>
   <td>配置名称 <code>ibm-worker-recovery-checks</code> 是常量，无法更改。</td>
   </tr>
   <tr>
   <td><code>namespace</code></td>
   <td><code>kube-system</code> 名称空间是常量，无法更改。</td>
   </tr>
   <tr>
   <td><code>checkhttp.json</code></td>
   <td>定义 HTTP 检查，用于检查 HTTP 服务器是否在每个节点的 IP 地址的端口 80 上运行，并在路径 <code>/myhealth</code> 处返回 200 响应。可以通过运行 <code>kubectl get nodes</code> 来查找节点的 IP 地址。
               例如，假设集群中有两个节点，其 IP 地址分别为 10.10.10.1 和 10.10.10.2。在此示例中，会对下面两个路径检查是否返回“200 正常”响应：<code>http://10.10.10.1:80/myhealth</code> 和 <code>http://10.10.10.2:80/myhealth</code>。
               示例 YAML 中的检查每 3 分钟运行一次。如果连续失败三次，将重新引导节点。此操作相当于运行 <code>bx cs worker-reboot</code>。HTTP 检查会一直处于禁用状态，直到您将 <b>Enabled</b> 字段设置为 <code>true</code>。</td>
   </tr>
   <tr>
   <td><code>checknode.json</code></td>
   <td>定义 Kubernetes API 节点检查，用于检查是否每个节点都处于 <code>Ready</code> 状态。如果特定节点不处于 <code>Ready</code> 状态，那么对该节点的检查计为一次失败。
               示例 YAML 中的检查每 3 分钟运行一次。如果连续失败三次，将重新装入节点。此操作相当于运行 <code>bx cs worker-reload</code>。节点检查会一直处于启用状态，直到您将 <b>Enabled</b> 字段设置为 <code>false</code> 或除去检查。</td>
   </tr>
   <tr>
   <td><code>checkpod.json</code></td>
   <td>定义 Kubernetes API pod 检查，用于根据分配给节点的 pod 总数来检查该节点上 <code>NotReady</code> pod 的总百分比。如果特定节点的 <code>NotReady</code> pod 的总百分比大于定义的 <code>PodFailureThresholdPercent</code>，那么对该节点的检查计为一次失败。
               示例 YAML 中的检查每 3 分钟运行一次。如果连续失败三次，将重新装入节点。此操作相当于运行 <code>bx cs worker-reload</code>。pod 检查会一直处于启用状态，直到您将 <b>Enabled</b> 字段设置为 <code>false</code> 或除去检查。</td>
   </tr>
   </tbody>
   </table>


   <table summary="了解单个规则的组成部分">
   <caption>了解单个规则的组成部分</caption>
   <thead>
   <th colspan=2><img src="images/idea.png" alt="“构想”图标"/> 了解单个规则的组成部分</th>
   </thead>
   <tbody>
   <tr>
   <td><code>Check</code></td>
   <td>输入希望自动恢复使用的检查类型。<ul><li><code>HTTP</code>：自动恢复调用在每个节点上运行的 HTTP 服务器，以确定节点是否在正常运行。</li><li><code>KUBEAPI</code>：自动恢复调用 Kubernetes API 服务器并读取工作程序节点报告的运行状态数据。</li></ul></td>
   </tr>
   <tr>
   <td><code>资源</code></td>
   <td>检查类型为 <code>KUBEAPI</code> 时，输入希望自动恢复检查的资源类型。接受的值为 <code>NODE</code> 或 <code>PODS</code>。</td>
   </tr>
   <tr>
   <td><code>FailureThreshold</code></td>
   <td>输入检查连续失败次数的阈值。达到此阈值时，自动恢复会触发指定的更正操作。例如，如果值为 3 且自动恢复连续三次执行配置的检查失败，那么自动恢复会触发与检查关联的更正操作。</td>
   </tr>
   <tr>
   <td><code>PodFailureThresholdPercent</code></td>
   <td>资源类型为 <code>PODS</code> 时，请输入工作程序节点上可以处于 [NotReady ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/#define-readiness-probes) 状态的 pod 的百分比阈值。此百分比基于安排到一个工作程序节点的 pod 总数。检查确定运行状况欠佳的 pod 百分比大于阈值时，该检查计为一次失败。</td>
   </tr>
   <tr>
   <td><code>CorrectiveAction</code></td>
   <td>输入在达到失败阈值时要运行的操作。仅当没有其他工作程序在进行修复，并且此工作程序节点距离执行上一个更正操作的时间已超过等待期时，才会运行更正操作。<ul><li><code>REBOOT</code>：重新引导工作程序节点。</li><li><code>RELOAD</code>：从干净的操作系统重新装入工作程序节点的所有必需配置。</li></ul></td>
   </tr>
   <tr>
   <td><code>CooloffSeconds</code></td>
   <td>输入自动恢复在对节点发出更正操作后，必须等待多长时间才能再次向该节点发出其他更正操作（以秒为单位）。等待期自发出更正操作时开始计算。</td>
   </tr>
   <tr>
   <td><code>IntervalSeconds</code></td>
   <td>输入连续检查的间隔秒数。例如，如果值为 180，那么自动恢复会每 3 分钟对每个节点运行一次检查。</td>
   </tr>
   <tr>
   <td><code>TimeoutSeconds</code></td>
   <td>输入在自动恢复终止调用操作之前，对数据库执行检查调用所用的最长时间（以秒为单位）。<code>TimeoutSeconds</code> 的值必须小于 <code>IntervalSeconds</code> 的值。</td>
   </tr>
   <tr>
   <td><code>端口</code></td>
   <td>检查类型为 <code>HTTP</code> 时，请输入工作程序节点上 HTTP 服务器必须绑定到的端口。此端口必须在集群中每个工作程序节点的 IP 上公开。自动恢复需要一个跨所有节点的常量端口号以用于检查服务器。将定制服务器部署到集群中时，请使用 [DaemonSets ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)。</td>
   </tr>
   <tr>
   <td><code>ExpectedStatus</code></td>
   <td>检查类型为 <code>HTTP</code> 时，请输入期望从检查返回的 HTTP 服务器状态。例如，值为 200 表示期望服务器返回 <code>OK</code> 响应。</td>
   </tr>
   <tr>
   <td><code>Route</code></td>
   <td>检查类型为 <code>HTTP</code> 时，请输入从 HTTP 服务器请求的路径。此值通常是在所有工作程序节点上运行的服务器的度量值路径。</td>
   </tr>
   <tr>
   <td><code>Enabled</code></td>
   <td>输入 <code>true</code> 以启用检查，或输入 <code>false</code> 以禁用检查。</td>
   </tr>
   </tbody>
   </table>

2. 在集群中创建配置映射。

    ```
    kubectl apply -f <my_file.yaml>
    ```
    {: pre}

3. 使用相应检查来验证是否已在 `kube-system` 名称空间中创建名称为 `ibm-worker-recovery-checks` 的配置映射。

    ```
    kubectl -n kube-system get cm ibm-worker-recovery-checks -o yaml
    ```
    {: pre}

4. 通过应用此 YAML 文件，将自动恢复部署到集群中。

   ```
   kubectl apply -f https://raw.githubusercontent.com/IBM-Cloud/kube-samples/master/ibm-worker-recovery/ibm-worker-recovery.yml
   ```
   {: pre}

5. 过几分钟后，可以检查以下命令的输出中的 `Events` 部分，以查看自动恢复部署上的活动。

    ```
    kubectl -n kube-system describe deployment ibm-worker-recovery
    ```
    {: pre}
