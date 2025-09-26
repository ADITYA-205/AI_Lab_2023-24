# Ex.No: 11  Planning –  Block World Problem 
### DATE: 26-09-2025                                                                          
### REGISTER NUMBER : 212223040007
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
     
### DOMAIN:
```
(define (problem pb1)
  (:domain blocksworld)

  (:objects
    a b
  )

  (:init
    (on-table a)
    (on-table b)
    (clear a)
    (clear b)
    (arm-empty)
  )

  (:goal
    (and
      (on a b)
    )
  )
)
```








### PROBLEM 1:
```
(define (problem pb1)
  (:domain blocksworld)

  (:objects
    a b
  )

  (:init
    (on-table a)
    (on-table b)
    (clear a)
    (clear b)
    (arm-empty)
  )

  (:goal
    (and
      (on a b)
    )
  )
)
```

### Output/Plan:
<img width="1396" height="680" alt="image" src="https://github.com/user-attachments/assets/4edf4bfc-913c-45f3-9b3e-12b30a4da8b0" />
<img width="1288" height="688" alt="image" src="https://github.com/user-attachments/assets/24ae72dd-f8c0-4c3e-9e71-1168d3a2fae1" />
### PROBLEM 2:
```
(define (problem pb3)
  (:domain blocksworld)

  (:objects
    a b c
  )

  (:init
    (on-table a)
    (on-table b)
    (on-table c)
    (clear a)
    (clear b)
    (clear c)
    (arm-empty)
  )

  (:goal
    (and
      (on a b)
      (on b c)
    )
  )
)
```
### Output/Plan:
<img width="1296" height="696" alt="image" src="https://github.com/user-attachments/assets/e4f84174-15a9-4995-a8f5-e76a7e47caa2" />
<img width="1361" height="700" alt="image" src="https://github.com/user-attachments/assets/6e23563e-3b36-47fb-830e-30509a90f27d" />
<img width="1313" height="696" alt="image" src="https://github.com/user-attachments/assets/58a0d847-e2f9-452a-8ed0-e19a669597e8" />
<img width="1265" height="716" alt="image" src="https://github.com/user-attachments/assets/62449233-3e25-4643-8ee0-c1ec3dca0833" />



### Result:
Thus the plan was found for the initial and goal state of block world problem.
