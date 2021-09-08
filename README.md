# Sai Deep Konduri

###### My favorite place is chicago

1. Get on I-35 N in Decatur County from MO-148 N, IA -148 N and IA-2-E
2. Follow I-35 N, I-80 E and I-88 E to W lda B. Wells Dr in Chicago.
    1. Continue on same road for 2hrs.
3. Continue on W lds B. Wells Dr. Drive to S Federal St.


**[Bio](AboutMe.md)**


---

# My Food Recommendations
Top 4 items
| Food | Available Location | Cost to Prepare |
| --- | --- | --- |
| Plain Dal with Mango pickle | Andhra Pradesh, India | 8 - 10$ |
| Sambar | Andhra Pradesh, India | 10 -15$ |
| Clay pot Curd with Onion and buttermilk chilies | Andhra Pradesh, India | 4 - 6$ |
| Tirumala Laddu | Tirupati, India | 1$ |


---

# My Quotes

 > Tomorrow is another name for Belief

 > Hope is good thing maybe the best of things

 # Choosen Algorithm - Minimum spanning tree - Prim's algorithm

 > Prim's algorithm (also known as Jarník's algorithm) is a greedy algorithm that finds a minimum spanning tree for a weighted undirected graph. This means it finds a subset of the edges that forms a tree that includes every vertex, where the total weight of all the edges in the tree is minimized. The algorithm operates by building this tree one vertex at a time, from an arbitrary starting vertex, at each step adding the cheapest possible connection from the tree to another vertex.


[source](https://en.wikipedia.org/wiki/Prim%27s_algorithm)

```
int n;
vector<vector<int>> adj; // adjacency matrix of graph
const int INF = 1000000000; // weight INF means there is no edge

struct Edge {
    int w = INF, to = -1;
};

void prim() {
    int total_weight = 0;
    vector<bool> selected(n, false);
    vector<Edge> min_e(n);
    min_e[0].w = 0;

    for (int i=0; i<n; ++i) {
        int v = -1;
        for (int j = 0; j < n; ++j) {
            if (!selected[j] && (v == -1 || min_e[j].w < min_e[v].w))
                v = j;
        }

        if (min_e[v].w == INF) {
            cout << "No MST!" << endl;
            exit(0);
        }

        selected[v] = true;
        total_weight += min_e[v].w;
        if (min_e[v].to != -1)
            cout << v << " " << min_e[v].to << endl;

        for (int to = 0; to < n; ++to) {
            if (adj[v][to] < min_e[to].w)
                min_e[to] = {adj[v][to], v};
        }
    }

    cout << total_weight << endl;
}

```
[Source Code](https://cp-algorithms.com/graph/mst_prim.html)