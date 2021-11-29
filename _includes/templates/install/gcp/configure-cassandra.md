Using Cassandra is an optional step. 
We recommend to use Cassandra if you plan to insert more than 5K data points per second or would like to optimize storage space.

##### Provision additional node groups

Provision additional node groups that will be hosting Cassandra instances. 
You may change the machine type. At least 4 vCPUs and 16GB of RAM is recommended.

We will create **3** separate node pools with **1** node per zone. 
Since we plan to use zonal disks, we don't want k8s to launch a pod on the node where the corresponding disk is not available.
Those zones will have the same node label. We will use this label to target deployment of our stateful set.

So, first, define **3** zones within your region:

```bash
export GCP_CASSANDRA_ZONE1=us-central1-a
export GCP_CASSANDRA_ZONE2=us-central1-b
export GCP_CASSANDRA_ZONE3=us-central1-c
```
{: .copy-code}

```bash
gcloud container node-pools create cassandra1 --cluster=$TB_CLUSTER_NAME --zone=$GCP_ZONE --node-locations=$GCP_CASSANDRA_ZONE1 \
--node-labels=role=cassandra --num-nodes=1 --min-nodes=1 --max-nodes=1 --machine-type=e2-standard-4
gcloud container node-pools create cassandra2 --cluster=$TB_CLUSTER_NAME --zone=$GCP_ZONE --node-locations=$GCP_CASSANDRA_ZONE2 \
--node-labels=role=cassandra --num-nodes=1 --min-nodes=1 --max-nodes=1 --machine-type=e2-standard-4
gcloud container node-pools create cassandra3 --cluster=$TB_CLUSTER_NAME --zone=$GCP_ZONE --node-locations=$GCP_CASSANDRA_ZONE3 \
--node-labels=role=cassandra --num-nodes=1 --min-nodes=1 --max-nodes=1 --machine-type=e2-standard-4
```
{: .copy-code}

{% assign tbCassandraRegion = "$GCP_REGION" tbCassandraRegionComments = ": " %}
{% include templates/install/cassandra-k8s-common.md %}