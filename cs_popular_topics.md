---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}




# Popular topics for {{site.data.keyword.containershort_notm}}
{: #cs_popular_topics}

Check out what container developers are interested in learning about in {{site.data.keyword.containerlong}}.
{:shortdesc}

## Popular topics in May 2018
{: #may18}


<table summary="The table shows popular topics. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Popular topics for containers and Kubernetes clusters in May 2018</caption>
<thead>
<th>Date</th>
<th>Title</th>
<th>Description</th>
</thead>
<tbody>
<tr>
<td>14 May</td>
<td>[Update: Deploy workloads on GPU bare metal worldwide](cs_app.html#gpu_app)</td>
<td>If you have a [bare metal graphics processing unit (GPU) machine type](cs_clusters.html#shared_dedicated_node) in your cluster, you can schedule mathematically intensive apps. The GPU worker node can process your app's workload across both the CPU and GPU to increase performance.</td>
</tr>
<tr>
<td>03 May</td>
<td>[Container Image Security Enforcement (beta)](/docs/services/Registry/registry_security_enforce.html#security_enforce)</td>
<td>Does your team need a little extra help to know which image to pull in your app containers? Try out the Container Image Security Enforcement beta to verify container images before you deploy them. Available for clusters that run Kubernetes 1.9 or later.</td>
</tr>
<tr>
<td>01 May</td>
<td>[Deploy the Kubernetes dashboard from the GUI](cs_app.html#cli_dashboard)</td>
<td>Did you ever want to access the Kubernetes dashboard with one click? Check out the **Kubernetes Dashboard** button in the {{site.data.keyword.Bluemix_notm}} GUI.</td>
</tr>
</tbody></table>




## Popular topics in April 2018
{: #apr18}

<table summary="The table shows popular topics. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Popular topics for containers and Kubernetes clusters in April 2018</caption>
<thead>
<th>Date</th>
<th>Title</th>
<th>Description</th>
</thead>
<tbody>
<tr>
<td>17 April</td>
<td>{{site.data.keyword.Bluemix_notm}} Block Storage</td>
<td>Install the {{site.data.keyword.Bluemix_notm}} Block Storage [plug-in](cs_storage.html#install_block) to save persistent data in block storage. Then, you can [create new](cs_storage.html#create) or [use existing](cs_storage.html#existing_block) block storage for your cluster.</td>
</tr>
<tr>
<td>13 April</td>
<td>[New tutorial to migrate Cloud Foundry apps to clusters](cs_tutorials_cf.html#cf_tutorial)</td>
<td>Do you have a Cloud Foundry app? Learn how to deploy the same code from that app to a container that runs in a Kubernetes cluster.</td>
</tr>
<tr>
<td>5 April</td>
<td>[Filtering logs](cs_health.html#filter-logs)</td>
<td>Filter out specific logs from being forwarded. Logs can be filtered out for a specific namespace, container name, log level, and message string.</td>
</tr>
</tbody></table>

## Popular topics in March 2018
{: #mar18}

<table summary="The table shows popular topics. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Popular topics for containers and Kubernetes clusters in March 2018</caption>
<thead>
<th>Date</th>
<th>Title</th>
<th>Description</th>
</thead>
<tbody>
<tr>
<td>16 March</td>
<td>[Provision a bare metal cluster with Trusted Compute](cs_clusters.html#shared_dedicated_node)</td>
<td>Create a bare metal cluster that runs [Kubernetes version 1.9](cs_versions.html#cs_v19) or later, and enable Trusted Compute to verify your worker nodes against tampering.</td>
</tr>
<tr>
<td>14 March</td>
<td>[Secure sign-in with {{site.data.keyword.appid_full}}](cs_integrations.html#appid)</td>
<td>Enhance your apps that are running in {{site.data.keyword.containershort_notm}} by requiring users to sign in.</td>
</tr>
<tr>
<td>13 March</td>
<td>[Location available in São Paulo](cs_regions.html)</td>
<td>Welcome São Paulo, Brazil as a new location in the US South region. If you have a firewall, be sure to [open the firewall ports](cs_firewall.html#firewall) for this location and the others within the region that your cluster is in.</td>
</tr>
<tr>
<td>12 March</td>
<td>[Just joined the {{site.data.keyword.Bluemix_notm}} with a Trial account? Try out a free Kubernetes cluster!](container_index.html#clusters)</td>
<td>With a Trial [{{site.data.keyword.Bluemix_notm}} account](https://console.bluemix.net/registration/), you can deploy one free cluster for 21 days to test out Kubernetes capabilities.</td>
</tr>
</tbody></table>

## Popular topics in February 2018
{: #feb18}

<table summary="The table shows popular topics. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Popular topics for containers and Kubernetes clusters in February 2018</caption>
<thead>
<th>Date</th>
<th>Title</th>
<th>Description</th>
</thead>
<tbody>
<tr>
<td>27 February</td>
<td>Hardware virtual machine (HVM) images for worker nodes</td>
<td>Increase the I/O performance of your workloads with HVM images. Activate on each existing worker node by using the `bx cs worker-reload` [command](cs_cli_reference.html#cs_worker_reload) or the `bx cs worker-update` [command](cs_cli_reference.html#cs_worker_update).</td>
</tr>
<tr>
<td>26 February</td>
<td>[KubeDNS autoscaling](https://kubernetes.io/docs/tasks/administer-cluster/dns-horizontal-autoscaling/)</td>
<td>KubeDNS now scales with your cluster as it grows. You can adjust the scaling rations by using the following command: `kubectl -n kube-system edit cm kube-dns-autoscaler`.</td>
</tr>
<tr>
<td>23 February</td>
<td>View the web UI for [logging](cs_health.html#view_logs) and [metrics](cs_health.html#view_metrics)</td>
<td>Easily view log and metric data on your cluster and its components with an improved web UI. See your cluster detail page for access.</td>
</tr>
<tr>
<td>20 February</td>
<td>Encrypted images and [signed, trusted content](../services/Registry/registry_trusted_content.html#registry_trustedcontent)</td>
<td>In {{site.data.keyword.registryshort_notm}}, you can sign and encrypt images to ensure their integrity when you store the images in your registry namespace. Run your container instances by using only trusted content.</td>
</tr>
<tr>
<td>19 February</td>
<td>[Set up the strongSwan IPSec VPN](cs_vpn.html#vpn-setup)</td>
<td>Quickly deploy the strongSwan IPSec VPN Helm chart to connect your {{site.data.keyword.containershort_notm}} cluster securely to your on-premises data center without a Vyatta.</td>
</tr>
<tr>
<td>14 February</td>
<td>[Location available in Seoul](cs_regions.html)</td>
<td>Just in time for the Olympics, deploy a Kubernetes cluster to Seoul in the AP North region. If you have a firewall, be sure to [open the firewall ports](cs_firewall.html#firewall) for this location and the others within the region that your cluster is in.</td>
</tr>
<tr>
<td>8 February</td>
<td>[Update Kubernetes 1.9](cs_versions.html#cs_v19)</td>
<td>Review the changes to make to your clusters before you update to Kubernetes 1.9.</td>
</tr>
</tbody></table>

## Popular topics in January 2018
{: #jan18}

<table summary="The table shows popular topics. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Popular topics for containers and Kubernetes clusters in January 2018</caption>
<thead>
<th>Date</th>
<th>Title</th>
<th>Description</th>
</thead>
<tbody>
<td>25 January</td>
<td>[Global registry available](../services/Registry/registry_overview.html#registry_regions)</td>
<td>With the {{site.data.keyword.registryshort_notm}}, you can use the global `registry.bluemix.net` to pull IBM-provided public images.</td>
</tr>
<tr>
<td>23 January</td>
<td>[Locations available in Singapore and Montreal, CA](cs_regions.html)</td>
<td>Singapore and Montreal are locations available in the {{site.data.keyword.containershort_notm}} AP North and US East regions. If you have a firewall, be sure to [open the firewall ports](cs_firewall.html#firewall) for these locations and the others within the region that your cluster is in.</td>
</tr>
<tr>
<td>8 January</td>
<td>[Enhanced flavors available](cs_cli_reference.html#cs_machine_types)</td>
<td>Series 2 virtual machine types include local SSD storage and disk encryption. [Move your workloads](cs_cluster_update.html#machine_type) to these flavors for improved performance and stability.</td>
</tr>
</tbody></table>

## Chat with like-minded developers on Slack
{: #slack}

You can see what others are talking about and ask your own questions in the [{{site.data.keyword.containershort_notm}} Slack. ![External link icon](../icons/launch-glyph.svg "External link icon")](https://ibm-container-service.slack.com)
{:shortdesc}

If you are not using an IBM ID for your {{site.data.keyword.Bluemix_notm}} account, [request an invitation](https://bxcs-slack-invite.mybluemix.net/) to this Slack.
{: tip}
