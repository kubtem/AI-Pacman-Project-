# Artificial-Intelligence
Solutions to projects in Berkeley CS188 Artificial Intelligence

This was a course at edx.org as an introduction to artificial intelligence. This repo contains solutions to the three projects assigned. Each project is showcased as a Pacman game where the student implements algorithms to win the game.

After cloning this repo, you can follow the links of each project to find in each project folder where the algorithms are implemented. All of the solutions are implemented by me and can be found under: "*** YOUR CODE HERE ***" of specific files.

You can also work through the problems yourself! The project description also shows you how to run various game simulations so you can see the AI algorithms in action before your very eyes :)

## Project 1 - Search
### Project 1 description

This project deals with search algorithms in AI. The implemented search algorithms will help Pacman traverse through the game board.

#### This project covers:
- Depth First Search
- Breadth First Search
- Uniform Cost Search
- A* Search
- Heuristic Techniques
      
![Pacman in a maze](https://inst.eecs.berkeley.edu/~cs188/fa24/assets/projects/maze.png)


<ul id="markdown-toc">
  <li><a href="#introduction" id="markdown-toc-introduction">Introduction</a></li>
  <li><a href="#welcome-to-pacman" id="markdown-toc-welcome-to-pacman">Welcome to Pacman</a></li>
  <li><a href="#new-syntax" id="markdown-toc-new-syntax">New Syntax</a></li>
  <li><a href="#q1-3-pts-finding-a-fixed-food-dot-using-depth-first-search-lecture-2" id="markdown-toc-q1-3-pts-finding-a-fixed-food-dot-using-depth-first-search-lecture-2">Q1 (3 pts): Finding a Fixed Food Dot using Depth First Search (Lecture 2)</a></li>
  <li><a href="#q2-3-pts-breadth-first-search-lecture-2" id="markdown-toc-q2-3-pts-breadth-first-search-lecture-2">Q2 (3 pts): Breadth First Search (Lecture 2)</a></li>
  <li><a href="#q3-3-pts-varying-the-cost-function-lecture-2" id="markdown-toc-q3-3-pts-varying-the-cost-function-lecture-2">Q3 (3 pts): Varying the Cost Function (Lecture 2)</a></li>
  <li><a href="#q4-3-pts-a-search-lecture-3" id="markdown-toc-q4-3-pts-a-search-lecture-3">Q4 (3 pts): A* search (Lecture 3)</a></li>
  <li><a href="#q5-3-pts-finding-all-the-corners-lecture-3" id="markdown-toc-q5-3-pts-finding-all-the-corners-lecture-3">Q5 (3 pts): Finding All the Corners (Lecture 3)</a></li>
  <li><a href="#q6-3-pts-corners-problem-heuristic-lecture-3" id="markdown-toc-q6-3-pts-corners-problem-heuristic-lecture-3">Q6 (3 pts): Corners Problem: Heuristic (Lecture 3)</a></li>
  <li><a href="#q7-4-pts-eating-all-the-dots" id="markdown-toc-q7-4-pts-eating-all-the-dots">Q7 (4 pts): Eating All The Dots</a></li>
  <li><a href="#q8-3-pts-suboptimal-search" id="markdown-toc-q8-3-pts-suboptimal-search">Q8 (3 pts): Suboptimal Search</a></li>
</ul><hr>
<h2 id="introduction">
  
# Introduction
  
  
</h2>
    

<p>In this project, your Pacman agent will find paths through his maze world, both to reach a particular location and to collect food efficiently. You will build general search algorithms and apply them to Pacman scenarios.</p>

<p>This project includes an autograder for you to grade your answers on your machine. This can be run with the command:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>


The code for this project consists of several Python files, some of which you will need to read and understand in order to complete the assignment, and some of which you can ignore. You can download all the code and supporting files as a [search.zip](https://inst.eecs.berkeley.edu/~cs188/fa24/assets/projects/search.zip).

<div class="table-wrapper"><table>
    <tbody>
      <tr>
        <td colspan="2"><b>Files you'll edit:</b></td>
      </tr>
      <tr>
        <td><code>search.py</code></td>
        <td>Where all of your search algorithms will reside.</td>
      </tr>
      <tr>
        <td><code>searchAgents.py</code></td>
        <td>Where all of your search-based agents will reside.</td>
      </tr>
      <tr>
        <td colspan="2"><b>Files you might want to look at:</b></td>
      </tr>
      <tr>
        <td><code>pacman.py</code></td>
        <td>The main file that runs Pacman games. This file describes a Pacman GameState type, which you use in this project.</td>
      </tr>
      <tr>
        <td><code>game.py</code></td>
        <td>The logic behind how the Pacman world works. This file describes several supporting types like AgentState, Agent, Direction, and Grid.</td>
      </tr>
      <tr>
        <td><code>util.py</code></td>
        <td>Useful data structures for implementing search algorithms.</td>
      </tr>
      <tr>
        <td colspan="2"><b>Supporting files you can ignore:</b></td>
      </tr>
      <tr>
        <td><code>graphicsDisplay.py</code></td>
        <td>Graphics for Pacman</td>
      </tr>
      <tr>
        <td><code>graphicsUtils.py</code></td>
        <td>Support for Pacman graphics</td>
      </tr>
      <tr>
        <td><code>textDisplay.py</code></td>
        <td>ASCII graphics for Pacman</td>
      </tr>
      <tr>
        <td><code>ghostAgents.py</code></td>
        <td>Agents to control ghosts</td>
      </tr>
      <tr>
        <td><code>keyboardAgents.py</code></td>
        <td>Keyboard interfaces to control Pacman</td>
      </tr>
      <tr>
        <td><code>layout.py</code></td>
        <td>Code for reading layout files and storing their contents</td>
      </tr>
      <tr>
        <td><code>autograder.py</code></td>
        <td>Project autograder</td>
      </tr>
      <tr>
        <td><code>testParser.py</code></td>
        <td>Parses autograder test and solution files</td>
      </tr>
      <tr>
        <td><code>testClasses.py</code></td>
        <td>General autograding test classes</td>
      </tr>
      <tr>
        <td><code>test_cases/</code></td>
        <td>Directory containing the test cases for each question</td>
      </tr>
      <tr>
        <td><code>searchTestClasses.py</code></td>
        <td>Project 1 specific autograding test classes</td>
      </tr>
    </tbody>
  </table></div>

<p><strong>Discussion:</strong> Please be careful not to post spoilers.</p><hr>

# Welcome to Pacman
    
<p>After downloading the code, unzipping it, and changing to the directory, you should be able to play a game of Pacman by typing the following at the command line:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Pacman lives in a shiny blue world of twisting corridors and tasty round treats. Navigating this world efficiently will be Pacman’s first step in mastering his domain.</p>

<p>The simplest agent in <code class="language-plaintext highlighter-rouge">searchAgents.py</code> is called the <code class="language-plaintext highlighter-rouge">GoWestAgent</code>, which always goes West (a trivial reflex agent). This agent can occasionally win:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">--layout</span> testMaze <span class="nt">--pacman</span> GoWestAgent
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>But, things get ugly for this agent when turning is required:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">--layout</span> tinyMaze <span class="nt">--pacman</span> GoWestAgent
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>If Pacman gets stuck, you can exit the game by typing CTRL-c into your terminal.</p>

<p>Soon, your agent will solve not only <code class="language-plaintext highlighter-rouge">tinyMaze</code>, but any maze you want.</p>

<p>Note that <code class="language-plaintext highlighter-rouge">pacman.py</code> supports a number of options that can each be expressed in a long way (e.g., <code class="language-plaintext highlighter-rouge">--layout</code>) or a short way (e.g., <code class="language-plaintext highlighter-rouge">-l</code>). You can see the list of all options and their default values via:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-h</span>
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Also, all of the commands that appear in this project also appear in <code class="language-plaintext highlighter-rouge">commands.txt</code>, for easy copying and pasting. In UNIX/Mac OS X, you can even run all these commands in order with <code class="language-plaintext highlighter-rouge">bash commands.txt</code>.</p><hr>

# New Syntax

<p>You may not have seen this syntax before:</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="k">def</span> <span class="nf">my_function</span><span class="p">(</span><span class="n">a</span><span class="p">:</span> <span class="nb">int</span><span class="p">,</span> <span class="n">b</span><span class="p">:</span> <span class="n">Tuple</span><span class="p">[</span><span class="nb">int</span><span class="p">,</span> <span class="nb">int</span><span class="p">],</span> <span class="n">c</span><span class="p">:</span> <span class="n">List</span><span class="p">[</span><span class="n">List</span><span class="p">],</span> <span class="n">d</span><span class="p">:</span> <span class="n">Any</span><span class="p">,</span> <span class="n">e</span><span class="p">:</span> <span class="nb">float</span><span class="o">=</span><span class="mf">1.0</span><span class="p">):</span>
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>This is annotating the type of the arguments that Python should expect for this function. In the example below, <code class="language-plaintext highlighter-rouge">a</code> should be an <code class="language-plaintext highlighter-rouge">int</code> – integer, <code class="language-plaintext highlighter-rouge">b</code> should be a <code class="language-plaintext highlighter-rouge">tuple</code> of 2 <code class="language-plaintext highlighter-rouge">int</code>s, <code class="language-plaintext highlighter-rouge">c</code> should be a <code class="language-plaintext highlighter-rouge">List</code> of <code class="language-plaintext highlighter-rouge">Lists</code> of anything – therefore a 2D array of anything, <code class="language-plaintext highlighter-rouge">d</code> is essentially the same as not annotated and can by anything, and <code class="language-plaintext highlighter-rouge">e</code> should be a <code class="language-plaintext highlighter-rouge">float</code>. <code class="language-plaintext highlighter-rouge">e</code> is also set to 1.0 if nothing is passed in for it, i.e.:</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">my_function</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="p">(</span><span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">),</span> <span class="p">[[</span><span class="s">'a'</span><span class="p">,</span> <span class="s">'b'</span><span class="p">],</span> <span class="p">[</span><span class="bp">None</span><span class="p">,</span> <span class="n">my_class</span><span class="p">],</span> <span class="p">[[]]],</span> <span class="p">(</span><span class="s">'h'</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>The above call fits the type annotations, and doesn’t pass anything in for e. Type annotations are meant to be an adddition to the docstrings to help you know what the functions are working with. Python itself doesn’t enforce these. When writing your own functions, it is up to you if you want to annotate your types; they may be helpful to keep organized or not something you want to spend time on.</p><hr>
<h2 id="q1-3-pts-finding-a-fixed-food-dot-using-depth-first-search-lecture-2">
  
  
# Question 1 : Finding a Fixed Food Dot using Depth First Search 
  
<p>In <code class="language-plaintext highlighter-rouge">searchAgents.py</code>, you’ll find a fully implemented <code class="language-plaintext highlighter-rouge">SearchAgent</code>, which plans out a path through Pacman’s world and then executes that path step-by-step. The search algorithms for formulating a plan are not implemented – that’s your job.</p>

<p>First, test that the <code class="language-plaintext highlighter-rouge">SearchAgent</code> is working correctly by running:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> tinyMaze <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>tinyMazeSearch
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>The command above tells the <code class="language-plaintext highlighter-rouge">SearchAgent</code> to use <code class="language-plaintext highlighter-rouge">tinyMazeSearch</code> as its search algorithm, which is implemented in <code class="language-plaintext highlighter-rouge">search.py</code>. Pacman should navigate the maze successfully.</p>

<p>Now it’s time to write full-fledged generic search functions to help Pacman plan routes! Pseudocode for the search algorithms you’ll write can be found in the lecture slides. Remember that a search node must contain not only a state but also the information necessary to reconstruct the path (plan) which gets to that state.</p>

<p><strong>Important note</strong>: All of your search functions need to return a list of actions that will lead the agent from the start to the goal. These actions all have to be legal moves (valid directions, no moving through walls).</p>

<p><strong>Important note</strong>: Make sure to use the <code class="language-plaintext highlighter-rouge">Stack</code>, <code class="language-plaintext highlighter-rouge">Queue</code> and <code class="language-plaintext highlighter-rouge">PriorityQueue</code> data structures provided to you in <code class="language-plaintext highlighter-rouge">util.py</code>! These data structure implementations have particular properties which are required for compatibility with the autograder.</p>

<p><em>Hint</em>: Each algorithm is very similar. Algorithms for DFS, BFS, UCS, and A* differ only in the details of how the fringe is managed. So, concentrate on getting DFS right and the rest should be relatively straightforward. Indeed, one possible implementation requires only a single generic search method which is configured with an algorithm-specific queuing strategy. (Your implementation need not be of this form to receive full credit).</p>

<p>Implement the depth-first search (DFS) algorithm in the <code class="language-plaintext highlighter-rouge">depthFirstSearch</code> function in <code class="language-plaintext highlighter-rouge">search.py</code>. To make your algorithm complete, write the graph search version of DFS, which avoids expanding any already visited states.</p>

<p>Your code should quickly find a solution for:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> tinyMaze <span class="nt">-p</span> SearchAgent
python pacman.py <span class="nt">-l</span> mediumMaze <span class="nt">-p</span> SearchAgent
python pacman.py <span class="nt">-l</span> bigMaze <span class="nt">-z</span> .5 <span class="nt">-p</span> SearchAgent
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>The Pacman board will show an overlay of the states explored, and the order in which they were explored (brighter red means earlier exploration). Is the exploration order what you would have expected? Does Pacman actually go to all the explored squares on his way to the goal?</p>

<p>Hint: If you use a <code class="language-plaintext highlighter-rouge">Stack</code> as your data structure, the solution found by your DFS algorithm for <code class="language-plaintext highlighter-rouge">mediumMaze</code> should have a length of 130 (provided you push successors onto the fringe in the order provided by getSuccessors; you might get 246 if you push them in the reverse order). Is this a least cost solution? If not, think about what depth-first search is doing wrong.</p>

<p><em>Grading</em>: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q1
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q2-3-pts-breadth-first-search-lecture-2">
  
# Question 2 : Breadth First Search

<p>Implement the breadth-first search (BFS) algorithm in the <code class="language-plaintext highlighter-rouge">breadthFirstSearch</code> function in <code class="language-plaintext highlighter-rouge">search.py</code>. Again, write a graph search algorithm that avoids expanding any already visited states. Test your code the same way you did for depth-first search.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> mediumMaze <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>bfs
python pacman.py <span class="nt">-l</span> bigMaze <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>bfs <span class="nt">-z</span> .5
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Does BFS find a least cost solution? If not, check your implementation.</p>

<p><em>Hint</em>: If Pacman moves too slowly for you, try the option –frameTime 0.</p>

<p><em>Note</em>: If you’ve written your search code generically, your code should work equally well for the eight-puzzle search problem without any changes.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python eightpuzzle.py
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Grading: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q2
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q3-3-pts-varying-the-cost-function-lecture-2">
 
  
# QQuestion 3 : Varying the Cost Function 

<p>While BFS will find a fewest-actions path to the goal, we might want to find paths that are “best” in other senses. Consider <code class="language-plaintext highlighter-rouge">mediumDottedMaze</code> and <code class="language-plaintext highlighter-rouge">mediumScaryMaze</code>.</p>

<p>By changing the cost function, we can encourage Pacman to find different paths. For example, we can charge more for dangerous steps in ghost-ridden areas or less for steps in food-rich areas, and a rational Pacman agent should adjust its behavior in response.</p>

<p>Implement the uniform-cost graph search algorithm in the <code class="language-plaintext highlighter-rouge">uniformCostSearch</code> function in <code class="language-plaintext highlighter-rouge">search.py</code>. We encourage you to look through <code class="language-plaintext highlighter-rouge">util.py</code> for some data structures that may be useful in your implementation. You should now observe successful behavior in all three of the following layouts, where the agents below are all UCS agents that differ only in the cost function they use (the agents and cost functions are written for you):</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> mediumMaze <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>ucs
python pacman.py <span class="nt">-l</span> mediumDottedMaze <span class="nt">-p</span> StayEastSearchAgent
python pacman.py <span class="nt">-l</span> mediumScaryMaze <span class="nt">-p</span> StayWestSearchAgent
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p><em>Note</em>: You should get very low and very high path costs for the <code class="language-plaintext highlighter-rouge">StayEastSearchAgent</code> and <code class="language-plaintext highlighter-rouge">StayWestSearchAgent</code> respectively, due to their exponential cost functions (see <code class="language-plaintext highlighter-rouge">searchAgents.py</code> for details).</p>

<p>Grading: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q3
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q4-3-pts-a-search-lecture-3">
  
  
# Question 4 : A* search 

<p>Implement A* search in the empty function <code class="language-plaintext highlighter-rouge">aStarSearch</code> in <code class="language-plaintext highlighter-rouge">search.py</code>. A* takes a heuristic function as an argument. Heuristics take two arguments: a state in the search problem (the main argument), and the problem itself (for reference information). The <code class="language-plaintext highlighter-rouge">nullHeuristic</code> heuristic function in <code class="language-plaintext highlighter-rouge">search.py</code> is a trivial example.</p>

<p>You can test your A* implementation on the original problem of finding a path through a maze to a fixed position using the Manhattan distance heuristic (implemented already as <code class="language-plaintext highlighter-rouge">manhattanHeuristic</code> in <code class="language-plaintext highlighter-rouge">searchAgents.py</code>).</p>

<p>Hint: In addition to keeping track of the visited state, you may also want to keep track of the best path cost to that state so far. Some nodes may need to be expanded more than once to find the optimal path.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> bigMaze <span class="nt">-z</span> .5 <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>astar,heuristic<span class="o">=</span>manhattanHeuristic
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>You should see that A* finds the optimal solution slightly faster than uniform cost search (about 549 vs. 620 search nodes expanded in our implementation, but ties in priority may make your numbers differ slightly). What happens on <code class="language-plaintext highlighter-rouge">openMaze</code> for the various search strategies?</p>

<p><em>Grading</em>: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q4
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q5-3-pts-finding-all-the-corners-lecture-3">
  
  
# Question 5 : Finding All the Corners

<p>The real power of A* will only be apparent with a more challenging search problem. Now, it’s time to formulate a new problem and design a heuristic for it.</p>

<p>In corner mazes, there are four dots, one in each corner. Our new search problem is to find the shortest path through the maze that touches all four corners (whether the maze actually has food there or not). Note that for some mazes like <code class="language-plaintext highlighter-rouge">tinyCorners</code>, the shortest path does not always go to the closest food first! Hint: the shortest path through <code class="language-plaintext highlighter-rouge">tinyCorners</code> takes 28 steps.</p>

<p><em>Note</em>: Make sure to complete Question 2 before working on Question 5, because Question 5 builds upon your answer for Question 2.</p>

<p>Implement the <code class="language-plaintext highlighter-rouge">CornersProblem</code> search problem in <code class="language-plaintext highlighter-rouge">searchAgents.py</code>. You will need to choose a state representation that encodes all the information necessary to detect whether all four corners have been reached. Now, your search agent should solve:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> tinyCorners <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>bfs,prob<span class="o">=</span>CornersProblem
python pacman.py <span class="nt">-l</span> mediumCorners <span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>bfs,prob<span class="o">=</span>CornersProblem
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>To receive full credit, you need to define an abstract state representation that does not encode irrelevant information (like the position of ghosts, where extra food is, etc.). In particular, do not use a Pacman <code class="language-plaintext highlighter-rouge">GameState</code> as a search state. Your code will be very, very slow if you do (and also wrong).</p>

<p>An instance of the <code class="language-plaintext highlighter-rouge">CornersProblem</code> class represents an entire search problem, not a particular state. Particular states are returned by the functions you write, and your functions return a data structure of your choosing (e.g. tuple, set, etc.) that represents a state.</p>

<p>Furthermore, while a program is running, remember that many states simultaneously exist, all on the queue of the search algorithm, and they should be independent of each other. In other words, you should not have only one state for the entire <code class="language-plaintext highlighter-rouge">CornersProblem</code> object; your class should be able to generate many different states to provide to the search algorithm.</p>

<p><em>Hint 1</em>: The only parts of the game state you need to reference in your implementation are the starting Pacman position and the location of the four corners.</p>

<p><em>Hint 2</em>: When coding up <code class="language-plaintext highlighter-rouge">getSuccessors</code>, make sure to add children to your successors list with a cost of 1.</p>

<p>Our implementation of <code class="language-plaintext highlighter-rouge">breadthFirstSearch</code> expands just under 2000 search nodes on <code class="language-plaintext highlighter-rouge">mediumCorners</code>. However, heuristics (used with A* search) can reduce the amount of searching required.</p>

<p>Grading: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q5
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q6-3-pts-corners-problem-heuristic-lecture-3">
  
# Question 6 : Corners Problem: Heuristic

<p><em>Note</em>: Make sure to complete Question 4 before working on Question 6, because Question 6 builds upon your answer for Question 4.</p>

<p>Implement a non-trivial heuristic for the <code class="language-plaintext highlighter-rouge">CornersProblem</code> in <code class="language-plaintext highlighter-rouge">cornersHeuristic</code>.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> mediumCorners <span class="nt">-p</span> AStarCornersAgent <span class="nt">-z</span> 0.5
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Note: <code class="language-plaintext highlighter-rouge">AStarCornersAgent</code> is a shortcut for</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>aStarSearch,prob<span class="o">=</span>CornersProblem,heuristic<span class="o">=</span>cornersHeuristic
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p><strong>Admissibility</strong>: Remember, heuristics are just functions that take search states and return numbers that estimate the cost to a nearest goal. More effective heuristics will return values closer to the actual goal costs. To be <em>admissible</em>, the heuristic values must be lower bounds on the actual shortest path cost to the nearest goal (and non-negative).</p>

<p><strong>Non-Trivial Heuristics</strong>: The trivial heuristics are the ones that return zero everywhere (UCS) and the heuristic which computes the true completion cost. The former won’t save you any time, while the latter will timeout the autograder. You want a heuristic which reduces total compute time, though for this assignment the autograder will only check node counts (aside from enforcing a reasonable time limit).</p>

<p><strong>Grading</strong>: Your heuristic must be a non-trivial non-negative heuristic to receive any points. Make sure that your heuristic returns 0 at every goal state and never returns a negative value. Depending on how few nodes your heuristic expands, you’ll be graded:</p>

<div class="table-wrapper"><table>
    <thead>
        <tr><th>Number of nodes expanded</th>
        <th>Grade</th>
    </tr></thead>
    <tbody>
      <tr>
        <td>more than 2000</td>
        <td>0/3</td>
      </tr>
      <tr>
        <td>at most 2000</td>
        <td>1/3</td>
      </tr>
      <tr>
        <td>at most 1600</td>
        <td>2/3</td>
      </tr>
      <tr>
        <td>at most 1200</td>
        <td>3/3</td>
      </tr>
    </tbody>
  </table></div>

<p>Grading: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q6
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q7-4-pts-eating-all-the-dots">
  
# Question 7 : Eating All The Dots  

<p>Now we’ll solve a hard search problem: eating all the Pacman food in as few steps as possible. For this, we’ll need a new search problem definition which formalizes the food-clearing problem: <code class="language-plaintext highlighter-rouge">FoodSearchProblem</code> in <code class="language-plaintext highlighter-rouge">searchAgents.py</code> (implemented for you). A solution is defined to be a path that collects all of the food in the Pacman world. For the present project, solutions do not take into account any ghosts or power pellets; solutions only depend on the placement of walls, regular food and Pacman. (Of course ghosts can ruin the execution of a solution! We’ll get to that in the next project.) If you have written your general search methods correctly, A* with a null heuristic (equivalent to uniform-cost search) should quickly find an optimal solution to <code class="language-plaintext highlighter-rouge">testSearch</code> with no code change on your part (total cost of 7).</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> testSearch <span class="nt">-p</span> AStarFoodSearchAgent
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Note: <code class="language-plaintext highlighter-rouge">AStarFoodSearchAgent</code> is a shortcut for</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="nt">-p</span> SearchAgent <span class="nt">-a</span> <span class="nv">fn</span><span class="o">=</span>astar,prob<span class="o">=</span>FoodSearchProblem,heuristic<span class="o">=</span>foodHeuristic
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>You should find that UCS starts to slow down even for the seemingly simple <code class="language-plaintext highlighter-rouge">tinySearch</code>. As a reference, our implementation takes 2.5 seconds to find a path of length 27 after expanding 5057 search nodes.</p>

<p><em>Note</em>: Make sure to complete Question 4 before working on Question 7, because Question 7 builds upon your answer for Question 4.</p>

<p>Fill in <code class="language-plaintext highlighter-rouge">foodHeuristic</code> in <code class="language-plaintext highlighter-rouge">searchAgents.py</code> with a heuristic for the <code class="language-plaintext highlighter-rouge">FoodSearchProblem</code>. Try your agent on the <code class="language-plaintext highlighter-rouge">trickySearch</code> board:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> trickySearch <span class="nt">-p</span> AStarFoodSearchAgent
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p>Our UCS agent finds the optimal solution in about 13 seconds, exploring over 16,000 nodes.</p>

<p>Any non-trivial non-negative heuristic will receive 1 point. Make sure that your heuristic returns 0 at every goal state and never returns a negative value. Depending on how few nodes your heuristic expands, you’ll get additional points:</p>

<div class="table-wrapper"><table>
    <thead>
        <tr><th>Number of nodes expanded</th>
        <th>Grade</th>
    </tr></thead>
    <tbody>
      <tr>
        <td>more than 15000</td>
        <td>1/4</td>
      </tr>
      <tr>
        <td>at most 15000</td>
        <td>2/4</td>
      </tr>
      <tr>
        <td>at most 12000</td>
        <td>3/4</td>
      </tr>
      <tr>
        <td>at most 9000</td>
        <td>4/4 (full credit; medium)</td>
      </tr>
      <tr>
        <td>at most 7000</td>
        <td>5/4 (optional extra credit; hard)</td>
      </tr>
    </tbody>
</table></div>

<p>Grading: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q7
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="q8-3-pts-suboptimal-search">
  
  
# Question 8 : Suboptimal Search 

<p>Sometimes, even with A* and a good heuristic, finding the optimal path through all the dots is hard. In these cases, we’d still like to find a reasonably good path, quickly. In this section, you’ll write an agent that always greedily eats the closest dot. <code class="language-plaintext highlighter-rouge">ClosestDotSearchAgent</code> is implemented for you in <code class="language-plaintext highlighter-rouge">searchAgents.py</code>, but it’s missing a key function that finds a path to the closest dot.</p>

<p>Implement the function <code class="language-plaintext highlighter-rouge">findPathToClosestDot</code> in <code class="language-plaintext highlighter-rouge">searchAgents.py</code>. Our agent solves this maze (suboptimally!) in under a second with a path cost of 350:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python pacman.py <span class="nt">-l</span> bigSearch <span class="nt">-p</span> ClosestDotSearchAgent <span class="nt">-z</span> .5
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div>

<p><em>Hint</em>: The quickest way to complete <code class="language-plaintext highlighter-rouge">findPathToClosestDot</code> is to fill in the <code class="language-plaintext highlighter-rouge">AnyFoodSearchProblem</code>, which is missing its goal test. Then, solve that problem with an appropriate search function. The solution should be very short!</p>

<p>Your <code class="language-plaintext highlighter-rouge">ClosestDotSearchAgent</code> won’t always find the shortest possible path through the maze. Make sure you understand why and try to come up with a small example where repeatedly going to the closest dot does not result in finding the shortest path for eating all the dots.</p>

<p>Grading: Please run the below command to see if your implementation passes all the autograder test cases.</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight"><code>python autograder.py <span class="nt">-q</span> q8
</code></pre></div><button type="button" aria-label="Copy code to clipboard"><svg viewBox="0 0 24 24" class="copy-icon"><use xlink:href="#svg-copy"></use></svg></button></div><hr>
<h2 id="submission">
  
 
