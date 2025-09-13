		
## Graph

###### - Directed Graph
![[Pasted image 20250628091343.png]]

###### - Undirected Graph
![[Pasted image 20250628091401.png]]

###### Vertex are considered as nodes of values
###### Edges are considered as Lines that connects the two vertex

### Creation 

Graph can be created using the Adjacent Matrix and Adjacent List . Also Using Hashmap

###### Adjacent matrix O(V^2)
![[Pasted image 20250628091343.png]]

Matrix 

![[Screenshot 2025-06-28 092914.png|300]]

CODE:(DFS TRAVERAL)
https://yesamitsingh.hashnode.dev/matrix


```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int V=5;
        int[][] edges={
                        { 0 , 1 },
                        { 0 , 2 },
                        { 1 , 2 },
                        { 2 , 3 },
                        { 2 , 4 }
                        
                      };
        
        int[][] adjMat=new int[V][V];
        
        for(int[] edge:edges){
            int u=edge[0];
            int v=edge[1];
            adjMat[u][v]=1;
            adjMat[v][u]=1;
        }
        
        // for(int i=0;i<V;i++){
        //     for(int j=0;j<V;j++){
        //         System.out.print(adjMat[i][j]+" ");
        //     }
        //     System.out.println();
        // }
        
        boolean[] visited=new boolean[V];
        bfs(0,adjMat,visited,V);
        
        visited=new boolean[V];
        dfs(0,adjMat,visited,V);
        
    }
    
    public static void bfs(int start,int[][] adjMat,boolean[] visited,int V){
        Queue<Integer> q=new LinkedList<>();
        q.offer(start);
        visited[start]=true;
        
        while(!q.isEmpty()){
            int node=q.poll();
            System.out.print(node+" ");
            
            for(int neighbour=0;neighbour<V;neighbour++){
                if(adjMat[node][neighbour]==1 && !visited[neighbour]){
                    q.offer(neighbour);
                    visited[neighbour]=true;
                }
            }
        }
        System.out.println();
    }
    
    public static void dfs(int node,int[][] adjMat,boolean[] visited,int V){
        visited[node]=true;
        System.out.print(node+" ");
        
        for(int neighbour=0;neighbour<V;neighbour++){
            if(adjMat[node][neighbour]==1 && !visited[neighbour])
                dfs(neighbour,adjMat,visited,V);
        }
    }
}
```

#### Time Complexity 

Finding the Node - O(1)
Deleting the Node - O(1)
Find or Delete using DFS - O(n)

###### Adjacency List - O(V+E)
![[Pasted image 20250628095759.png|500]]

#### Time Complexity 

Finding the Node - O(Out Degree)
Deleting the Node - O(Out Degree)
Find or Delete using DFS - O(V+E)

CODE
```java
import java.util.*;
public class Main
{
	public static void main(String[] args) {
		int V = 5;
        int[][] edges = {
            {0, 1},
            {0, 2},
            {2, 3},
            {2, 4}
        };
        
        Map<Integer,List<Integer>> map=new HashMap<>();
        for(int[] edge:edges)
        {
            int u=edge[0];
            int v=edge[1];
            map.put(u,map.getOrDefault(u,new ArrayList<>()));
            map.put(v,map.getOrDefault(v,new ArrayList<>()));
            map.get(u).add(v);
            map.get(v).add(u);
        }
        System.out.print(map);
	}
}
```


CODE:(DFS TRAVERAL)
https://yesamitsingh.hashnode.dev/list-graph
### Directed cyclic Graph

This a graph which has direction also it contains the cycle in the graph

![[Pasted image 20250628093404.png|200]]

#### LEETCODE

##### 1971 . Find If Path Exists in graph
##### 797 . All Path from source to Destination
##### 547 . Number of provinces
##### 2316 . Count Unreachable pairs of nodes in undirected graph
##### Detect Cycle in the undirected graph(gfg)
##### Detect Cycle in the directed graph(gfg)
Bfs of a graph
Shortest path in an unweighted graph(code ninja)
Word ladder
Bus routes
##### Rotting orange
##### 463.Island Perimeter
##### 695.Max Area of Island
##### 200.No of Island
###### 2658 . Maximum Number of Fish in a Grid

Topological Sort(gfg) - DFS , BFS







