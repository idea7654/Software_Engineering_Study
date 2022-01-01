# NEAT : NeuroEvolution of Augmenting Topologies

### Encoding - Row data로부터 Feature Vector만을 추출

- direct Encoding - straightforward to understand
- Input and output nodes are not evolved in the node gene list
- Hidden nodes can be added or removed.
- Connection nodes specify **where a connection comes into and out of**, **the weight of such connection**, **whether or not the connection is enabled**, and an **innovation number**

### Mutation

- can either mutate existing connections or can add new structure to a network
- if a new connection is added between a start and end node, it is randomly assigned a weight
- if a new node is added, it is placed between two nodes that are already connected
- The previous connection is disabled(though still present in the genome)
- The previous start node is linked to the new node with the weight of the old connection and the new node is linked to the previous and node with a weight of 1
- Mutation은 Link, Trait에서 발생

### Competing Conventions

- 두 neural networks의 게놈을 넘나들면 끔찍한 mutated와 non-functional이 일어날 수 있는 문제
- if two networks are dependent on central nodes that both get recombined out of the network, we have an issue
- Genomes can be of different size
- homology - alignment of chromosomes(염색체) based on matching genes for a specific trait
- crossover can happen with much less chance of error than if chromosomes were blindly mixed together
- By marking new evolutions with a historical number, when it comes time to crossover two individuals, this can be done with much less chance of creating individuals that are non-functional.
- historical number - ?
- individuals - ?
- By marking new evolutions with a historical number, when it comes time to crossover two individuals, this can be done with it comes time to crossover two individuals, this can be done with much less chance of creating individuals that are non-functional.
- Each gene can be aligned and (potentially) crossed-over
- Each time a new node or new type of connection occurs, a historical marking is assigned, allowing easy alignment when it comes to breed two of our individuals(개체?).

### Speciation

- protect new structures and allow them to optimize before we eliminate them from the population entirely
- Simply splits up the population into several species based on the similarity of topology and connections
- NEAT uses historical markings in its encoding, this becomes much easier to measure
- individuals in a population only have to compete with other individuals within that species
- 문제 - 가중치의 최적화가 일어나기 전에 새로운 커넥션이나 노드가 추가될 경우 낮은 performance를 보일 수 있음
- 해결 - Speciation사용, Speciation은 단순히 topology와 connection의 유사성에 기초하여 개채군을 여러 종으로 나눈 것으로, Encoding에 historical marking을 사용하여 측정이 쉬움. 한 개체군의 개체들이 해당 species내의 다른 개체들과만 경쟁하면 됨. 이를 통해 새로운 구조가 탐색되기 전에 제거될 가능성이 없이 최적화될 수 있음

### Minimal Structure

- A large goal of the NEAT was to create a framework for evolving networks that allowed for minimal networks to be evolved
- 최소한의 node와 connection으로 시작하는 알고리즘을 구축해 useful하고 necessary하다고 판단될 경우만 시간에 따라 complexity가 진화하도록 하는 것
- sets up their algorithm to evolve minimal networks by starting all networks with no hidden nodes
- Each individual in the initial population is simply input nodes, output nodes, and a series of connection genes between them
