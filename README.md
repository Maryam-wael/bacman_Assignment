============================================================
ITML601 - Advanced AI and NLP
Assignment 1: Search and Adversarial Search in Pacman
------------------------------------------------------------
Team members:
  [Sughra Hassan ] - [20165579 ]
  [Maryam Wael] - [20174867]
  [Qabas Elayan] - [20174119]

Date: [1 - 11 - 2026]
============================================================

CONTENTS OF THIS SUBMISSION
------------------------------------------------------------
  search.py         - DFS, BFS, UCS, A* graph search (Part A, Q1-Q4)
  searchAgents.py   - CornersProblem, cornersHeuristic, foodHeuristic,
                      ClosestDotSearchAgent (Part A, Q5-Q8)
  multiAgents.py    - MinimaxAgent, AlphaBetaAgent, ExpectimaxAgent,
                      betterEvaluationFunction (Part B, Q2-Q5)

TESTED ENVIRONMENT
------------------------------------------------------------
  Python 3.12, Windows 11
  Berkeley CS188 Pacman projects (sp24): Project 1 + Project 2
  (kept in separate folders, as required)

AUTOGRADER SCORES OBTAINED (python autograder.py --no-graphics)
------------------------------------------------------------

PART A - SEARCH (folder: search)
  Question q1 (DFS):                3/3
  Question q2 (BFS):                3/3
  Question q3 (UCS):                3/3
  Question q4 (A*):                 3/3
  Question q5 (CornersProblem):     3/3
  Question q6 (cornersHeuristic):   3/3   (heuristic: 393 nodes on mediumCorners)
  Question q7 (foodHeuristic):        5/4   EXTRA CREDIT
                                    (410 nodes on trickySearch; thresholds 15000/12000/9000/7000)
  Question q8 (ClosestDotSearchAgent): 3/3

PART B - MULTI-AGENT SEARCH (folder: multiagent)
  Question q1 (ReflexAgent):        warmup - not graded (left as provided)
  Question q2 (MinimaxAgent):       5/5
  Question q3 (AlphaBetaAgent):     5/5
  Question q4 (ExpectimaxAgent):    5/5
  Question q5 (betterEvaluationFunction): 6/6
                                    (10/10 wins, average score 1123.5 on smallClassic)

HOW TO REPRODUCE
------------------------------------------------------------
Search tests (run from the 'search' folder):
  python autograder.py -q q1 --no-graphics
  ...
  python autograder.py --no-graphics

Multi-agent tests (run from the 'multiagent' folder):
  python autograder.py --no-graphics

Sample visual runs:
  python pacman.py -l bigMaze -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic -z .5
  python pacman.py -l mediumCorners -p AStarCornersAgent -z .5
  python pacman.py -l trickySearch -p AStarFoodSearchAgent -q
  python pacman.py -p AlphaBetaAgent -l minimaxClassic -a depth=3 --frameTime 1
  python pacman.py -p ExpectimaxAgent -l trappedClassic -a depth=3 -q -n 10

NOTES
------------------------------------------------------------
- A* handles inconsistent heuristics via best-g tracking with
  re-expansion (stale entries skipped), as required by the autograder.
- foodHeuristic uses an MST lower bound over {position} U remaining food
  with cached maze distances (food-food computed once, position-food on demand).
- betterEvaluationFunction: score - 4*food + 10/(d+1) nearest-food reward,
  ghost cliff penalties (-200 at d<=1, -50 at d=2), +20/(d+1) scared-ghost
  attraction, -15 per remaining capsule, with +/-inf terminal values.
- No debug prints remain in the submitted code.
============================================================