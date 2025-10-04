# Ex.No: 12  Planning –  Monkey Banana Problem
### DATE: 27-09-2025                                                                            
### REGISTER NUMBER : 212223040007
### AIM: 
To find the sequence of plan for Monkey Banana problem using PDDL Editor.
###  Algorithm:
Step 1:  Start the program <br> 
Step 2 : Create a domain for Monkey Banana Problem. <br> 
Step 3:  Create a domain by specifying predicates. <br> 
Step 4: Specify the actions GOTO, CLIMB, PUSH-BOX, GET-KNIFE, GRAB-BANANAS in Monkey Banana problem.<br>  
Step 5:   Define a problem for Monkey Banana problem.<br> 
Step 6:  Obtain the plan for given problem.<br> 
Step 7: Stop the program.<br> 
### Program:
#### Domain:
```
(define (domain monkey)
  (:requirements :strips)
  (:constants monkey box knife bananas glass waterfountain)
  (:predicates 
    (location ?x)
    (on-floor)
    (at ?m ?x)
    (hasknife)
    (onbox ?x)
    (hasbananas)
    (hasglass)
    (haswater))

  ;; movement and climbing
  (:action GO-TO
    :parameters (?x ?y)
    :precondition (and (location ?x) (location ?y) (on-floor) (at monkey ?y))
    :effect (and (at monkey ?x) (not (at monkey ?y))))

  (:action CLIMB
    :parameters (?x)
    :precondition (and (location ?x) (at box ?x) (at monkey ?x))
    :effect (and (onbox ?x) (not (on-floor))))

  (:action PUSH-BOX
    :parameters (?x ?y)
    :precondition (and (location ?x) (location ?y) (at box ?y) (at monkey ?y) (on-floor))
    :effect (and (at monkey ?x) (not (at monkey ?y))
                 (at box ?x) (not (at box ?y))))

  ;; getting bananas
  (:action GET-KNIFE
    :parameters (?y)
    :precondition (and (location ?y) (at knife ?y) (at monkey ?y))
    :effect (and (hasknife) (not (at knife ?y))))

  (:action GRAB-BANANAS
    :parameters (?y)
    :precondition (and (location ?y) (hasknife) (at bananas ?y) (onbox ?y))
    :effect (hasbananas))

  ;; getting water
  (:action PICKGLASS
    :parameters (?y)
    :precondition (and (location ?y) (at glass ?y) (at monkey ?y))
    :effect (and (hasglass) (not (at glass ?y))))

  (:action GETWATER
    :parameters (?y)
    :precondition (and (location ?y) (hasglass) (at waterfountain ?y) (at monkey ?y) (onbox ?y))
    :effect (haswater)))
```
#### Problem:
```
(define (problem pb1)
  (:domain monkey)
  (:objects p1 p2 p3 p4 bananas monkey box knife)
  (:init 
    (location p1)
    (location p2)
    (location p3)
    (location p4)
    (at monkey p1)
    (on-floor)
    (at box p2)
    (at bananas p3)
    (at knife p4))
  (:goal 
    (and (hasbananas))))
```






### Output/Plan:
<img width="575" height="531" alt="image" src="https://github.com/user-attachments/assets/5652c1cb-6734-4b4c-b471-d5dd58ec341a" />
<img width="567" height="507" alt="image" src="https://github.com/user-attachments/assets/2c73a345-f18b-497e-9921-b3a138cbec12" />
<img width="573" height="541" alt="image" src="https://github.com/user-attachments/assets/4ba21a47-3fe0-4d00-921f-78e8ff5ae324" />
<img width="569" height="639" alt="image" src="https://github.com/user-attachments/assets/c2245b97-22c2-450a-a1b3-8ea464709c99" />
<img width="540" height="489" alt="image" src="https://github.com/user-attachments/assets/04a4b0c9-f7ae-4ace-9c6c-be438885f766" />
<img width="529" height="406" alt="image" src="https://github.com/user-attachments/assets/cf1a8cbd-b0f0-42fd-978a-f66582da6ec1" />



### Result:
Thus the plan was found for the initial and goal state of given problem.
