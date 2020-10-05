# Problem


# Solution
This problem is basically finding maximum path from head to end of graph from a directed graph.  

```python
class Solution(object):
    def buildGraph(self, manager, informTime):
        graph = {}
        for i, manager in enumerate(manager):
            if manager not in graph:
                graph[manager] = [[i, informTime[manager]]]
            else:
                graph[manager].append([i, informTime[manager]])
        return graph 
    
    def dfs(self, node, graph):
        if node not in graph:
            return 0
        else:
            max_time = 0 
            for (employee, time) in graph[node]:
                max_time = max(max_time, time + self.dfs(employee, graph))
            return max_time
       
    def numOfMinutes(self, n, headID, manager, informTime):
        graph = self.buildGraph(manager, informTime)
        time = self.dfs(headID, graph)
        return time
   ```     
        
