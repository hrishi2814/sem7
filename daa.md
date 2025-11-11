## 🧮 Practical 1: Fibonacci Numbers and Step Count

### What is an algorithm?

An algorithm is a finite, well-defined, step-by-step set of instructions or rules designed to perform a specific task or solve a particular problem.

### Explain the purpose of step count in algorithm analysis.

A **step count** is a method of analysing an algorithm's efficiency by counting the number of fundamental operations (like assignments, comparisons, or arithmetic operations) it performs. Its purpose is to get a concrete measure of performance that is **independent of the hardware** (CPU speed) or programming language.

### What is time complexity?

**Time complexity** is a theoretical measure of how the runtime of an algorithm _grows_ as the input size ($n$) increases. It's not about the exact time in seconds, but about the _rate of growth_. It is commonly expressed using asymptotic notations (like Big-O).

### How do you calculate step count for an iterative algorithm?

You count the number of times each statement executes.

- **Constant time operations:** (e.g., `a = b + c`) count as 1 step.
    
- **Loops:** A loop that runs $n$ times containing 1 step will be $n$ steps.
    
- Nested Loops: A loop running $n$ times with a nested loop running $n$ times will be $n \times n = n^2$ steps.
    
    The total step count is the sum of the counts for all statements.
    

### What is the time complexity of the Fibonacci series using iteration?

The iterative (bottom-up) approach uses a simple loop that runs $n$ times.

- **Time Complexity:** $O(n)$ (Linear time).
    
- **Space Complexity:** $O(1)$ (as you only need to store the previous two values).
    

### What is the time complexity of the Fibonacci series using recursion?

The naive recursive approach (e.g., `fib(n) = fib(n-1) + fib(n-2)`) is highly inefficient.

- Time Complexity: $O(2^n)$ (Exponential time).
    
    This is because it re-calculates the same subproblems (like fib(3)) many times.
    

### Why is recursive Fibonacci inefficient?

It suffers from the **"overlapping subproblems"** property. To calculate `fib(5)`, it calls `fib(4)` and `fib(3)`. Then, `fib(4)` calls `fib(3)` and `fib(2)`. Notice that `fib(3)` is computed twice, and this redundancy grows exponentially.

### How can we optimize Fibonacci calculation?

We can use **Dynamic Programming (DP)**:

1. **Memoization (Top-Down):** Use the recursive solution but store the result of each `fib(k)` in an array or map. Before computing, check if the value is already stored. This brings the time complexity down to $O(n)$.
    
2. **Tabulation (Bottom-Up):** This is the iterative solution. Build an array (or use two variables) and calculate `fib(0)`, `fib(1)`, `fib(2)`, ... up to `fib(n)`. This is also $O(n)$.
    

### Define asymptotic notations O, Ω, and Θ.

These notations describe the growth rate of functions.

- **O (Big-O):** **Upper Bound**. It describes the **worst-case** scenario. $f(n) = O(g(n))$ means the runtime $f(n)$ grows _no faster than_ $g(n)$.
    
- **Ω (Omega):** **Lower Bound**. It describes the **best-case** scenario. $f(n) = \Omega(g(n))$ means the runtime $f(n)$ grows _at least as fast as_ $g(n)$.
    
