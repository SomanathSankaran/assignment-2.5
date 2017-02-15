# assignment-2.5
QN 1   Explain what is a cluster and what is a hadoop cluster

CLUSTER
1.A computer cluster consists of a set of loosely or tightly connected computers that work together so that, in many respects, they can be viewed as a single system. Unlike grid computers, computer clusters have each node set to perform the same task, controlled and scheduled by software.
2.The components of a cluster are usually connected to each other through fast local area networks ("LAN"), with each node (computer used as a server) running its own instance of an operating system. In most circumstances, all of the nodes use the same hardware and the same operating system, although in some setups (i.e. using Open Source Cluster Application Resources (OSCAR)), different operating systems can be used on each computer, and/or different hardware.
3.They are usually deployed to improve performance and availability over that of a single computer, while typically being much more cost-effective than single computers of comparable speed or availability.

HADOOP CLUSTER
A Hadoop cluster is a special type of computational cluster designed specifically for storing and analyzing huge amounts of unstructured data in a distributed computing environment. 

Such clusters run Hadoop's open source distributed processing software on low-cost commodity computers. Typically one machine in the cluster is designated as the NameNode and another machine the as JobTracker; these are the masters. The rest of the machines in the cluster act as both DataNode and TaskTracker; these are the slaves. Hadoop clusters are often referred to as "shared nothing" systems because the only thing that is shared between nodes is the network that connects them. 

Hadoop clusters are known for boosting the speed of data analysis applications. They also are highly scalable: If a cluster's processing power is overwhelmed by growing volumes of data, additional cluster nodes can be added to increase throughput. Hadoop clusters also are highly resistant to failure because each piece of data is copied onto other cluster nodes, which ensures that the data is not lost if one node fails.

QN 2.WHAT IS MEANT BY RACK AND EXPLAIN RACK ARRANGEMENT IN HADOOP  CLUSTER

 RACK
mounted describes a unit of electronic equipment that is housed in a metal framework called an equipment rack. Usually, an equipment rack contains multiple "bays," each designed to hold a unit of equipment such as a computer server . Typically, the equipment unit is mounted (inserted into a bay in the rack) and secured in place with screws. 
Rack-mounted describes a unit of electronic equipment that is housed in a metal framework called an equipment rack. Usually, an equipment rack contains multiple "bays," each designed to hold a unit of equipment such as a computer server . Typically, the equipment unit is mounted (inserted into a bay in the rack) and secured in place with screws.

A rack server, also called a rack-mounted server, is a computer dedicated to use as a server and designed to be installed in a framework called a rack. The rack contains multiple mounting slots called bays, each designed to hold a hardware unit secured in place with screws. A rack server has a low-profile enclosure, in contrast to a tower server, which is built into an upright, standalone cabinet.

A single rack can contain multiple servers stacked one above the other, consolidating network resources and minimizing the required floor space. The rack server configuration also simplifies cabling among network components. In an equipment rack filled with servers, a special cooling system is necessary to prevent excessive heat buildup that would otherwise occur when many power-dissipating components are confined in a small space.
 1 RACK UNIT is equal to  1 and quarter inches and it is the space between three consecutive holes in a rack.

RACK ARRANGEMENT IN HADOOP  CLUSTER

In Hadoop we assume that there are 3 blocks namely A,B,C with replication factor of 3 and there are 3 physical Racks(1,2,3).So THERE WILL BE "9" BLOCKS((A,A1,A2),(B,B1,B2),(C,C1,C2)).Due to rack awareness the replicas A A1 and A2 will be stored in seperate racks AS 
SHOWN IN FIGURE ATTACHED
What happens if Rack1 goes down? We still have the block replicas in other data nodes
So evidently Rack awareness increases data availability. Also the HDFS balancer and decommissioning of data nodes are rack aware operations.

What about performance?

Faster replication operation. Since the replicas are placed within the same rack it would use higher bandwidth and lower latency hence making it faster.
If YARN is unable to create a container in the same data node where the queried data is located it would try to create the container in a data node within the same rack. This would be more performant because of the higher bandwidth and lower latency of the data nodes inside the same rack.
