# 489 - Robot Room Cleaner

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/robot-room-cleaner/
| Language | Python 3
| Runtime | 73 ms, faster than 83.14% of Python3 online submissions for Robot Room Cleaner
| Memory Usage | 15.3 MB, less than 80.16% of Python3 online submissions for Robot Room Cleaner

```python
# """
# This is the robot's control interface.
# You should not implement it, or speculate about its implementation
# """
#class Robot:
#    def move(self):
#        """
#        Returns true if the cell in front is open and robot moves into the cell.
#        Returns false if the cell in front is blocked and robot stays in the current cell.
#        :rtype bool
#        """
#
#    def turnLeft(self):
#        """
#        Robot will stay in the same cell after calling turnLeft/turnRight.
#        Each turn will be 90 degrees.
#        :rtype void
#        """
#
#    def turnRight(self):
#        """
#        Robot will stay in the same cell after calling turnLeft/turnRight.
#        Each turn will be 90 degrees.
#        :rtype void
#        """
#
#    def clean(self):
#        """
#        Clean the current cell.
#        :rtype void
#        """
class Solution:
    def cleanRoom(self, robot):
        """
        :type robot: Robot
        :rtype: None
        """
        self.cleaned = set()
        self.roomba(robot, (0,0), (0,1))
        
    def roomba(self, robot, current_position, direction):
        robot.clean()
        self.cleaned.add(current_position)
        x, y = current_position

        for _ in range(4):
            next_position = (
                current_position[0] + direction[0],
                current_position[1] + direction[1]
            )
        
            if (next_position) not in self.cleaned and robot.move():
                self.roomba(robot,next_position,direction)
                self.moveBack(robot)
                
            robot.turnLeft()
            direction = -direction[1], direction[0]

    def moveBack(self,robot):
        robot.turnLeft()
        robot.turnLeft()
        robot.move()
        robot.turnLeft()
        robot.turnLeft()
```
