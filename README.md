# Robot's Learning Landscape - 3D Reinforcement Learning Visualization

## Overview

This project is a single HTML file containing an interactive 3D simulation designed to visually demonstrate the core concepts of Reinforcement Learning (RL). It features a simple "robot" agent exploring a 4x4 grid world, learning to find a goal (reward) while avoiding traps and obstacles. The learning process is visualized through a dynamic 3D landscape where terrain height and color represent learned values, alongside a worksheet showing precise Q-values.

This simulation is particularly geared towards educational purposes, aiming to make RL concepts tangible and understandable for students (suggested Grade 4+).

## Core Concepts Demonstrated

*   **State (s):** Where the agent is currently located on the grid. Represented by the robot's position on a specific pillar and the `(r,c)` coordinates shown in the 3D label and worksheet.
*   **Action (a):** The decision the agent makes: Move UP, DOWN, LEFT, or RIGHT. Shown in the Log Book and implicitly chosen during exploration or testing.
*   **Reward (R):** The points received for taking an action in a state.
    *   `+10` for reaching the Goal (Gold Pillar).
    *   `-10` for falling into a Trap (Red Pillar).
    *   `-1` for stepping into Mud (Brown Pillar).
    *   `-1` for hitting a Wall (Dark Grey Pillar) or the grid edge.
    *   `0` for stepping onto an Empty (Light Grey/Green/Red) or Start (Blue) pillar.
*   **Policy (π):** The robot's strategy or plan – which action it thinks is best to take from each state.
    *   Visualized by the **brightly colored arrow** on top of each pillar, pointing in the learned best direction.
    *   Also represented textually in the last column of the **Worksheet Table**.
*   **Value (Q-Value / State Value):** The long-term expected reward or "goodness" the robot has learned for being in a state, or for taking a specific action from a state.
    *   **Pillar Height & Color:** The height and color (Red = Bad, Grey = Neutral, Green = Good) of each pillar visually represent the *maximum Q-value* (overall value) learned for that state. This creates the "learning landscape."
    *   **Worksheet Scores:** The table explicitly shows the learned Q-value (Smartness Score) for *each specific action* (Up, Down, Left, Right) from each state.

## Features

*   **Interactive 3D Grid:** Uses Three.js for a visually engaging blocky world.
*   **Dynamic Terrain:** Pillars representing grid cells grow taller/shorter and change color based on their learned value (`maxQ`).
*   **Clear Policy Visualization:** A distinct arrow on top of each pillar indicates the best action learned so far for that state.
*   **Coordinate & Value Labels:** Hovering text labels in the 3D view show the `(r,c)` coordinates and the current `maxQ` value for each pillar.
*   **Linked Worksheet:** A table displays the numerical Q-values for every state-action pair, updating live.
*   **Visual Learning Feedback:**
    *   Worksheet cells flash yellow when their Q-value updates.
    *   The corresponding 3D pillar briefly flashes white when *any* of its Q-values update.
    *   The policy arrow on the pillar flashes when the *best* action for that state changes.
*   **Narrative Log Book:** Records the robot's actions, received rewards, and key events step-by-step.
*   **Exploration Mode:** The robot chooses actions randomly to discover the environment.
*   **Policy Test Mode:** The robot follows its learned policy (the arrows) to see how well it performs. Includes a step limit to prevent infinite loops.
*   **Batch Episode Runner:** Run many exploration episodes quickly to accelerate learning.
*   **Randomize World:** Generate a new grid layout with random placements for goal, traps, etc.
*   **Controls:** Step-by-step execution, auto-run, speed control, learning visualization toggle, reset options.
*   **Confetti Celebration:** A visual reward when the robot reaches the goal!

## How to Use

1.  **Save:** Save the complete code as an HTML file (e.g., `robot_landscape.html`).
2.  **Open:** Open the HTML file in a modern web browser (like Chrome, Firefox, Edge).
3.  **Explore:**
    *   Use the mouse (click-drag, scroll wheel, right-click-drag) to orbit, zoom, and pan the 3D view.
    *   Click **"Step (Explore)"** to watch the robot take one random action and learn from it. Observe the Log Book, Worksheet, and 3D changes.
    *   Click **"Start Auto (Explore)"** to have the robot explore automatically. Use the **Speed** slider to adjust the pace. Click **"Stop Auto"** to pause.
    *   Click **"Run Explore"** after setting the number of **Episodes** to run many learning cycles quickly.
4.  **Observe Learning:**
    *   Make sure **"Show/Hide Learn"** is active (button appears pressed).
    *   Watch how pillar heights and colors change – green/tall pillars are "good," red/short pillars are "bad."
    *   Notice the arrows on top of pillars changing direction as the robot learns better paths.
    *   See how the scores update in the **Worksheet** and how the table flashes link to the flashing pillar in the 3D view.
5.  **Test the Plan:**
    *   After some exploration (e.g., running 50-100 episodes), click **"Test Best Plan"**.
    *   The robot will now follow the arrows. Observe if it efficiently reaches the goal or gets stuck.
6.  **Reset & Randomize:**
    *   **"Next Episode"** resets the robot's position but keeps the learned knowledge (Q-values and pillar heights/arrows).
    *   **"Reset All"** clears all learning and resets the world to its initial state.
    *   **"Randomize World"** creates a completely new maze layout and resets all learning.

## How it Demonstrates Reinforcement Learning

*   **Exploration vs. Exploitation:** The "Explore" modes show pure exploration (random actions). The "Test Best Plan" mode shows pure exploitation (following the learned policy). A key challenge in RL is balancing these two.
*   **Value Function:** The height/color of the pillars visually represents the learned state-value function (specifically, V(s) = max_a Q(s,a)). Students can see how value propagates from the goal (high value) backwards.
*   **Policy Improvement:** Watching the arrows change shows the policy improving over time as the robot learns better actions from its experiences (rewards and penalties).
*   **Trial and Error:** The Log Book clearly shows the robot taking actions, receiving rewards/penalties, and implicitly updating its knowledge (visualized on the grid/worksheet).

## Technical Details

*   Single HTML file with embedded CSS and JavaScript (ES6 Module).
*   Uses the **Three.js** library (via CDN) for 3D rendering (WebGL).
*   Uses **OrbitControls** for camera manipulation.
*   Uses **FontLoader** and **TextGeometry** for 3D text labels.
*   Uses **canvas-confetti** library (via CDN) for goal celebration.
*   Implements the **Q-Learning** algorithm.

## Potential Enhancements

*   Implement epsilon-greedy or other action selection strategies to show the exploration-exploitation trade-off during learning.
*   Visualize the Q-values for *all four actions* within the 3D view (e.g., small bars/glyphs around the pillar) instead of just the max value and best action.
*   Add different agent models.
*   Allow users to draw their own maze layouts.
*   Show the Bellman equation update more explicitly.
