# Breadth-first Searc- [Breadth-first Search](#Breadth-first-Search)

- [Employee info](#Employee-info)h

"""python
# Employee info
class Employee:
    def __init__(self, id, importance, subordinates):
        # It's the unique id of each node.
        # unique id of this employee
        self.id = id
        # the importance value of this employee
        self.importance = importance
        # the id of direct subordinates
        self.subordinates = subordinates
"""
class Solution:
    def getImportance(self, employees, id):
        """
        :type employees: Employee
        :type id: int
        :rtype: int
        """
        importance_dict = {}
        sub_dict = {}
        for e in employees:
            importance_dict[e.id] = e.importance
            sub_dict[e.id] = e.subordinates

        ans = 0
        queue = [id] 
        while queue:
            e = queue.pop(0)
            ans += importance_dict[e.id]
            for sub in sub_dict[e.id]:
                queue.append(sub.id)
            
        return ans
