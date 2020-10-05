# Problem


# Solution
This problem is basically finding maximum path from head to end of graph from a directed graph.  
- Create a weighted graph in adjacency form in which the key is the manager, and children are their (employee, informtime) 
- Do a DFS. If an employee is at the bottom, return 0 
- If a manager has n employees, for each employee, we return the maximum path starting from that employee
- The solution: The time for a manager = max(manager's employees) + informTime[manager] 

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
        
