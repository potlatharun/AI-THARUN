import heapq
def A_star_search(graph,start,goal,heuristic ):
    open_list = []
    heapq.heappush(open_list,(0+ heuristic[start],start))
    g_costs={start: 0}
    parents ={start: None}
    while open_list:
        current_f, current_node= heapq.heappop(open_list)
        if current_node==goal:
           path = []
           while current_node:
               path.append(current_node)
               current_node = parents[current_node]
           return path[::-1]
        for neighbor, cost in graph[current_node].items():
            tentative_g = g_costs[current_node]+cost
            if (neighbor not in g_costs) or (tentative_g < g_costs[neighbor]):
                g_costs[neighbor]= tentative_g 
                f_cost = tentative_g + heuristic[neighbor]
                heapq.heappush(open_list, (f_cost, neighbor))
                parents[neighbor]=current_node
    return None
graph ={
        'A':{'B': 1, 'C': 4},
        'B':{'A': 1, 'D': 2, 'E': 5 },
        'C':{'A': 4, 'F': 1},
        'D':{'B': 2, 'G': 2},
        'E':{'B': 5},
        'F':{'C': 1, 'G': 3},
        'G':{'D': 2, 'F': 3}}
heuristic = {
    'A': 6, 'B': 4,'C': 4, 'D': 3, 'E': 2, 'F': 2, 'G': 0}
start= 'A'
goal = 'G'
path = A_star_search(graph, start, goal,heuristic)
print("path: ",path)
cost = sum(graph[path[i]][path[i+1]]for i in range(len(path)-1))
print(f"Total Cost: {cost}")
