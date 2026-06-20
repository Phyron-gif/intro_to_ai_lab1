# intro_to_ai_lab1
REFLECTION QUESTIONS

15.1 Problem Formulation
1. The state in this lab is every location the drone finds itself in.

2. An action is decision taken by the drone for a given input or precept.

3. The result function is more like the transition model function that that shows the drone potential nodes to explore or routes to take.

4. This is because the problem definition needs more analysis than the search algorithm that works based on what the problem is.

15.2 BFS

1. This is because BFS searches all neighboring(sibling nodes) before moving to child nodes. in this case it would have to search the earliest nodes in the frontier before the former.

2. This is because it spreads through out the states and given it a high chance of meeeting the goal in less steps.

3. The reached serves as storage for nodes that have already been explored. this is to avoid redundancy or the drone moving in cycles.

15.3 DFS

1. This is because DFS searches all child node before moving to sibling nodes. this causes it to search deeper thus it would search the last child node in the frontier to the earliest sibling node in the frontier.
in this case it would have to search the earliest nodes in the frontier before the earliest.

2. No. this is because DFS will always go as deep as possible without comparing the neighboring alternatives in reaching the goal state. the only time it can guarantee the shortest path is when the goal state is the first child node or the initial state.

3. if no reached data structire and memory management is used.

4.  When it reaches a solution at maximum depth m in the last path. this is because it takes O(b^m ) time where b is maximum number of available actions.

15.4 DLS

1. It misses its goal

2. cutoff is a predefined maximum depth limit imposed on the search to reduced infinite state spaces.

3. DLS has a limit of nodes that it can eplore to fine the goal wheras DFS doesnot have any depth limit.

4. This is to avoid agent moving in cycles that is infinite looping.

15.5 IDS

1. This is to acheive DFS'S  good memory footprint, avoid infinite cycles and to preserve  the optimality guaranty of BFS.

2. This is because IDS increases on the limit of DLS that is where it stops IDS continues to the next limit to get the goal.

3. This is because even though it uses the BFS idea, the number of actions in the longext path without loops is is than the the smallest depth it would go for an optimal solution.

4. he upper tree levels would be re-explored multiples causing redundancy.

15.6 Real-World Drone Context
1. when it has less obstacles
2. i would use BFS. because it is optimal when all is uniform and searches neighboring nodes first which mean it explores the search tree level by level, so it is guarantee to find the goal at the shallowest possible depth it exist at.

Which algorithm would you choose if you want to limit how deep the drone is allowed to search? Explain.
3. Depth limited search. this is because we are not focused on whether the drone reaches the goal all not but whether its able to searc for the goal up to a particular limit, ehich is what depth limited search does.
What limitations does this grid model have compared with real drone navigation?

4. in this grid the eveironment is full known whearas in real drone navigation the environment is not always fully known since we can have infinite number of state spaces. 
The grid moves the drone in fixed steps between cells, wheras n real simulations drone moves through continuous 3D space.



PART B REFLECTION QUESTIONS

16.1 Heuristic Functions
1. h(n) estimates the cost of reaching the goal state from current node. it knowledge comes from the infromed searcch algorithms like the greedy best search and A* star search.

2. it removes the obstacle or wall constraint assuming that the grid is freely traversable.
 
 3. The manhattan distance dominates the euclidean distance. this domination predicts that fewer nodes will be expanded under an A* search using the manhattan distance and this will cause the search to be more efficient towards its goal.

4. This is because as long as every terrain costis > or equal to 1, the true path cost can only be eqyal to or greater than the manhattan distance, so it never overestimates. if the cost were to be 0.5 it migth overstimate the true cost breaking admissibility.


16.2 Greedy Best-First Search

1. The idea of greedy search is that it only cares about nodes that takes you closer to the goal that is the heuristic function is just h(n) ignoring the accumulated cost g(n) of traversing.
since it doesnot take into consideration g(n), it can run into expensive(turbulence) that looks closer to the goal.


2. This is because in real life cost matters and even though greedy might expand fewer nodes it might acqire higher cost than other algorithms which doesnot count as a quality solution even though it is efficient.


3. Greedy expanded fewer nodes than A* on some maps. Why is that not enough to call it the better algorithm?
Describe a drone mission where Greedy's behaviour would actually be acceptable.

3. A drone required to deliver in emergency health situation like asthmatic attacked patients.

16.3  A* Search

1. This mean the path taken by drone highly depends on path from start position to end postion.

2. A* Search uses a priority queque so when node is poped it has the lowest cost path than when it is generated. an early goal test may lead too expensive nodes exploration, whereas less expensive nodes could be explored later on.

3. because we need to associate each node is mapped to a cost

4. UCS expanded 52 nodes wheras A* expanded 18 nodes, both used an same optimal however the heuristic function for A*star was more effecient causing it to not explore unneccesary nodes before the goal node.



16.4 Admissibility and Consistency

1. Admissibility in terms of heuristic would be when the heuristic doesnot overestimate the true remaining cost. A consistent heuristic is one that obeys the triangle inequality that is the cost to the gaol is never greater than the cost of moving to a neighbor node and that of its estimated cost o the goal.consitency implies admissibility.

2. it shows that a A* search is faster

3. yes because movement is per step and each step cost is uniform.

    
16.5 Weighted A* and Trade-offs

1. W determines the balance between the actual cost and heuristic estimate.

2. Weighted A* guarantees that the solution cost will not exceed W times the optimal cost.yes the reuslts stayed well in within the suboptimality limit.

3. I would choose Weighted A* with W aproximately 1.5–2. This reduces computation and node expansions compared to UCS or standard A*, which is important for a slow flight computer.

16.6 Memory and Real-World Drone Context

1. A* uses large open (frontier) and closed (visited) lists, which can consume a lot of memory. IDA* avoids this by storing only the current path, but it has to repeat searches and therefore takes more time.

2. would include things like weather conditions, wind speed, battery level, temporary .

3. If the target moves, the heuristic may point the drone toward an outdated location, making the search less effective.  learned heuristics become important because they can adapt as the target changes position.

4. I would combine BFS and Weighted A* by using BFS in simple areas and Weighted A* in larger or more complex areas to find paths faster. I would reconsider if the environment changed frequently or if memory  became major limitations.




