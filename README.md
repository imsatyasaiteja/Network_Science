# Resilience of Delhi Road Networks to Traffic Disruptions

>### Problem Statement
* Road networks are complex systems that are essential for movement of people and goods.
* They are also highly interconnected, making them vulnerable to disruptions caused by accidents, natural disasters, or infrastructure failures.
* These disruptions can have a significant impact on the economy and society, and can lead to many problems.

>### Objective of Project
* The objective of this project is to examine the Resilience of road networks to traffic disruptions from a network science perspective.
* This will involve analyzing the network’s structure and investigating strategies for improving the network’s robustness.

>### Background
* Network science is a field of study that examines the structure and function of complex networks, with Road networks being a prime example.
*   This knowledge allows us to assess the resilience of Road networks, referring to their ability to maintain connectivity and function at an acceptable level despite disruptions.

>### Outcome
* The outcome of this project will be a better understanding of the network science factors that contribute to the resilience of road networks.
* This knowledge can be used to develop strategies for improving the resilience of existing networks, and to design new Road networks that are more resilient to disruptions.

## Dataset
* Static dataset of the Delhi road network (in GTFS format) has been obtained from [Open Transit Data - Delhi Website](https://otd.delhi.gov.in/)

## Network Analysis
* We've performed network analysis by utilizing the _networkx_ library in python
* Initially we preprocessed the data and obtained only useful attributes. With the help of this refined data, we constructed a directed graph. In this graph, nodes symbolize stops and edges represent the connecting routes.
* Subsequently, we endowed the nodes with various attributes, including stop ID, stop name, latitude, longitude, in-degree, out-degree, and overall degree. The degree of each node corresponds to the cumulative number of trips associated with the stop.
* Furthermore, the edges were enriched with attributes such as distance, along with a dictionary encapsulating route IDs and trip IDs.

>### Degree Distribution
<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/ed07f27b-d888-4474-851d-f2d5df3f0827" width="600" alt="degree_dist">

>### Power Law Distribution and Scale Free Property
* Some real-world networks exhibit a power-law degree distribution, meaning that a small number of nodes have very high degrees, while the majority have relatively low degrees.
* The power-law distribution is given by $(p_k \sim k^{-\alpha})$ and the ${\alpha}$ is its degree exponent.
* The power-law exponent ${\alpha}$ is a parameter that characterizes the shape of the power-law distribution. A smaller α indicates a steeper decline in the distribution.

<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/10846a67-4b10-461f-95fa-4c0b3d17a34a" width="300" alt="power_law">

>### Hubs & Betweenness Centrality
* Node degree centrality is a measure of the importance of a node in a network based on its degree, i.e., the number of edges connected to it.
* Hubs in a network refer to nodes that have a significantly higher node degree centrality compared to other nodes. 
* They play a crucial role in maintaining connectivity and influencing the flow of information.
* The concept of hubs can be related to the **power-law distribution** by considering nodes with high degrees.
* The centrality of a node i in a network can be represented as: $$C_i = \frac{\text{{Degree of Node }} i}{\text{{Maximum Degree in the Network}}}$$
* This provides a normalized measure of how central a node is based on its degree.
* Betweenness centrality is a measure of a node's centrality in a network based on its role in facilitating the flow of information or influence between other nodes.
* Nodes with high betweenness centrality have a significant influence on the communication or interaction between other nodes in the network.
* Betweenness centrality is calculated by determining the number of shortest paths that pass through a node, relative to the total number of shortest paths in the network.
* Nodes with high betweenness centrality often act as bridges or bottlenecks in the network, as they control the flow of information between different parts of the network.
<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/33cdf89a-3077-4a06-99e2-4574645cc704" width="300" alt="hubs">
<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/6c56746e-eebb-483d-9717-8648facfdc3c" width="300" alt="betweenness">

## Disruption Scenarios

## Robustness Metrics

## Recovery Strategies

## Credits


## References
