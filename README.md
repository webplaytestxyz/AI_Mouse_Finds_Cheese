
<h1>AI Mouse Finds Cheese — Q-Learning Demo</h1>

<p>A polished, single-file browser demo that teaches core reinforcement-learning concepts with an adorable visual: a mouse learns to find cheese in procedurally generated mazes using tabular Q-learning. Ready-to-run, highly hackable, and ideal for demos, teaching, quick experiments, or as a starting point for sim-to-real robotics research.</p>

<h2>Why this repo matters</h2>
<ul>
  <li>Learn reinforcement learning basics with immediate visual feedback.</li>
  <li>Observe exploration, pathfinding, reward shaping, and value propagation in action.</li>
  <li>Small, self-contained codebase (single HTML file) — easy to modify and extend.</li>
  <li>Perfect for classroom demos, portfolio projects, or RL-to-robot workflow prototypes.</li>
</ul>

<h2>Live demo</h2>
<ul>
  <li>Open <code>index.html</code> in any modern browser (no server required).</li>
  <li>On Windows: double-click the file or run <code>start index.html</code> from the folder containing the file.</li>
  <li>On macOS / Linux: double-click the file or open it via the browser’s “Open File” dialog.</li>
</ul>

<h2>Quick highlights</h2>
<ul>
  <li>Procedural maze generation (recursive backtracker).</li>
  <li>Tabular Q-learning (state = grid cell, actions = 4 cardinal moves).</li>
  <li>Real-time rendering: maze, agent, Q-value heatmap, and greedy path overlay.</li>
  <li>Interactive UI: episodes/sec, max steps/episode, exploration (ε), Start/Pause/Reset Q.</li>
  <li>Metrics: Confidence Level (%), episodes, collisions, best steps.</li>
</ul>

<h2>What this demo teaches about AI and robotics</h2>

<h3>Reinforcement learning fundamentals</h3>
<ul>
  <li>Q-table representation of state-action values and Bellman updates.</li>
  <li>Exploration vs. exploitation via ε-greedy policy.</li>
  <li>Reward shaping: goal reward, collision penalty, step penalty.</li>
</ul>

<h3>Practical limitations & lessons</h3>
<ul>
  <li>Tabular Q-learning scales only to small discrete spaces — neural approximators are needed for real sensors (vision, lidar).</li>
  <li>Sample inefficiency: real robots require massive data, simulators, or sample-efficient algorithms.</li>
  <li>Safety & sim-to-real gap: policies learned in clean simulators can fail on real hardware unless noise, dynamics, and domain randomization are addressed.</li>
</ul>

<h3>Relevance & future directions</h3>
<ul>
  <li>Demonstrates navigation and goal-directed behavior, foundational to mobile robots.</li>
  <li>Natural next steps: DQN / policy-gradient methods, representation learning for sensor inputs, hierarchical RL, safe RL with constraints.</li>
  <li>Combining learned policies with classical planners, model-based methods, and on-device lightweight inference unlocks practical autonomy for edge robots.</li>
</ul>

<h2>Confidence Level (%)</h2>
<ul>
  <li>Metric: running success rate = <code>successCount / totalEpisodes</code> (rounded to percent).</li>
  <li>Updated at the end of every episode in <code>index.html</code> (variables <code>successCount</code>, <code>totalEpisodes</code>, and <code>confidence</code> element).</li>
  <li>Interpretation: quick indicator of learned policy reliability. Resetting Q-values does not reset this metric (refresh page or modify code to reset counters).</li>
</ul>

<h2>Getting started</h2>
<ul>
  <li>Open the folder containing <code>index.html</code>.</li>
  <li>Open <code>index.html</code> in any modern browser (double-click or use browser’s “Open File” feature).</li>
  <li>Use the UI to adjust:
    <ul>
      <li>Episodes per second, Max steps/episode, Exploration (ε).</li>
      <li>Start → watch the mouse learn in real time. Pause / Reset Q as needed.</li>
      <li>Double-click the canvas to regenerate maze and randomize start/goal.</li>
    </ul>
  </li>
</ul>

<h2>Controls & UI overview</h2>
<ul>
  <li><strong>Start:</strong> begin asynchronous episode loop (reads sliders on start).</li>
  <li><strong>Pause:</strong> stop the runner.</li>
  <li><strong>Reset Q:</strong> clear Q-table and best-step stat (does not clear confidence counters).</li>
  <li><strong>Sliders:</strong> episodes/sec, max steps/episode, exploration (ε).</li>
  <li><strong>Canvas:</strong> shows maze, start (orange dot), goal (🧀), mouse (🐭), Q-value heat, greedy path.</li>
</ul>

<h2>Suggested experiments (fast wins)</h2>
<ul>
  <li>Anneal ε over time: gradually move from exploration → exploitation.</li>
  <li>Increase max steps or reduce step penalty for sparse-goal mazes.</li>
  <li>Replace tabular Q with a small neural network (DQN) to scale to larger state spaces.</li>
  <li>Serialize qTable to JSON for checkpointing and offline analysis.</li>
  <li>Add observation/action noise or domain randomization to study sim-to-real robustness.</li>
</ul>

<h2>Implementation notes & key functions</h2>
<ul>
  <li>Maze: <code>generateMaze(w,h)</code> (recursive backtracker).</li>
  <li>Tile constants: <code>TILE</code>, <code>GRID_W</code>, <code>GRID_H</code>, <code>WALL</code>, <code>EMPTY</code>, <code>GOAL_TILE</code>.</li>
  <li>Agent actions: <code>ACTIONS = [UP, RIGHT, DOWN, LEFT]</code>.</li>
  <li>Q-table helpers: <code>qKey(x,y)</code>, <code>ensureQ(pos)</code>, <code>resetQ()</code>, <code>qTable</code>.</li>
  <li>Learning loop: <code>runEpisodes()</code> (async), <code>chooseAction(pos)</code>, <code>stepEnvironment(pos,actionIndex)</code>, <code>qLearnUpdate(...)</code>.</li>
  <li>UI elements wired at bottom of <code>index.html</code>.</li>
  <li>Confidence metric: <code>successCount</code>, <code>totalEpisodes</code>, updated in <code>runEpisodes()</code>.</li>
</ul>

<h2>File structure</h2>
<ul>
  <li><code>index.html</code> — single-file demo with UI, maze generation, Q-learning, and rendering.</li>
  <li><code>README.md</code> — this document.</li>
</ul>

<h2>How to contribute</h2>
<ul>
  <li>Fork and submit PRs: suggest new reward schemes, add DQN examples, introduce curriculum learning, or persistent checkpoints.</li>
  <li>Open issues for feature requests or bugs.</li>
</ul>

<h2>License</h2>
<p>MIT-style: friendly use encouraged. Keep attribution when sharing derivative work publicly.</p>

<h2>Contact & attribution</h2>
<p>Designed as a learning and demo project. Use in workshops, tutorials, or as a base for robotics research prototypes.</p>

<p>Enjoy exploring reinforcement learning — hack the code, run experiments, and imagine how these concepts scale toward robust autonomy in future robots.</p>

</body>
</html>
