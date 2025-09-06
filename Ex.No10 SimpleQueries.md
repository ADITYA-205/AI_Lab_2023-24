# Ex.No: 10  Logic Programming –  Simple queries from facts and rules
### DATE: 06-09-2025                                                                           
### REGISTER NUMBER : 212223040007
### AIM: 
To write a prolog program to find the answer of query. 
###  Algorithm:
 Step 1: Start the program <br> 
 Step 2: Convert the sentence into First order Logic  <br> 
 Step 3:  Convert the sentence into Horn clause form  <br> 
 Step 4: Add rules and predicates in a program   <br> 
 Step 5:  Pass the query to program. <br> 
 Step 6: Prolog interpreter shows the output and return answer. <br> 
 Step 8:  Stop the program.
### Program:
### Task 1:
Construct the FOL representation for the following sentences <br> 
1.	John likes all kinds of food.  <br> 
2.	Apples are food.  <br> 
3.	Chicken is a food.  <br> 
4.	Sue eats everything Bill eats. <br> 
5.	 Bill eats peanuts  <br> 
   Convert into clause form and Prove that John like Apple by using Prolog. <br> 
### Program:
```
likes(john,X):-food(X).
food(apple).
food(chicken).
eats(sue,X):-eats(bill,X).
eats(bill,peanuts).
```

### Output:
<img width="954" height="95" alt="image" src="https://github.com/user-attachments/assets/dc52b0a1-ef35-4af0-bd95-0155907c7541" />

### Task 2:
Consider the following facts and represent them in predicate form: <br>              
1.	Steve likes easy courses. <br> 
2.	Science courses are hard. <br> 
3. All the courses in Have fun department are easy <br> 
4. BK301 is Have fun department course.<br> 
Convert the facts in predicate form to clauses and then prove by resolution: “Steve likes BK301 course”<br> 

### Program:
```
likes(steve,X):-easycourse(X).
hard(science).
easycourse(X):-dept(basketweaving,X).
dept(basketweaving,bk301).
```

### Output:
<img width="948" height="90" alt="image" src="https://github.com/user-attachments/assets/b191ce31-fa46-4c3f-8aa5-2189b88451a7" />

### Task 3:
Consider the statement <br> 
“This is a crime for an American to sell weapons to hostile nations. The Nano , enemy of America has some missiles and its missiles were sold it by Colonal West who is an American” <br> 
Convert to Clause form and prove west is criminal by using Prolog.<br> 
### Program:
```
missile(m1).
owns(nono, m1).
enemy(nono, america).
american(west).
sells(west, m1, nono).
weapon(X) :- missile(X).
hostile(X) :- enemy(X, america).
criminal(X) :- american(X), weapon(Y), hostile(Z), sells(X, Y, Z).
```

### Output:
<img width="944" height="77" alt="image" src="https://github.com/user-attachments/assets/982bac9d-da80-4fd0-84d9-845730982159" />

### Result:
Thus the prolog programs were executed successfully and the answer of query was found.
