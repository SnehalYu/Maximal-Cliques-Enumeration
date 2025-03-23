# DAA_Assignment


## Project Overview
This project implements and compares three maximal clique enumeration algorithms using C/C++. The algorithms are executed on three large-scale graph datasets, and the results are analyzed based on execution time, clique sizes, and frequency distributions.

## Clique Detection Algorithm (Chiba & Nishizeki, 1985)

This code implements an efficient algorithm for detecting all cliques in a given graph, leveraging the arboricity of the graph to improve performance. The algorithm runs in O(α(G)·m) time per clique, where:
m = Number of edges in the graph
α(G) = Arboricity (minimum number of edge-disjoint spanning forests)

The algorithm follows a vertex ordering and edge-searching strategy:
- Sorts vertices in non-decreasing order of degree.
- Iteratively searches for cliques using adjacency lists.
- Avoids redundant computations by systematically deleting processed vertices.

Complexity Analysis: 
- Uses O(α(G)·m) time per clique.
- Requires O(m) space.
- Efficient for sparse graphs, as α(G) is usually small.

Requirements
G++ Compiler Version 6.3.0
- This code is known to work with G++ 6.3.0. Compatibility with later versions may require minor modifications.

Compile and Run
g++ -O3 filename.cpp -o cliques 
./cliques

## Maximal Clique Enumeration in Sparse Graphs (Eppstein et al., 2010)

This project implements an optimized version of the Bron–Kerbosch algorithm for listing all maximal cliques in a graph. The algorithm is parameterized by degeneracy (d), a sparsity measure closely related to arboricity, and achieves a near-optimal worst-case running time of O(d·n³ᵈ/³).

Benefits of using this algorithm:
- Optimized for sparse graphs: Works well on real-world graphs with low degeneracy.
- Near-optimal performance: Runs in O(d·n³ᵈ/³) time, which matches the theoretical worst-case output size.
- Uses degeneracy ordering: Reduces unnecessary recursive calls, improving efficiency.

This code :
- Computes a degeneracy ordering of the input graph.
- Modifies the Bron–Kerbosch algorithm:
	- Uses non-pivoting recursion at the top level (outer loop).
	- Uses pivoting strategy (Tomita et al., 2006) in inner recursion levels.
- Reduces the number of recursive calls, making it efficient for large sparse graphs.

Complexity Analysis :
Time Complexity	O(d·n³ᵈ/³)
Space Complexity	O(m)
d = degeneracy (smallest number such that every subgraph has a vertex of degree ≤ d).
n = number of vertices, m = number of edges.
The number of maximal cliques in the worst case is Θ((n-d)³ᵈ/³).

Compile and run : 
g++ -O3 filename.cpp -o cliques 
./cliques

## Maximal Clique Enumeration (Tomita et al., 2006)

This project implements the Tomita-Tanaka-Takahashi (TTT) algorithm, a depth-first search (DFS) approach for efficiently listing all maximal cliques in a graph. The algorithm is an improvement over the Bron–Kerbosch algorithm, incorporating:
- Tree-like output representation to save space.
- Pruning techniques to reduce unnecessary recursion.
- Worst-case optimal complexity: O(3ⁿ/³), which matches the theoretical maximum number of cliques.

1. DFS-based clique expansion
	- Expands cliques recursively by searching neighbors.

2. Two pruning techniques
	- Processed set (FINI): Avoids redundant computations.
	- Pivot selection: Ensures fewer recursive calls.

3. Tree-structured output representation
	- Reduces memory usage compared to direct clique listing

Complexity Analysis
Time Complexity : O(3ⁿ/³)
Space Complexity	 : O(n²)
n = number of vertices
m = number of edges
The number of maximal cliques in the worst case is Θ(3ⁿ/³) (Moon-Moser bound).

Compile and run :
g++ -O3 filename.c -o cliques 
./cliques

## Comparisions : 
Chiba & Nishizeki (1985)	: O(d²·n) per clique : Uses arboricity, slower for high-degree graphs.
Tomita et al. (2006) : O(3ⁿ/³) : Optimal for general graphs but lacks degeneracy optimization.
ELS Implementation : O(d·n³ᵈ/³) : Best for sparse graphs with low degeneracy.

## Datasets
We use three real-world graph datasets

Email-Enron Network
AS-Skitter Internet Network
Wikipedia Vote Network
Details on preparing the three datasets for maximal clique enumeration:

Email-Enron Network
Description: This dataset represents the email communication network within Enron. It contains about 36,692 nodes (email addresses) and 183,831 edges (email communications). Preparation Steps: Download: Obtain the dataset from https://snap.stanford.edu/data/email-Enron.html.

Format: The dataset is provided in a text file (email-Enron.txt.gz), which needs to be decompressed.

Conversion: If necessary, convert the data into a suitable format for your algorithms (e.g., adjacency list or matrix).

Cleaning: Ensure that the graph is undirected since the dataset represents undirected communication.

AS-Skitter Internet Network
Description: This dataset is an internet topology graph derived from traceroutes. It consists of approximately 1.7 million nodes and 11 million edges. Preparation Steps:

Download: Get the dataset from https://snap.stanford.edu/data/as-Skitter.html.

Format: The dataset is available as as-skitter.txt.gz, which needs to be decompressed.

Conversion: Convert the data into a suitable format for your algorithms.

Cleaning: This dataset is already in a form suitable for graph analysis, but ensure it is undirected if necessary.

Wikipedia Vote Network
Description: This dataset represents the voting network among Wikipedia users. It contains about 7,115 nodes and 103,689 edges. Preparation Steps:

Download: Obtain the dataset from https://snap.stanford.edu/data/wiki-Vote.html.

Format: The dataset is provided as Wiki-Vote.txt.gz, which needs to be decompressed.

Conversion: Convert the data into a suitable format for your algorithms.

Cleaning: Since this dataset is directed, you may need to convert it to an undirected graph depending on your algorithm requirements.

Execution Instructions
For .cpp files g++ -O3 filename.cpp -o cliques ./cliques

Upload the input dataset .txt file in the same directory as the files and run using ./cliques

We executed our codes on macOS, where Clang is the default compiler, providing support for C++17. Additionally, the Chiba Code was compiled using g++ version 6.3.0.

Individual Contributions
-Harsh Bavishi ->Chiba Algorithm Implementation 
-Aiman ->ELS Algorithm Implementation 
-Snehal Yutika ->tomitaO6cliques Algorithm Implementation 
-Mustafa Poonawala ->ReadMe 
-Sanchit Arora -> Report & Documentation

