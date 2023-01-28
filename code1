MOD = 10 ** 9 + 7
from queue import PriorityQueue
from typing import List, Tuple


class Solution:
    def countPaths(self, n: int, roads: List[List[int]]) -> int:
        graph = [[] for _ in range(n)]
        for road in roads:
            u, v, time = road
            graph[u].append((v, time))
            graph[v].append((u, time))

        return self.dijkstra(graph, n, 0)

    def dijkstra(self, graph: List[List[Tuple[int, int]]], n: int, src: int) -> int:
        dist = [float('inf') for _ in range(n)]
        ways = [0 for _ in range(n)]
        ways[src] = 1
        dist[src] = 0
        minHeap = PriorityQueue()
        minHeap.put((0, 0))
        while not minHeap.empty():
            d, u = minHeap.get()
            if d > dist[u]: continue
            for v, time in graph[u]:
                if dist[v] > d + time:
                    dist[v] = d + time
                    ways[v] = ways[u]
                    minHeap.put((dist[v], v))
                elif dist[v] == d + time:
                    ways[v] = (ways[v] + ways[u]) % MOD
        return ways[n - 1]
def main():
    solution = Solution()
    n = 7
    roads = [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]
    print(solution.countPaths(n, roads))

if __name__ == "__main__":
    main()




