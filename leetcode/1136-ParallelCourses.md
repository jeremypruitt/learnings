# 1136 - Parallel Courses

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/parallel-courses/
| Language | Python 3
| Runtime | 286 ms, faster than 74.07% of Python3 online submissions for Parallel Courses
| Memory Usage | 17.2 MB, less than 33.94% of Python3 online submissions for Parallel Courses
| Datastructures | Graph
| Algorithms | BFS, topological sort

### Procedure

1. TBD...

### Code

```python
class Solution:
    def minimumSemesters(self, n: int, relations: List[List[int]]) -> int:
        courses_taken = []
        semester_count = 0
        
        # Init graph
        incoming_edges = {}
        graph = {}
        for i in range(1, n+1):
            incoming_edges[i] = 0
            graph[i] = []
        
        # Build graph
        for course1, course2 in relations:
            graph[course1].append(course2)
            incoming_edges[course2] += 1
        
        # Find all sources (vertices with 0 in_degree)
        sources = []
        for source in incoming_edges:
            if incoming_edges[source] == 0:
                sources.append(source)
        
        # Check for cycle. If no source course to start, then there must
        # be a cycle and we can't finish
        semester_course_count = 0
        if len(sources) > 0:
            semester_count += 1
            semester_course_count = len(sources)
        else:
            return -1
        
        # Add each source to course_taken and -1 from all of it's children
        # in degrees. If child in degree is 0, then add to sources queue
        while sources:
            # If we have taken all courses this semester
            if semester_course_count <= 0:
                # Start a new semester
                semester_count += 1
                # Courses we can take in new semester:
                semester_course_count = len(sources)
            
            # Take a course this semester
            # 1) Decrement course count for semester
            # 2) Pop source from sources queue
            # 3) Add course to courses taken
            # 4) ???
            semester_course_count -= 1
            source = sources.pop(0)
            courses_taken.append(source)
            for child in graph[source]:
                incoming_edges[child] -= 1
                if incoming_edges[child] == 0:
                    sources.append(child)
        
        # Return failure if not able to take all  courses
        if len(courses_taken) != n: return -1
        
        return semester_count
```
