```python
# water jug problem

  

# jugs = (4, 3)

# initial state = (0,0)

# final state = (2, n) where n = 0, 1, 2, 3

  

def pour_water(jugs, initial, final):

    a, b = jugs

    x, y = initial

    visited = set()

    goal = final[0]

  

    while x != goal:

        if (x, y) in visited:

            return "No solution"

        visited.add((x, y))

        if x == 0:

            x = a

        elif y == b:

            y = 0

        else:

            transfer = min(x, b - y)

            x -= transfer

            y += transfer

  

        print(f"({x}, {y})")

    return "Solution found"

  

jugs = (4, 3)

initial = (0, 0)

final = (2, 0)

pour_water(jugs, initial, final)
```

