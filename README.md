<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name:Niranjani.C                 </h3>
<h3>Register Number/Staff Id:212223220069                </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>Program </h1>

```
wumpus = [["Save", "Breeze", "PIT", "Breeze"],
          ["Smell", "Save", "Breeze", "Save"],
          ["WUMPUS", "GOLD", "PIT", "Breeze"],
          ["Smell", "Save", "Breeze", "PIT"]]


# Initial Variables
row, column = 0, 0  # Starting at top-left corner
arrow = True
player = True
score = 0

while player:
    choice = input("Press u to move up\nPress d to move down\nPress l to move left\nPress r to move right\n").lower()

    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("Move denied")
    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("Move denied")
    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("Move denied")
    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("Move denied")
    else:
        print("Invalid move. Try again.")

    print("Current location:", wumpus[row][column], "\n")

    if wumpus[row][column] == "Smell" and arrow:
        arrow_choice = input("You smell the Wumpus!\nDo you want to shoot the arrow?\nPress y to shoot\nPress n to save your arrow\n").lower()
        if arrow_choice == "y":
            arrow_throw = input("Shoot direction:\nPress u for up\nPress d for down\nPress l for left\nPress r for right\n").lower()
            hit = False
            if arrow_throw == "u" and row > 0:
                if wumpus[row-1][column] == "WUMPUS":
                    hit = True
                    wumpus[row-1][column] = "Save"
            elif arrow_throw == "d" and row < 3:
                if wumpus[row+1][column] == "WUMPUS":
                    hit = True
                    wumpus[row+1][column] = "Save"
            elif arrow_throw == "l" and column > 0:
                if wumpus[row][column-1] == "WUMPUS":
                    hit = True
                    wumpus[row][column-1] = "Save"
            elif arrow_throw == "r" and column < 3:
                if wumpus[row][column+1] == "WUMPUS":
                    hit = True
                    wumpus[row][column+1] = "Save"

            if hit:
                print("Wumpus killed!")
                score += 1000
                # Remove the smell from adjacent cells
                wumpus[1][0] = "Save"
                wumpus[3][0] = "Save"
            else:
                print("Arrow wasted...")
                score -= 10

            print("Score:", score)
            arrow = False

    if wumpus[row][column] == "WUMPUS":
        score -= 1000
        print("Wumpus here!! You die.\nYour score is:", score)
        break

    if wumpus[row][column] == "GOLD":
        score += 1000
        print("Congratulations! You found the GOLD!\nYou win!\nYour score is:", score)
        break

    if wumpus[row][column] == "PIT":
        score -= 1000
        print("Ahhhhh!!!! You fell into a pit.\nYour score is:", score)
        break
```
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)

<h1>Output</h1>

![image](https://github.com/user-attachments/assets/3cf3d7f1-08da-4972-9c54-117da94de4cb)

<h1>Result</h1>
Thus the Wumpus World Problem using Python demonstrating Inferences from Propositional Logic executed successfully.