- **Θ (Theta):** **Tight Bound**. It describes the **average-case** scenario. $f(n) = \Theta(g(n))$ means the runtime $f(n)$ grows _at the same rate as_ $g(n)$ (it's "sandwiched" between the upper and lower bound).
    

### What is the difference between best, worst, and average case analysis?

- **Best Case:** The minimum runtime for an algorithm, given the "easiest" possible input (e.g., finding an item at the _start_ of a list).
    
- **Worst Case:** The maximum runtime, given the "hardest" possible input (e.g., finding an item at the _end_ of a list).
    
- **Average Case:** The expected runtime, averaged over all possible inputs.
    

### What are dominant operations in an algorithm?

The **dominant operation** (or "basic operation") is the operation that is executed most frequently and contributes the most to the overall runtime, especially as the input size $n$ grows. This is typically the operation inside the innermost loop.

### Why do we need algorithm correctness?

An algorithm is "correct" if it halts and produces the correct output for _every_ valid input. If an algorithm is fast but gives the wrong answer, it is useless. Correctness is the most fundamental property.

### What are the characteristics of a good algorithm?

1. **Correct:** Produces the right output.
    
2. **Efficient:** Has low time and space complexity.
    
3. **Finite:** Terminates after a finite number of steps.
    
4. **Well-defined:** Each step is clear and unambiguous.
    
5. **Simple/Readable:** Easy to understand and implement.
    

### Explain the concept of iterative algorithm design issues.

This refers to the common challenges when designing iterative (loop-based) solutions:

- **Initialization:** Correctly setting up all variables before the loop.
    
- **Loop Invariant:** Defining a property that is true _before_, _during_, and _after_ each iteration. This helps prove correctness.
    
- **Progress:** Ensuring the loop is making progress toward the end.
    
- **Termination:** Guaranteeing the loop will stop (i.im, avoid infinite loops).
    
- **State Management:** Correctly updating variables (state) within the loop.
    

### Compare iterative and recursive Fibonacci implementations.

|**Feature**|**Iterative (Tabulation)**|**Recursive (Naive)**|
|---|---|---|
|**Logic**|Bottom-up (starts at 0, 1 and builds up)|Top-down (starts at $n$, breaks down)|
|**Time**|$O(n)$ - Linear|$O(2^n)$ - Exponential|
|**Space**|$O(1)$|$O(n)$ - due to call stack depth|
|**Overhead**|Low|High (many function calls)|
|**Efficiency**|Very efficient|Very inefficient|

---

## 💼 Practical 2: Job Sequencing with Deadlines (Greedy Method)

### What is the greedy method?

The **greedy method** is an algorithmic strategy for solving optimization problems. It works by making the **locally optimal choice** at each step (the choice that seems best at the moment) with the hope that these choices will lead to a **globally optimal solution**.

### Explain the principle of greedy strategy with an example.

The principle is to always make the best immediate choice, without ever reconsidering it.

- **Example: Making Change.** To give 48 cents in change using US coins (25, 10, 5, 1), you greedily:
    
    1. Take the largest coin $\le 48$ (a **25-cent** coin). Remaining: 23 cents.
        
    2. Take the largest coin $\le 23$ (a **10-cent** coin). Remaining: 13 cents.
        
    3. Take the largest coin $\le 13$ (a **10-cent** coin). Remaining: 3 cents.
        
    4. Take the largest coin $\le 3$ (a **1-cent** coin). Remaining: 2 cents.
        
    5. ...and so on.
        
        This greedy approach happens to be optimal for US currency.
        

### What is job sequencing with deadlines?

It's an optimization problem where you are given a set of jobs, each with a **profit** and a **deadline**. You can only perform one job per time unit. The goal is to find a schedule (a subset of jobs) that **maximizes the total profit**, such that all selected jobs are completed by their respective deadlines.

### What is the objective of job sequencing (profit maximization)?

The objective is to select a subset of jobs and schedule them, one per time slot, to earn the **maximum possible total profit**.

### What are the inputs and outputs for the job sequencing problem?

- **Inputs:** A list of $n$ jobs, where each job $i$ has a profit $P_i$ and a deadline $D_i$.
    
- **Outputs:**
    
    1. An optimal subset of jobs that can be scheduled.
        
    2. The maximum total profit.
        

### Explain the control abstraction of a greedy method.

A "control abstraction" is a generic template for an algorithm. For a greedy method, it looks like this:

```
GreedySolution(Input):
  Solution = {}
  while (more items in Input):
    item = Select(Input)    // Greedy choice
    if (Feasible(Solution, item)):
      Solution = Union(Solution, item)
  return Solution
```

### What is the time complexity of the job sequencing algorithm?

1. **Sorting:** Sort all $n$ jobs in decreasing order of profit. This takes $O(n \log n)$ time.
    
2. **Scheduling:** For each of the $n$ jobs, find a valid time slot (from its deadline $D_i$ down to 1). In the worst case, this can take $O(n \times D_{max})$ or $O(n^2)$.
    

- A more efficient implementation using a **disjoint set data structure** can make the scheduling part nearly $O(n)$, making the total time dominated by sorting: **$O(n \log n)$**.
    

### How is sorting used in job sequencing?

Sorting is the core of the greedy choice. You **sort all jobs by profit in descending (decreasing) order**. This ensures that you always try to schedule the most profitable jobs first.

### Why is greedy strategy suitable for this problem?

This problem exhibits the **greedy choice property**. The strategy is to take the most profitable job, and place it in the latest possible time slot that is still before its deadline. It can be proven (using an "exchange argument") that this local choice (highest profit) always leads to a globally optimal solution.

### What happens when two jobs have the same deadline?

It doesn't matter. The greedy choice is based on **profit**, not deadline. You will simply try to schedule the job with the higher profit first. If both have the same deadline, the one with more profit gets first dibs on the time slots.

### What is an optimal solution in the context of greedy algorithms?

An optimal solution is a **feasible solution** (one that satisfies all constraints) that achieves the best possible value for the objective function (e.g., maximum profit, minimum cost).

### Compare job sequencing with activity selection problem.

Both are classic greedy problems.

- **Activity Selection:** Given activities with start/end times. **Goal:** Maximize _number_ of activities. **Greedy Choice:** Sort by **finish time** and pick the next compatible activity.
    
- **Job Sequencing:** Given jobs with profits/deadlines. **Goal:** Maximize _total profit_. **Greedy Choice:** Sort by **profit** and place in the latest available time slot.
    

### What are the limitations of greedy strategy?

The main limitation is that **it doesn't always work**. It fails for problems that require "looking ahead." For many problems (like the 0/1 Knapsack), a greedy choice may seem good locally but prevent a better global solution later.

### Explain real-life applications of job sequencing.

- Scheduling tasks on a single-core CPU.
    
- Manufacturing processes with different valuable tasks and due dates.
    
- Resource allocation in a system where tasks have different priorities (profits) and deadlines.
    

### How does greedy differ from dynamic programming in solving optimization problems?

|**Feature**|**Greedy Method**|**Dynamic Programming (DP)**|
|---|---|---|
|**Choice**|Makes one locally optimal choice.|Explores _all_ possible choices.|
|**Subproblems**|Does not solve subproblems.|Solves overlapping subproblems.|
|**Strategy**|Makes a choice and "never looks back."|"Remembers" past results (memoization).|
|**Guarantee**|Only works if the problem has the greedy-choice property.|Guarantees optimality if the problem has optimal substructure.|

---

## 🎒 Practical 3: Fractional Knapsack Problem (Greedy Method)

### What is the knapsack problem?

It's an optimization problem. Given a set of items, each with a **weight** and a **value (or profit)**, determine the set of items to include in a knapsack of a fixed **capacity $W$** to **maximize the total value**.

### What is the difference between 0/1 and fractional knapsack?

- **0/1 Knapsack:** You must take the _entire_ item or _none_ of it. You cannot take a fraction. (Choice is binary: 0 or 1).
    
- **Fractional Knapsack:** You **can** take fractions of items. (e.g., 50% of an item).
    

### Why can the fractional knapsack be solved using a greedy approach?

Because you can take fractions. The greedy strategy is to always take the item with the **highest value-per-unit-of-weight**. If you fill the knapsack and the next "best" item doesn't fit, you can just take a _fraction_ of it to fill the remaining space. This "no-regret" move guarantees an optimal solution.

### What is the principle of the greedy method applied here?

1. Calculate the **profit/weight (P/W) ratio** for every item.
    
2. Sort all items in **descending order** based on this ratio.
    
3. Iterate through the sorted list. For each item:
    
    - If the _entire item_ fits, take it.
        
    - If it _doesn't fit_, take the _fraction_ of the item that fills the remaining capacity.
        
    - Stop when the knapsack is full.
        

### Explain the term “profit/weight ratio”.

It is the "value density" of an item: $v_i / w_i$. It tells you how much profit you get for _each unit of weight_. The greedy algorithm prioritizes items with the highest "bang for your buck."

### What is the time complexity of the fractional knapsack algorithm?

The most time-consuming step is **sorting** the $n$ items by their P/W ratio.

- Time Complexity: $O(n \log n)$.
    
    The subsequent loop to fill the knapsack only takes $O(n)$ time.
    

### What data structures are used in its implementation?

- An array or list of objects (or structs) to store the items' weights, profits, and their calculated P/W ratio.
    
- The sorting algorithm might use additional space depending on the implementation (e.g., $O(n)$ for merge sort).
    

### Why is sorting important in fractional knapsack?

Sorting is **the greedy choice**. It arranges the items from "most desirable" (highest P/W ratio) to "least desirable." This allows the algorithm to simply iterate through the list and make the correct local choice at each step.

### Give one real-life example of fractional knapsack.

- Loading a truck with different types of divisible goods like **grain, sand, or liquids**. You can take any fraction of these goods, and you want to maximize the total value in the truck.
    
- Allocating a investment budget to various assets, where you can buy fractional shares.
    

### What is the difference between optimal substructure and greedy choice property?

- **Optimal Substructure:** An optimal solution to a problem contains optimal solutions to its _subproblems_. (Both DP and Greedy use this).
    
- **Greedy Choice Property:** This is unique to greedy algorithms. It means that a _locally optimal choice_ (the greedy choice) is _guaranteed_ to be part of _some_ globally optimal solution. You can "commit" to a choice without it backfiring.
    

### What are control abstractions of greedy algorithms?

(This is the same as in Practical 2). It's a general template for a greedy algorithm: select the best item, check if it's feasible, and add it to the solution.

### Compare fractional knapsack and 0/1 knapsack in terms of constraints.

- **Fractional Knapsack:** The amount to take of item $i$, $x_i$, can be $0 \le x_i \le 1$.
    
- **0/1 Knapsack:** The amount to take of item $i$, $x_i$, must be $x_i \in \{0, 1\}$.
    

### Define the term "local optimum" vs "global optimum" in greedy algorithms.

- **Local Optimum:** The best choice you can make _right now_, without considering future consequences.
    
- Global Optimum: The absolute best possible solution to the entire problem.
    
    The goal of a greedy algorithm is to find a global optimum by only making locally optimal choices.
    

### How do you prove the correctness of greedy solutions?

The most common method is an **"exchange argument"** (a proof by contradiction):

1. Assume there is an optimal solution $S_{opt}$ that is _not_ the greedy solution $S_{greedy}$.
    
2. Find the first step where the two solutions differ.
    
3. Show that you can "exchange" the non-greedy choice in $S_{opt}$ with the greedy choice from $S_{greedy}$ to get a _new_ solution that is _at least as good_ (or better) than $S_{opt}$.
    
4. This contradicts the assumption that $S_{opt}$ was optimal and different from the greedy one.
    

### What are the limitations of greedy approach?

(This is the same as in Practical 2). It fails on problems where a short-sighted local choice can prevent a better long-term solution (like in 0/1 Knapsack or navigating a complex maze).

---

## 🧠 Practical 4: 0–1 Knapsack Problem (Dynamic Programming / Branch & Bound)

### What is the 0–1 Knapsack problem?

It's an optimization problem where you must choose from a set of items (each with a weight and profit) to fit into a knapsack of capacity $W$. The constraint is that for each item, you must either take the **whole item (1)** or **leave the whole item (0)**.

### Why can’t 0–1 Knapsack be solved optimally by greedy strategy?

The greedy strategy (by P/W ratio) fails.

- **Example:** Capacity $W = 10$.
    
    - Item 1: 6 kg, $18 profit (Ratio: 3)
        
    - Item 2: 6 kg, $18 profit (Ratio: 3)
        
    - Item 3: 10 kg, $20 profit (Ratio: 2)
        
- **Greedy** (by ratio) would pick Item 1 ($18). Now $W=4$. It can't pick Item 2 or 3. Total profit = $18.
    
- **Greedy** (by profit) would pick Item 3 ($20). $W=0$. Total profit = $20.
    
- **Optimal** is to pick Item 1 + Item 2. Total weight = 12 (oops, let's fix the example).
    
- **Correct Example:** Capacity $W = 50$.
    
    - Item 1: 10 kg, $60 profit (Ratio: 6)
        
    - Item 2: 20 kg, $100 profit (Ratio: 5)
        
    - Item 3: 30 kg, $120 profit (Ratio: 4)
        
- **Greedy** (by ratio) picks Item 1 ($60). $W=40$. Picks Item 2 ($100). $W=20$. Can't pick Item 3. Total Profit = $160.
    
- Optimal is to pick Item 2 + Item 3 ($100 + $120 = $220).
    
    The greedy choice of Item 1 "locked out" the better global solution.
    

### What is dynamic programming (DP)?

**Dynamic Programming** is an algorithmic technique for solving optimization problems by breaking them down into simpler, **overlapping subproblems**. It solves each subproblem _only once_ and stores its solution in a table (memoization) to avoid redundant computations.

### Explain the principle of optimality.

This is the core idea of DP. It states that an **optimal solution to a problem is composed of optimal solutions to its subproblems**. For the 0/1 Knapsack, the optimal solution for $n$ items _must_ be built from an optimal solution for $n-1$ items.

### What is overlapping subproblem property?

This is the property that makes DP efficient. It means that the algorithm would re-encounter and re-solve the _exact same subproblems_ multiple times if it were implemented naively (like recursive Fibonacci). DP stores the answers to avoid this.

### What is the difference between DP and recursion?

- **Recursion (Naive):** Is top-down. Can be very inefficient if it has overlapping subproblems (like $O(2^n)$ for Knapsack).
    
- **DP (Memoization):** Is **Recursion + Caching**. It's top-down but stores results to avoid re-solving.
    
- **DP (Tabulation):** Is **iterative** and bottom-up. It builds a table of solutions from the smallest subproblem up to the final solution.
    

### Write the recursive formula for 0–1 knapsack.

Let $DP(i, w)$ be the maximum profit for a knapsack of capacity $w$ using items from $1$ to $i$.

For each item $i$, there are two choices:

1. **Don't include item $i$:** The profit is $DP(i-1, w)$.
    
2. **Include item $i$:** The profit is $Profit_i + DP(i-1, w - Weight_i)$. (Only if $w \ge Weight_i$).
    

The formula is:

$$DP(i, w) = \max(DP(i-1, w), \ Profit_i + DP(i-1, w - Weight_i))$$

### How is memoization used in DP?

Memoization (or caching) is used to store the results of the recursive function. You create a 2D array, memo[i][w], initialized to a special value (like -1).

Before computing DP(i, w), you check:

if memo[i][w] != -1: return memo[i][w]

After computing, you store:

memo[i][w] = result

### What is the time complexity of the DP approach?

The algorithm fills a 2D table of size $n \times W$. Each cell takes $O(1)$ time to compute.

- Time Complexity: $O(n \cdot W)$
    
    This is pseudo-polynomial time because it depends on the value of the capacity $W$, not just the number of items $n$.
    

### What is the space complexity of 0–1 knapsack?

- Space Complexity: $O(n \cdot W)$ to store the DP table.
    
    (This can be optimized to $O(W)$ if you only need the final profit, not the items).
    

### What is branch and bound?

**Branch and Bound (B&B)** is an algorithm design paradigm for optimization problems. It's a **state-space search** (like backtracking) that uses a **bounding function** to _prune_ (cut off) branches of the search tree that cannot possibly contain the optimal solution.

### How is bounding function used in branch and bound strategy?

A bounding function calculates an **upper bound** (for maximization) on the best possible solution in a given branch.

1. We maintain a "best solution found so far" (lower bound).
    
2. At each node (partial solution), we calculate the upper bound.
    
3. If **`upper_bound` $\le$ `best_solution_so_far`**, we **prune** this entire branch, because it can't _possibly_ lead to a better solution.
    

- For 0/1 Knapsack, a common upper bound is the solution to the **Fractional Knapsack** for the remaining items.
    

### Compare dynamic programming and branch & bound approaches.

|**Feature**|**Dynamic Programming (DP)**|**Branch & Bound (B&B)**|
|---|---|---|
|**Strategy**|Fills a table bottom-up.|State-space search (DFS or Best-First).|
|**Subproblems**|Solves _all_ subproblems.|Prunes branches, avoids many subproblems.|
|**Complexity**|$O(n \cdot W)$ (pseudo-polynomial)|$O(2^n)$ (Exponential - worst case)|
|**Best For**|Problems where $W$ is reasonably small.|Problems where $W$ is huge but $n$ is small, or when a good bound is found early.|

### What real-world problems are modeled as knapsack problems?

- **Resource Allocation:** Allocating a fixed budget to various projects, each with a cost (weight) and expected return (profit).
    
- **Portfolio Selection:** Choosing a set of investments.
    
- **Loading Cargo:** Deciding what items to put on a plane or truck.
    

### What are the advantages and disadvantages of DP over greedy method?

- **Advantage:** DP **guarantees optimality** for problems where greedy fails (like 0/1 Knapsack). It is more robust.
    
- **Disadvantage:** DP is more complex to design and implement. It has higher time and space complexity ($O(nW)$) compared to a greedy algorithm ($O(n \log n)$).
    

---

## 👑 Practical 5: N–Queens Problem using Backtracking

### What is the backtracking method?

**Backtracking** is a general algorithmic technique for solving **constraint satisfaction problems (CSPs)**. It's a recursive, "depth-first" search that builds a solution incrementally. If at any point it finds that a partial solution _cannot_ lead to a valid full solution, it **"backtracks"** (undoes its last choice) and tries the next available option.

### Explain the principle of backtracking.

1. **Start** at the root of a "state-space tree."
    
2. **Move** to a new child node (make a choice).
    
3. **Check Constraints:** Is this new partial solution "promising" (not invalid)?
    
    - **Yes:** If it's a full solution, record it. Otherwise, recursively call on the next level.
        
    - **No:** This path is a "dead end." **Backtrack** (undo the choice) and try the next sibling.
        

### What is the n-Queens problem?

The problem is to place $N$ chess queens on an $N \times N$ chessboard such that **no two queens can attack each other**. This means no two queens can be in the same **row**, **column**, or **diagonal**.

### What are constraints in the n-Queens problem?

We place one queen per row. So, for the queen in row $k$:

1. **Column Constraint:** It must not be in the same column as any queen in rows $0...k-1$.
    
2. **Diagonal Constraint:** It must not be on the same "up-right" or "up-left" diagonal as any queen in rows $0...k-1$.
    

### How does backtracking differ from brute force?

- **Brute Force:** Would try _all_ possible placements of $N$ queens (e.g., $N^N$ or $N!$ possibilities) and _then_ check if each placement is valid. This is incredibly slow.
    
- **Backtracking:** Is a "smart" brute force. It **prunes** the search. As soon as it places a queen that conflicts with another, it _stops_ exploring that entire branch of the search tree, saving a massive amount of computation.
    

### What is the concept of state space tree?

It's a tree that represents all possible states (partial solutions) of the problem.

- The **root** is the empty board.
    
- **Level 1** nodes are all possible placements for the 1st queen.
    
- Level 2 nodes are all possible placements for the 2nd queen, given the 1st.
    
    Backtracking is a DFS traversal of this tree, where "dead-end" branches are pruned.
    

### What is a promising node?

A node (partial solution) in the state-space tree is "promising" if it **does not violate any constraints** so far. It's "not promising" if it's already invalid (e.g., two queens are attacking). Backtracking only explores promising nodes.

### Explain the control abstraction of backtracking.

It's a recursive function:

```
Solve(column):
  if (all N queens are placed):
    return true // Found a solution
  
  for each row = 1 to N:
    if (isSafe(row, column)):
      PlaceQueen(row, column)
      if (Solve(column + 1) == true):
        return true
      RemoveQueen(row, column) // BACKTRACK
  
  return false // No solution found from here
```

### What is the time complexity of n-Queens problem?

It's still an exponential algorithm, as it's a search problem. It's much better than $O(N!)$, but there's no simple polynomial solution. The time complexity is roughly $O(N!)$ in the worst-case, but pruning makes it much faster in practice.

### What is the difference between partial and complete solutions?

- **Partial Solution:** A non-leaf node in the state-space tree (e.g., $k < N$ queens have been placed, and they are all safe so far).
    
- **Complete Solution:** A leaf node in the state-space tree where all $N$ queens have been placed and all constraints are satisfied.
    

### Why is backtracking preferred for constraint satisfaction problems?

Because it's a natural fit. The algorithm's core "isSafe()" check _is_ the constraint check. It's designed to explore options _while_ adhering to constraints, and it's very efficient at discarding large parts of the search space.

### What is pruning?

**Pruning** is the act of "cutting off" a branch of the state-space tree. In backtracking, this happens when the `isSafe()` check returns `false`. We stop exploring that path because we know it can't lead to a solution.

### What are the advantages of backtracking?

- **Efficiency:** Far more efficient than brute force.
    
- **Flexibility:** Can be adapted to many different CSPs (Sudoku, maze-solving, etc.).
    
- **Finds all solutions:** Can be easily modified to find _all_ possible solutions, not just the first one.
    

### Compare backtracking and branch and bound.

|**Feature**|**Backtracking**|**Branch & Bound (B&B)**|
|---|---|---|
|**Problem Type**|**Constraint Satisfaction** (Find _a_ solution).|**Optimization** (Find the _best_ solution).|
|**Pruning**|Uses **constraints** (`isSafe()`).|Uses **bounding function** (compares to "best-so-far").|
|**Example**|N-Queens, Sudoku|0/1 Knapsack, Traveling Salesman|
|**Note:** B&B is essentially an _enhancement_ of backtracking for optimization.|||

### Give another real-life example that can be solved using backtracking.

- **Sudoku Solver:** Each empty cell is a "choice." The constraints are the rules of Sudoku.
    
- **Maze Solving:** Each step is a "choice" (up, down, left, right). The constraint is "don't hit a wall" and "don't go in circles."
    
- **Graph Coloring:** Assigning colors to vertices with the constraint that no adjacent vertices share a color.
    

---

## 🪶 Practical 6: Huffman Coding using Greedy Strategy

### What is Huffman coding?

Huffman coding is a famous **greedy algorithm** used for **lossless data compression**. It creates an optimal **prefix-free, variable-length** encoding for a set of characters based on their frequencies.

### Why is Huffman coding called a greedy algorithm?

At each step, the algorithm makes the locally optimal choice: it finds the two characters (or sub-trees) with the **lowest frequencies** and **merges them** into a new sub-tree. This greedy merging process is repeated until only one tree remains.

### What is the goal of Huffman coding?

The goal is to **minimize the average code length** for a file. It does this by assigning very **short** binary codes (like `01`) to high-frequency characters (like 'e') and **long** binary codes (like `11011`) to low-frequency characters (like 'z').

### What data structure is used to implement Huffman coding?

A **Min-Heap (or Priority Queue)**. This data structure is essential to _efficiently_ find the two nodes with the minimum frequencies at each step.

### Explain how frequency of characters affects the code.

- **High Frequency** (e.g., 'a', 'e'): These characters end up at the _top_ of the Huffman tree (close to the root). This gives them a **short path**, and thus a **short code**.
    
- **Low Frequency** (e.g., 'q', 'z'): These characters end up at the _bottom_ of the tree (far from the root). This gives them a **long path**, and thus a **long code**.
    

### What is the time complexity of Huffman coding?

For $n$ characters:

1. **Building the Min-Heap:** $O(n)$
    
2. **Merging Loop:** The loop runs $n-1$ times. Each iteration involves:
    
    - `extract-min()` (twice): $O(\log n)$
        
    - `insert()` (once): $O(\log n)$
        

- **Total Time Complexity:** $O(n \log n)$.
    

### What is a prefix-free code?

A code in which **no codeword is a prefix of any other codeword**.

- **Example:** If `a = 01`, then `b` _cannot_ be `010` (because `01` is a prefix).
    
- **Why?** This property guarantees **unambiguous decoding**. When decoding `010110`, the decoder sees `01` (that's 'a'), then `01` (that's 'a'), then `10` (that's 'c'). There's never any doubt.
    

### Why does Huffman coding produce an optimal code?

It's proven to produce the optimal prefix-free code. The greedy choice of merging the two lowest frequencies _always_ leads to the minimum possible total weighted path length, which is the goal.

### Compare fixed-length and variable-length encoding.

- **Fixed-Length (e.g., ASCII):** Every character uses the same number of bits (e.g., 8 bits). 'e' takes 8 bits, 'z' takes 8 bits. Simple, but inefficient.
    
- **Variable-Length (e.g., Huffman):** Code length varies. 'e' might take 2 bits, 'z' might take 10. This is far more efficient for compression, as common characters take up less space.
    

### What is the difference between Huffman coding and run-length encoding?

They are both compression, but they work differently.

- **Huffman Coding:** A **statistical** method. It compresses based on the _frequency_ of individual symbols.
    
- Run-Length Encoding (RLE): Compresses runs of identical data. (e.g., AAAAABBB becomes A5B3).
    
    They are often used together (e.g., RLE first, then Huffman).
    

### What is the role of min-heap in Huffman coding?

Its role is **speed**. It allows the algorithm to find the two nodes with the minimum frequency in $O(\log n)$ time. Without a heap (e.g., just searching a list), this step would take $O(n)$, making the whole algorithm $O(n^2)$.

### Explain how Huffman tree is constructed.

1. Create a leaf node for each character, weighted by its frequency.
    
2. Place all leaf nodes into a min-heap.
    
3. While the heap has more than one node:
    
    a. extract-min() (this is node A).
    
    b. extract-min() (this is node B).
    
    c. Create a new internal node with frequency = A.freq + B.freq.
    
    d. Make A the left child and B the right child.
    
    e. insert() this new internal node back into the heap.
    
4. The last node remaining in the heap is the **root** of the Huffman tree.
    

### How is the encoded message generated from the Huffman tree?

1. **Create a lookup table:** Traverse the tree from the root. Assign '0' to left branches and '1' to right branches. The path from the root to a character's leaf is its binary code (e.g., Left, Right, Left = `010`).
    
2. **Encode:** Read the original message, character by character, and replace each one with its code from the lookup table.
    

### What are real-world applications of Huffman coding?

It's a fundamental part of many compression standards:

- File formats like **.zip**, **.gzip**, **.png**, and **.jpeg**.
    
- Media formats like **.mp3**.
    
- Network protocols like **HTTP/2** for header compression.
    

### Compare Huffman coding with Shannon-Fano coding.

Both are variable-length encoding methods based on frequency.

- **Shannon-Fano:** Is **top-down**. It recursively _splits_ the set of characters into two groups of (roughly) equal total frequency. It is _not_ guaranteed to be optimal.
    
- **Huffman:** Is **bottom-up**. It _merges_ the two lowest-frequency nodes. It _is_ guaranteed to be optimal.