# ChainKeeper-Analytics
## Abstract <br>
Most of the bitcoin transaction analysis machine learning models are heavily dependent on the
labeled data sets. By looking at each labeled address researchers have worked to gather the
related features form other addresses. We believe this method grabs so many biases. But luckily we can not prove these models are totally wrong or totally correct because of the pseudo-anonymity of the bitcoin. We have to use another labeled address to test the models. So most of the time training and testing labeled data coming from one single source, We have no grantee or transparency of how these sources went through the pseudo-anonymity of the bitcoin and identified the type of this address (Most of the time these observations depend on graph inference study using identity relived address or looking to the address in well-known wallets). 

We believe bitcoin transactions grabs so many patterns rather we can grab from the above studies, and each pattern is different. Studying the entire blockchain using an identity relived address then understand the behaviors of that type of addresses is not the best way, It will only relive 5-10% (tentative value) qualities of the cluster (address type), so most of the qualities of that address class (Cluster or address type) is hidden inside the blockchain. And most importantly these qualities (we may say features in machine learning) are so volatile and they heavily depend on social trends. In order to understand the cluster type of a particular address, capturing, those dynamic features is the most cumbersome process. Studying about behaviors of the address types mainly depends on a graph, we can transform the entire bitcoin database to a graph and study the graph part by part and capture some common qualities on each strongly connected component. 

Then we can project some well-known addresses from different sources into the bitcoin graph and check the projection density of these labeled addresses on each connected component. This method also very naive because of the labeling process of the well-known address and bitcoin graph may have two different time states. Since the bitcoin graph is dynamic we have to have much robust and real-time label production, in this way the entire process will depend on the state of update level of known labeled address.

We believe in order to overcome this highly dynamic behaviour of bitcoin graph and understand the real nature of the bitcoin graph, we have to go a little step further than classical features and labeling training. This approach based on a transaction property graph [Table 1] of the entire blockchain and adding super vertices using (https://www.walletexplorer.com/). And follow the process of above paragraph. In order to keep the system up to date, the deployment of this model should integrate into a data pipeline.<br> <br>
![Untitled Diagram (2)](https://user-images.githubusercontent.com/20130001/90658285-06158480-e261-11ea-9918-3dd3e90b1dfa.png) <br> <br>
## Data gathering crawlers <br>
To set up crawlers, first set up apache airflow (optional these crawlers can run as standalone python executable with Cron jobs) 
#### Set up Apache Airflow
```
export AIRFLOW_HOME=~/airflow
pip install apache-airflow
airflow initdb
airflow webserver -p 8080
airflow scheduler
```
#### Add new crawlers <br>
Edit ```./airflow/dag1.py``` and load the dag to AirFlow 
## Data analysis environment <br>
This project contains a couple of docker environments to easily set up BlockSci blockchain analysis tool with Jupiter notebook and Docker environment for setting up TensorFlow, Jupiter notebook with stellar graph
#### Docker build <br>
```
cd ChainKeeper-Analytics/docker/BlockSci V0.7 Docker/
docker build -t <TAG> .

cd ChainKeeper-Analytics/docker/Anaconda-Tensorflow-Stellargraph Docker/
docker build -t <TAG> .
```
#### View some sample data that we collected <br>
view some sample data at ``` ChainKeeper-Analytics/data/ ```
### Analysis
Check data analysis and modeling the collected data to a graph ``` ChainKeeper-Analytics/notebooks/ ```
