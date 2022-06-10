# Dining Philosophers Problem
The dining philosophers problem is an example problem often used in concurrent algorithm design 
to illustrate synchronization issues and techniques for resolving them.

## Problem statement:
* There are 5 philosophers sitting around a round table eating spaghetti and each of them has one fork between them (i.e. a total of five forks).
* Every philosopher has two states: eating and thinking.
* When a philosopher gets hungry, he tries to acquire his left and right fork, one by one. If successful in acquiring two forks, he eats for a while, then puts down the forks (thus allowing other philosopher to pick it up), and continues to think.

### Deadlock 
When each philosopher picks up the fork to their left, they also end up picking the right fork of the
person sitting next to them which leaves every philosopher with just one fork and nobody can start eating. 
Since every philosopher is dependent on each other, it forms a circular-wait and the system goes into a deadlock condition.
<p align="center">
     <img src="images/deadlock.png" width="500">
</p>

# The solution process
<p align="center">
     <img src="images/solution.png" width="900">
</p>

## Example:
```go
$ go run .
There are 5 philosophers sitting at a table
Phil 3 - is thinks for 666.145821ms
Phil 1 - is thinks for 235.010051ms
Phil 5 - is thinks for 947.77941ms
Phil 4 - is thinks for 287.113937ms
Phil 2 - is thinks for 82.153551ms
Phil 2 - got the left fork
Phil 2 - got the right fork
Phil 2 - is eats for 549.16732ms
Phil 1 - got the left fork
Phil 1 - put the left fork down
Phil 1 - is thinks for 632.969758ms
Phil 4 - got the left fork
Phil 4 - got the right fork
Phil 4 - is eats for 331.776148ms
Phil 4 - return forks
Phil 4 - is done dining
Phil 2 - return forks
Phil 2 - is done dining
Phil 3 - got the left fork
Phil 3 - got the right fork
Phil 3 - is eats for 183.117216ms
Phil 3 - return forks
Phil 3 - is done dining
Phil 1 - got the left fork
Phil 1 - got the right fork
Phil 1 - is eats for 480.279449ms
Phil 5 - got the left fork
Phil 5 - put the left fork down
Phil 5 - is thinks for 760.398084ms
Phil 1 - return forks
Phil 1 - is done dining
Phil 5 - got the left fork
Phil 5 - got the right fork
Phil 5 - is eats for 263.669287ms
Phil 5 - return forks
Phil 5 - is done dining
5 philosophers finished eating!
```
