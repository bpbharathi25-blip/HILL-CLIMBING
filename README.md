<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name: Persys freeda J          </h3>
<h3>Register Number: 212224060185           </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>


<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence

# Hill Climbing Algorithm Implementation in Python

import random
import string

# Function to calculate fitness (Heuristic function)
def fitness_function(target, test_string):
    score = 0
    for i in range(len(target)):
        score += abs(ord(target[i]) - ord(test_string[i]))
    return score

# Function to generate a random string of same length as target
def random_string(length):
    letters = string.ascii_letters + string.punctuation + ' '
    return ''.join(random.choice(letters) for _ in range(length))

# Function to mutate one character in the string
def mutate(parent):
    index = random.randint(0, len(parent) - 1)
    letters = string.ascii_letters + string.punctuation + ' '
    new_char = random.choice(letters)
    child = list(parent)
    child[index] = new_char
    return ''.join(child)

# Hill Climbing algorithm
def hill_climb(target):
    current_solution = random_string(len(target))
    current_score = fitness_function(target, current_solution)
    print("Initial Score:", current_score, "Initial Solution:", current_solution)

    while True:
        new_solution = mutate(current_solution)
        new_score = fitness_function(target, new_solution)

        print("Score:", new_score, "Solution:", new_solution)

        if new_score == 0:
            print("\nResult : Solution Found =", new_solution)
            break

        if new_score < current_score:
            current_solution = new_solution
            current_score = new_score

# ---------------- MAIN PROGRAM ----------------
target = input("Enter the target string: ")
hill_climb(target)


<h2>Output:</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>
result 
thus the output has been executed
