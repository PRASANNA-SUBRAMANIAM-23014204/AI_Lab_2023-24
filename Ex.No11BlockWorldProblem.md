# Ex.No: 11  Planning –  Block World Problem 
### DATE:   23/09/2025                                                                         
### REGISTER NUMBER : 2122230204
### AIM: 
To find the sequence of plan for Block word problem using PDDL  
###  Algorithm:
Step 1 :  Start the program <br>
Step 2 : Create a domain for Block world Problem <br>
Step 3 :  Create a domain by specifying predicates clear, on table, on, arm-empty, holding. <br>
Step 4 : Specify the actions pickup, putdown, stack and un-stack in Block world problem <br>
Step 5 :  In pickup action, Robot arm pick the block on table. Precondition is Block is on table and no other block on specified block and arm-hand empty.<br>
Step 6:  In putdown action, Robot arm place the block on table. Precondition is robot-arm holding the block.<br>
Step 7 : In un-stack action, Robot arm pick the block on some block. Precondition is Block is on another block and no other block on specified block and arm-hand empty.<br>
Step 8 : In stack action, Robot arm place the block on under block. Precondition is Block holded by robot arm and no other block on under block.<br>
Step 9 : Define a problem for block world problem.<br> 
Step 10 : Obtain the plan for given problem.<br> 
     
### Program:
```
(define (domain blocksworld)
(:requirements :strips :equality)
(:predicates (clear ?x)
(on-table ?x)
(arm-empty)
(holding ?x)
(on ?x ?y))
(:action pickup
:parameters (?ob)
:precondition (and (clear ?ob) (on-table ?ob) (arm-empty))
:effect (and (holding ?ob) (not (clear ?ob)) (not (on-table ?ob))
(not (arm-empty))))
(:action putdown
:parameters (?ob)
:precondition (and (holding ?ob))
:effect (and (clear ?ob) (arm-empty) (on-table ?ob)
(not (holding ?ob))))
(:action stack
:parameters (?ob ?underob)
:precondition (and (clear ?underob) (holding ?ob))
:effect (and (arm-empty) (clear ?ob) (on ?ob ?underob)
(not (clear ?underob)) (not (holding ?ob))))
(:action unstack
:parameters (?ob ?underob)
:precondition (and (on ?ob ?underob) (clear ?ob) (arm-empty))
:effect (and (holding ?ob) (clear ?underob)
(not (on ?ob ?underob)) (not (clear ?ob)) (not (arm-empty)))))
```









### Input 
```
(define (problem pb1)
(:domain blocksworld)
(:objects a b)
(:init (on-table a) (on-table b) (clear a) (clear b) (arm-empty))
(:goal (and (on a b))))

(define(problem pb3)
(:domain blocksworld)
(:objects a b c)
(:init (on-table a) (on-table b) (on-table c)
(clear a) (clear b) (clear c) (arm-empty))
(:goal (and (on a b) (on b c))))
```

### Output/Plan:
<img width="509" height="654" alt="Screenshot 2025-09-23 091455" src="https://github.com/user-attachments/assets/8dc38f92-be70-46ee-b9ce-86856ae43c92" />
<img width="504" height="640" alt="Screenshot 2025-09-23 091856" src="https://github.com/user-attachments/assets/ad0f0d44-2926-441e-bad6-7fb4ef4f148b" />
<img width="512" height="652" alt="Screenshot 2025-09-23 093201" src="https://github.com/user-attachments/assets/7f6bbde8-ba81-402b-921d-c8c449efa6f2" />
<img width="569" height="596" alt="Screenshot 2025-09-23 093214" src="https://github.com/user-attachments/assets/965018cb-72cb-408a-90fb-e52c39acf7c5" />







### Result:
Thus the plan was found for the initial and goal state of block world problem.
