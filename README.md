# Big-Data-Analytics
Use Case 1: COVID-19 Monitoring Platform
Use Case 2: Smart Repairing System

Objectives: To understand the challenges and opportunities in dealing with Big Data using
two use cases: 1. Covid-19 monitoring platform to predict next geographical area where
covid-19 outbreak is likely to occur. 2. Smart repairing system whereby faults are
automatically reported to nearby garages and designing a Big Data infrastructure solution for
these use cases.


Methods: To design the big data infrastructures Hadoop Framework is used with appropriate
components for each use case.


Reflections: The module helped on designing a big data analytics architecture with different
components using open-source Hadoop framework to provide a scalable data processing
solution. Acquired hands-on experience in practical seminars and interactive group activities.


Discussion & Conclusion: The proposed system design solutions being modular, are
scalable enough to handle and process massive amounts of data. There could be some
ethical issues which need to be addressed but the big data systems provides solutions for
the global challenges and maintain sustainability.

Use Case 1: COVID-19 Monitoring Platform
Figure 1: Data Architecture of Covid-19 Monitoring System
![image](https://user-images.githubusercontent.com/120987787/224342583-43ecfaa7-91f1-43b1-881d-61aef2cabc14.png)

Covid-19 big data can be handled by distributing and processing it in parallel over several
nodes. Hadoop is the open-source framework that serves this purpose and could also
perform analytics . Hadoop framework consists of a number of tools or
components. Following are the components used in this use case:

Hadoop Distributed File System (HDFS)- The first building block of Hadoop is HDFS, a
Java-based distributed file system which ensures reliable long-term storage and provides
quick access to large amounts of data like Covid-19 data regarding number of infections,
geographical regions, healthcare facilities, diagnosis data, pharmaceutical industry, etc.
HDFS has two nodes- Data Nodes and Name Nodes. HDFS splits the files into blocks and
each block replicates on different nodes on the cluster for easy access .

Yet Another Resource Negotiator (YARN)- YARN is in charge of resource management,
which allows the infrastructure and the programming model to be separated, which

MapReduce used to perform along with its map-reduce tasks. Under YARN, A client
program sends an application request to the Resource manager, which contacts the node
manager asking for a container. The node manager then launches the container to execute
the application. The node managers handle the former tasktracker responsibilities, while the
resource manager, application master, and timeline server (which keeps application history)
share the jobtracker responsibilities from MapReduce.


Apache HIVE- Hive is an open source data warehousing solution built on top of Hadoop. It
is a multi-purpose, scalable data processing engine that allows to run any query on massive
amounts of data stored in HDFS and used for ad hoc data summarising and querying. Hive
allows queries written in HiveQL, a SQL-like language. These queries are turned into
map-reduce tasks that are run on a Hadoop cluster. Hive organises data into tables, offering
a mechanism to tie structure to data stored in HDFS and metadata like table schema, is
stored into a database known as the metastore (Bali, 2016), this way the raw covid-19 data
in the HDFS is structured into tables with Hive.


Apache Spark- With Apache Spark, data streams are separated, tasks are performed 100
times faster than other systems in a few stages, and they can be analysed or transmitted in
real-time to Hadoop applications, systems analysis, Big Data lakes (Riswantini et al., 2021).
Hadoop HDFS can be used with Spark. A Spark programming model is an extension of the
Map-Reduce programming model for a range of operations, faster than MapReduce. Spark
implements in-memory cluster computing, which greatly improves performance and makes it
ideal for machine learning algorithmic that processes same datasets repetitively, interactive
applications, and interactive queries using join and match parallel techniques (Gendy, 2021).
The use of Apache Spark enhances the efficiency to manage massive Covid-19 datasets on
a daily basis (Haafza et al., 2021).

Spark MLlib- MLlib is Spark's distributed machine learning library that targets large-scale
learning settings, and it offers significant benefits through its close integration with Spark,
such as “data parallelism and model parallelism” for storing and analysing data or models.
Being a Spark project, MLlib contains Java, Scala, and Python APIs (Meng et al., 2016).
While MLlib covers the same range of learning categories as Hadoop Mahout, it also adds
regression models that Mahout does not, along with algorithms for topic modelling, frequent
pattern mining, dimensionality reduction, etc. Because it uses in-memory processing, jobs
run much faster than Mahout (Landset et al., 2015).

Sqoop- Sqoop is a tool for transferring Covi-19 data between a RDBMS and HDFS. It pulls
data from Relational Databases like SQL as tuples, which are then transferred as records
and saved as text files then sent to HDFS (Saroha & Sharma, 2019).
Zookeeper & Ambari- Zookeeper records and manages changes in configurations and
delivers a distributed configuration and synchronisation, whereas Apache Ambari controls
and monitors cluster resources, can be readily integrated with other tools and has an
easy-to-use interface (Abidin et al., 2018).

Data from source:
The data is assumed to be retrieved from a source which is RDBMS SQL server. Covid-19
data of a country is regarding number of infections, geographical regions, healthcare
facilities, diagnosis data, etc.
Example Source Data tables:
1. Infections table
Column
Names
Description Data type
Infection Number of infection on daily
basis
Integer
Date Date Date
City Name of the city Varchar
Region Name of the region Varchar
Status Type of zone- Red, Orange
and Green zones
Varchar

2. Healthcare_facilities table
Column
Names
Description Data type
Number of
resources
Number of medical resources
available
Integer
Number of
health staff
Number of health staff
available
Integer
Date Date Date
City Name of the city Varchar

3. Diagnosis table
Column
Names
Description Data type
Type of
symptoms
Type of symptoms patients
experience
Varchar
Number of
Discharged
patients
Number of Discharged
patients on particular date
Integer
Date Date Date
City Name of the city Varchar



![image](https://user-images.githubusercontent.com/120987787/224343165-288bf01c-97ec-4e4d-9179-9b95c0f21bca.png)

Fig 2: Workflow of Covid-19 Monitoring System
Workflow:
First of all, Sqoop retrieves the Covid-19 data from the RDBMS tables of source SQL server
and stores it in the form of text file with headers as specified into Hadoop HDFS (cluster)
using following command which needs connection details, source server and target location,
same for other tables:
![image](https://user-images.githubusercontent.com/120987787/224343330-a180ec6d-0c0b-4274-b0fe-d76f9e83e591.png)


The files can be accessed from HDFS using following command:
![image](https://user-images.githubusercontent.com/120987787/224343354-8869b58a-8f44-41b3-b6ea-ed3431713d71.png)


Once the data is stored in the HDFS, it is accessed by Hive for ETL processing and to
perform the HiveQL querying on the data. HiveQL is similar to standard SQL, but supports
some extensions not found in SQL, along with create table as select and multi-table inserts
and supports various relational, arithmetic, and logical operators and joins (Talend, 2022).
The data in text files with header stored in HDFS is extracted into RDBMS structure by
creating a database, main tables and a final table by extracting useful data from main tables,
which will be used as an input dataset for machine learning tools for prediction.

SQL queries for creating Hive Database and tables:

![image](https://user-images.githubusercontent.com/120987787/224343389-a6bce33d-376f-41a0-b4c4-ff6a6e4fb748.png)

The data from HDFS is loaded into these tables using following commands:
![image](https://user-images.githubusercontent.com/120987787/224343411-7b38e97b-813a-4c9a-9997-08c262f31fed.png)


The next thing is prediction which will be performed using machine learning algorithms
supported by Apache Spark’s MLlib library. Apache Spark provides APIs for working with
huge data sets in a variety of programming languages and abstraction levels, including Java,
Python, Scala, and R (Salloum et al., 2016). Pyspark is a Python API that implements the
machine learning algorithm for covid-19 outbreak prediction by importing the MLlib library,
which is relatively easy to learn and use. It has an API that is both user-friendly and
comprehensive. Compared to Java and Scala, Python has dramatically higher readability,
maintenance, and familiarity, and also has a variety of data visualisation features, which is
difficult to achieve in Scala and Java (Databricks, 2022). The factors such as
no_of_infections, Date, City, Region, no_of_resources, no_of_health_staff,
type_of_symptoms , no_of_patients_discharged are deciding variables and Status (Red,
Orange, Green) is the target variable of prediction.


importing the pyspark and pyspark SQL modules:
![image](https://user-images.githubusercontent.com/120987787/224343522-3ef7de88-6986-407d-a6f1-6047d6bd022f.png)


creating a spark session and enable the Hive support to interact with the hive database:

![image](https://user-images.githubusercontent.com/120987787/224343648-5befdf72-1fcd-4765-8802-d428f0d69670.png)

verifying the databases in hive using pyspark:
![image](https://user-images.githubusercontent.com/120987787/224343691-7acbfb26-b5a6-4da1-9a60-2e02886ff85e.png)![image](https://user-images.githubusercontent.com/120987787/224343730-1ff872eb-6b94-4dc5-9ac4-eb37012e20d3.png)

fetching rows from the table in hive using pyspark and store them in the dataframe:
![image](https://user-images.githubusercontent.com/120987787/224343807-44d9aeaf-cefe-4392-9786-92efd7a8591f.png)


The dataframe is then feeded as input dataset to the machine learning algorithm by
importing Spark’s MLlib library. Prediction with a machine learning algorithm involves steps
such as data preparation, partition, model implementation and model evaluation. The model
is trained using the Decision Tree classification algorithm by setting different required
parameters to predict the status outcome, which will classify the status as Red, Orange and
Green. Red being the region where Covid-19 outbreak is likely to occur. These prediction
results can then be visualised further or can be used to develop a dashboard to monitor
geographical regions. Following is the basic Pyspark code for decision tree classification:

![image](https://user-images.githubusercontent.com/120987787/224343917-cc892a39-8525-4c41-95c7-e356589cc6f1.png)




Use Case 2: Smart Repairing System
![image](https://user-images.githubusercontent.com/120987787/224344949-4e77c8a3-4ed0-4b76-b29f-ae4af19a2c91.png)
Figure 3: Data Architecture of Smart Repairing System

IoT, sensors in cars, and big data are examples of recent technologies that can be used for
monitoring and decision-making (Syafrudin et al., 2018), hence a hadoop based data
infrastructure is built which could automatically report faults in the cars to nearby garages,
having underlying components in the architecture as follows:

Apache Kafka- In the study by Syafrudin et al. (2018) on big data processing of sensor
data, Kafka was used for building real-time applications. It's scalable, fault-tolerant, and has
a high throughput. Using Kafka for manufacturing, transportation, healthcare, and IoT sensor
data has been demonstrated to offer considerable benefits in several studies. When the
volume of data and the number of subscribers increased, the system proved capable of
efficiently processing massive amounts of sensor data. Kafka's implementation is projected
to save cost in terms of infrastructure and deployment.

Spark Streaming- Despite the fact that each car uploads a little stream of data, due to the
high frequency and enormous fleet scale, a large stream is combined (Zhang et al., 2017).
IoT sensors produce data in unstructured/semi-structured format and continuous manner,
which is becoming a difficult problem (Syafrudin et al., 2018). As a result, processing the
stream of massive vehicle data in real-time is a key necessity in this scenario (Zhang et al.,
2017). Spark Streaming, service offered by Spark, is based on micro-batching, a technique
that can be interpreted as simulating real-time processing and simplifies load balancing and
is more resilient to node outages (Landset et al., 2015), hence utilised for the use case.

Apache Spark- The study by Syafrudin et al. (2018) on big data processing of sensor data
showed results that ApacheSpark has higher throughput than Apache Storm when the
system was examined. This module visualises the status of vehicle data collected and
processes data that requires real-time processing using streaming, used for analysis of
large-scale data in real time. Spark supports the processing of data from multiple sources,
including DB, CSV and JSON. Data frames are the “primary processing unit” inside Spark
(Yoo et al., 2020). “DStreams can be converted to DataFrames, Spark SQL can be used to
query streaming data and different Spark libraries can be used together” (Salloum et al.,
2016).

Apache HIVE- Apache Hive, built on top of Hadoop, stepped in when traditional RDBMS
were failing to handle, store, or analyse enormous amounts of data efficiently and scalably
(Loganathan et al., 2014). Hive uses HiveQL, an ANSI SQL extension comparable to
MySQL, to query data stored in HDFS (Landset et al., 2015).

Hadoop Distributed File System (HDFS)- HDFS is intended to store data over several
nodes of commodity hardware (Landset et al., 2015) and is a distributed, fault-tolerant file
system that runs on low-cost hardware (Bali, 2016). HDFS is used to store car sensor results
data created in HIVE RDBMS after analysis and processing owing to its significant features.
YARN- YARN runs efficiently on larger clusters, doubling its capacity to handle jobs and
tasks before hitting bottlenecks. YARN makes Hadoop much more generalised, so
MapReduce can be just one type of YARN application that can be dropped entirely (Landset
et al., 2015). In addition to maximising resource utilisation, it provides an environment for the
execution of an application that promotes distributed processing (Loganathan et al., 2014).


Apache Ambari- The two key functionalities that a data infrastructure must undertake are
monitoring and responding to problems. Regardless of cluster size, Apache Ambari allows
ongoing cluster maintenance, management, and administration. Ambari Alerts stores health
checks and alerts for the services by automatically configuring the specific set of alerts
according to the services installed and controls which alerts are enabled, their thresholds,
and the report output. The Ambari alert system gives great flexibility through the use of alert
groups and multiple notification targets that include EMAIL and SNMP notifications as per
preference (Jain, 2022).

Example Data:
Data from sources:
Sensor Data:
control_unit_id, sensor_id, sensor_status (normal, fault),
driver_location
Driver Data:
vehical_id, driver_contact
Garage Data:
garage_name, garage_address, garage_contact,
garage_email_id



![image](https://user-images.githubusercontent.com/120987787/224344306-af9c2a1d-3700-48af-9557-3025f6496007.png)
Figure 4: Workflow of Smart Repairing System


Workflow:
Before being delivered to the Kafka server, IoT-based sensors generate data in JSON format
(Syafrudin et al., 2018). Kafka is a subscription-based “message distribution system” that
consists of three components: producer, consumer, and topic. Messages sent from
producers to consumers in the Kafka system are routed through the topic of the Kafka broker
(Yoo et al., 2020). Spark Streaming integrates with Kafka consumer API and is similar in
design to the Direct Stream approach. Simple parallelism is provided, along with one-to-one
correspondence between Kafka partitions and Spark partitions, as well as access to offsets
and metadata (Spark 2.2.0 Documentation, 2022). This way the sensor datastreams enter
the system through Kafka and Spark integration. Beside this, Kafka also retrieves Garage
information regarding garage names, address, contact information, email_id, etc in HDFS.
Below is the sample for sensor data in JSON format:
![image](https://user-images.githubusercontent.com/120987787/224344371-f1f6bec5-3972-4057-87f2-f8dbb4904161.png)


Below is the sample for garage data in CSV format:
![image](https://user-images.githubusercontent.com/120987787/224344410-d1fef8ce-663b-46b7-bb25-3a870ae6070b.png)

The sensor data is then delivered to the Apache Spark Data flow engine which performs the
in-memory processing of the data in real-time where the analysis is done to find the faults in
the sensors, identify the driver location and contact, verify the nearby garages as per driver’s
location. All this information obtained after analysis is then stored in the Hive RDBMS tables
to be used as a message if any fault is detected. The nearby garage locations are retrieved
from the data stored in HDFS through Kafka in csv files. Following is the code to create a
spark session and read streaming data:
![image](https://user-images.githubusercontent.com/120987787/224344420-6af5eda3-18d1-4abc-a52f-9c9a7dce7950.png)


Pyspark is used for incoming data loading for the analysis and finding faults, also for reading
the garage data stored in HDFS in csv files. PySpark includes a DAG execution engine that
aids in-memory computation and acyclic data flow, yielding faster speed. PySpark enables
fault tolerance with Spark abstraction-RDD. When it comes to real-time stream processing,
PySpark is renowned and far superior to other languages, which is not achievable with
Hadoop MapReduce (Advantages of PySpark, 2021). Following is the pseudo code for
analysis to find fault, driver location and contact, nearby garages as per driver’s location:

![image](https://user-images.githubusercontent.com/120987787/224344469-85d48bf9-46e7-42a7-91a2-8efcfda49598.png)

Ambari alerts are set to send the message to the nearby garages via email or SNMP
notification alerts preferably if any fault is detected, with the following information in the
message from the data stored in Hive Table:
Vehical_id, driver_contact, sensor_id, sensor_status, driver_location, garage_address,
garage_contact, garage_email_id.
Below is the HQL query to create a messages table in Hive RDBMS:
![image](https://user-images.githubusercontent.com/120987787/224344499-548becd3-2883-42e6-adc7-0e0a313c4e74.png)




