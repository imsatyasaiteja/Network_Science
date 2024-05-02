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

<p align="center">
<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/92bbe438-8c5a-42ef-85b9-09468b068bcb" width="1000" alt="node_data">
</p>

>### Degree Distribution
<p align="center">
<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/ed07f27b-d888-4474-851d-f2d5df3f0827" width="1000" alt="degree_dist">
</p>

>### Power Law Distribution and Scale Free Property
* Some real-world networks exhibit a power-law degree distribution, meaning that a small number of nodes have very high degrees, while the majority have relatively low degrees.
* The power-law distribution is given by $(p_k \sim k^{-\alpha})$ and the ${\alpha}$ is its degree exponent.
* The power-law exponent ${\alpha}$ is a parameter that characterizes the shape of the power-law distribution. A smaller α indicates a steeper decline in the distribution.

<p align="center">
<img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/10846a67-4b10-461f-95fa-4c0b3d17a34a" width="500" alt="power_law">
</p>

>### Hubs & Betweenness Centrality
* Network hubs, identified by their high node degree centrality, play a key role in influencing connectivity and information flow.
* You can observe the top 50 hubs, significant bus stops in the graph below.
* Hubs, represented by red nodes, serve as pivotal points with numerous connections. 
* Their significance lies in their ability to link to various routes and trips, making them central in our road network. 
* The arrows between them symbolize bus routes, establishing connections between stops.
* These hubs play a critical role in Delhi's road network, ensuring seamless connectivity and operational efficiency.

<p align="center">
  <img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/33cdf89a-3077-4a06-99e2-4574645cc704" width="500" alt="hubs">
</p>

* Betweenness centrality measures how important a node is in helping information or influence move around a network.
* Nodes with high betweenness often act as important bridges or bottlenecks, controlling how information flows between different
parts of the network
* The figure below illustrates the top 50 nodes with high betweenness centrality.
* To compute this, we first calculate edge weights based on latitude and longitude coordinates using the Haversian formula from the geodesic library, yielding distances in kilometers.
* These distance values are then assigned to the edges' distance attribute, serving as edge weights in our graph.
* Utilizing the ‘betweenness_centrality’ function in the ‘networkx’ library, we identify nodes with high betweenness centrality.
* The Haversian formula internally employs the Brandes algorithm to calculate all shortest paths for each pair of nodes.

<p align="center">
  <img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/6c56746e-eebb-483d-9717-8648facfdc3c" width="500" alt="betweenness">
</p>

## Disruption Scenarios
* We simulate disruptions, such as road closures, malignant accidents, natural disasters and assess their impact on network connectivity.
* Visualize the network both before and after the disruption to clearly illustrate the resulting changes.

>### Road Closure
* Road closures, stemming from construction, maintenance, or infrastructure projects, constitute prolonged disruptions lasting from days to years.
* To simulate such disruptions, we will selectively remove edges associated with nodes in the network.

<p align="center">
  <img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/d14a6258-1d88-4279-b73d-a7c4b5ddf184" width="500" alt="rc_comparison">
</p>

>### Malignant Accidents
* Road accidents can temporarily close specific routes, leading to the temporary cancellation of trips to stops along the affected route.
* To simulate such disruptions, we remove trips associated with the stops connecting the impacted route.

<p align="center">
  <img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/87bda63e-8be0-4ef4-8d96-c9281b406868" width="500" alt="ma_comparison">
</p>

>### Natural disasters
* Natural disasters exhibit varying durations and impacts on road networks.
* Brief disruptions, such as heavy rains, lead to temporary delays in trips. In contrast, prolonged events like floods can endure for days, causing road closures, rendering certain stops inaccessible, and necessitating the cancellation of all trips along affected routes.
* To simulate such disruptions, we remove nodes, rendering corresponding locations inaccessible.

<p align="center">
  <img src="https://github.com/imsatyasaiteja/Network_Science/assets/85508314/74fc9809-55f0-44b5-bfb8-090bf96168ca" width="500" alt="rc_comparison">
</p>

## Robustness Metrics
* Robustness refers to the ability of a network to maintain its structural and functional integrity in the face of perturbations, disruptions, or attacks.
* Specifically, degree-based robustness metrics provide insights into how well a network can withstand the removal of nodes or edges based on their degrees.
* We understand it through the _Average degree_ and _Standard deviation of degree_ metrics

>### Average degree
* The average degree of a network is calculated by summing the degrees of all nodes and dividing by the total number of nodes.
* A higher average degree indicates a denser network, suggesting stronger connectivity among nodes.
* In terms of robustness, networks with higher average degrees tend to be more resilient to random failures.

>### Standard deviation of degree
* The standard deviation of degree measures the degree variability among nodes in the network.
* A higher standard deviation suggests a more heterogeneous network where nodes have diverse degrees.
* In terms of robustness, networks with higher degree heterogeneity may exhibit a _scale-free structure_, making them more resistant to targeted attacks on highly connected nodes.

## Recovery Post disruptions
* We applied a rerouting algorithm by finding the shortest paths between the top nodes in the original and disrupted networks.
* Specifically, it calculates the shortest paths from the highest-degree nodes in the original network to those in the disrupted network.
* Using the nx.shortest_path function the most efficient path between two nodes in a graph was determined.
* It internally uses Dijkstra's algorithm, considering the weighted distance edges of the road network to calculate shortest paths.

## Key Findings
* The degree distribution analysis indicates a power-law distribution with an alpha value of 3.08, highlighting the scale-free property of the road network.
* The average degree values for these scenarios are 4.11406, 4.10651, and 4.10982 along with their corresponding standard deviations 2.67282, 2.12648, and 2.66600 provide a measure of the impact on network connectivity.
* These metrics serve as key indicators of the network's robustness in the face of various disruptions.
* For further understanding, kindly refer to the project report uploaded above.

## References

1) Barabási, A. L. (2002). “How Everything Is Connected to Everything Else and What It Means for
Business, Science, and Everyday Life.” Plume. ISBN: 978-0452284395.

2) Newman, M. E. J. (2018). “Networks: An Introduction.” Oxford University Press. ISBN:
978-0198805090.

3) GitHub Repository - Road Network Robustness:
- Author: Tamene Bekele
- Title: “Road-Network-Robustness”
- Repo URL: [Road Network Robustness](https://github.com/tamene21/Road-Network-Robustness)

4) Gupta, R. “Evaluation of Accident Black Spots on Roads Using Geographical Information Systems.”
- Author: Rajiv Gupta
- Affiliation: Birla Institute of Technology and Science Pilani

5) Ganin, A. A., & Kitsak, M. “Resilience and efficiency in transportation networks.”
- Author: Alexander A.Ganin , Maksim Kitsak

6) Ientile, S., Schmidt, F., Chevalier, C., & Orchesi, A. “Road network analysis for risk and resilience assessment framework of road infrastructure systems.”
- Author: Silvia Ientile, Fransika Schimdt , Christophe Chevalier , Andre Orchesi

7) Lu, Y., & Zhang, Z. “Resilience of urban road network to malignant traffic accidents.”
- Author: Yiding lu, Zhan Zhang
