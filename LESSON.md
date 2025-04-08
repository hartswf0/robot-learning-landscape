# Lesson Plan: Robot's Learning Landscape!

**Grade Level:** 4th - 7th Grade (Adaptable)

**Subject:** Introduction to Computer Science, Artificial Intelligence Concepts, Problem Solving

**Time Allotment:** 45-60 minutes

**Learning Objectives:**

Students will be able to:

1.  **Identify** the core components of a simple reinforcement learning problem: State, Action, Reward/Penalty.
2.  **Explain** that the robot learns through trial-and-error by exploring its environment.
3.  **Describe** how positive rewards (like finding treasure) encourage certain actions/paths.
4.  **Describe** how negative rewards/penalties (like hitting traps/walls) discourage certain actions/paths.
5.  **Define** (simply) what a "Policy" or "Plan" is for the robot (its learned best guesses).
6.  **Observe** how the robot's learned "Value" (pillar height/color) and "Policy" (arrow direction) change over time with more exploration.
7.  **Differentiate** between the robot exploring randomly and following its learned plan.

**Materials:**

*   Computer with a modern web browser (Chrome, Firefox, Edge recommended) for each student or pair of students.
*   The `robot_landscape.html` file (or access via a web link if hosted).
*   Projector or large screen for demonstration (optional, but recommended).
*   Whiteboard or chart paper (optional).
*   Simple handout with key vocabulary (optional).

**Vocabulary (Simplified):**

*   **Robot:** The agent trying to learn.
*   **Landscape/World:** The grid the robot moves in.
*   **Spot (State):** Where the robot is right now `(row, column)`.
*   **Move (Action):** What the robot *does* (Up, Down, Left, Right).
*   **Points (Reward/Penalty):** Score the robot gets for landing on a spot (+ for Goal, - for Trap/Mud/Wall).
*   **Learning:** How the robot gets smarter by remembering the points it gets for its moves.
*   **Value (Score):** How "good" the robot thinks a spot is (shown by pillar height/color). Higher is better!
*   **Plan / Policy:** The robot's "map" of the best move to make from each spot (shown by the arrows).
*   **Explore:** Trying random moves to learn about the world.
*   **Test Plan:** Following the learned plan (arrows) without exploring randomly.

**Procedure:**

**(5-10 min) Introduction: Learning Like a Robot**

1.  **Hook:** Ask students: "How do you learn to play a new game? Do you try things out? What happens if you make a mistake? What happens if you succeed?" Relate this to how pets learn tricks (treats = reward).
2.  **Introduce the Robot:** "Today we have a robot trying to learn its way through a landscape to find treasure! It doesn't know the map at first, just like you learning a new game. It has to learn by trying things."
3.  **Goal:** Explain the robot's goal (find the Gold `Goal` pillar) and things to avoid (Red `Trap` pillars, Brown `Mud` pillars, Grey `Wall` pillars).

**(15-20 min) Exploring and Learning**

1.  **Load Simulation:** Have students open the `robot_landscape.html` file. Briefly demonstrate the 3D controls (orbit, zoom, pan).
2.  **Identify Components:** Point out the **Robot**, the **Landscape** (pillars), the **Worksheet**, and the **Log Book**.
3.  **Manual Exploration (Step):**
    *   Have students click the **"Step (Explore)"** button a few times.
    *   Ask: "What did the robot do?" (Look at "Last Move" status). "Where is it now?" (Look at "Robot Spot"). "Did it get points?" (Look at "Points").
    *   Direct attention to the **Log Book**. Read a few entries together. Emphasize the `[Exp]` prefix, `(r,c)` state, action taken, result, and points.
4.  **Auto Exploration:**
    *   Have students click **"Start Auto (Explore)"**. Let it run for 10-20 steps (adjust speed if needed).
    *   Ask: "Is the robot moving smartly? Does it seem to have a plan?" (Likely no, it's random).
5.  **Introduce Learning Visualization:**
    *   Click **"Show/Hide Learn"** if it's off. Explain:
        *   "The **Worksheet** shows the robot's 'Smartness Score' for each move from each spot. Watch the numbers change!"
        *   "In the 3D world, watch the **pillars**! They change height and color. **Taller/Greener** means the robot thinks that spot is good. **Shorter/Redder** means it thinks it's bad."
        *   "When a score updates on the worksheet (flashes yellow), the matching pillar in the 3D world flashes white! This shows *where* the learning happened."
        *   "See the **arrow** on top of some pillars? That's the robot's **Best Guess** move (its Plan!) from that spot right now."
6.  **Accelerated Learning:**
    *   Click **"Stop Auto"**.
    *   Set the **Episodes** input to 50 or 100. Click **"Run Explore"**.
    *   While it runs (quickly), ask students to watch the overall landscape change. "Are areas near the Goal getting taller/greener? Are areas near the Traps getting shorter/redder? Are the arrows starting to point somewhere useful?"

**(10-15 min) Policy and Testing**

1.  **Explain Policy:** "After exploring, the robot has learned a **Plan** (or Policy). The arrows on the pillars show this plan – the best move it *thinks* it should make from each spot."
2.  **Test the Plan:** Click **"Test Best Plan"**. The mode will change, and the robot will now follow the arrows.
3.  **Observe:** Ask: "Is the robot following the arrows? Is it finding the Goal faster now? Does it avoid the Traps? Did it get stuck?"
4.  **Discuss:** Why is testing the plan useful? (To see if the learning was good). Why did the robot explore randomly first? (To find the rewards and penalties). Briefly mention this is the "Explore vs. Use What You Know" idea.

**(5-10 min) Wrap-up & Discussion**

1.  **Randomize:** Click **"Randomize World"** and **"Reset All"**. Show how the robot has to learn again from scratch in a new environment.
2.  **Review:** Briefly review the key vocabulary (State, Action, Reward, Policy, Value).
3.  **Connect:** Ask students where else they see learning like this (video game characters learning paths, training a dog, figuring out the best way to school).
4.  **Q&A:** Answer student questions.

**Assessment (Informal):**

*   Observe student participation and discussion.
*   Ask students to point out the State, a possible Action, a Reward/Penalty spot on the screen.
*   Ask students to predict where the arrow might point after the robot experiences a big reward or penalty nearby.
*   (Optional Handout) Have students draw a simple 3x3 grid, label a Start/Goal/Trap, and draw arrows showing a possible learned path.

**Differentiation/Extensions:**

*   **Younger/Simpler:** Focus only on manual steps, the log book, and the basic idea of rewards/penalties changing robot behavior. Ignore the worksheet and maybe the height changes, focusing just on the policy arrows appearing.
*   **Older/Advanced:** Discuss the learning rate and discount factor (conceptually – how fast it learns, how much future matters). Discuss why random exploration is sometimes needed even after learning a plan (exploration-exploitation trade-off). Have students try different numbers of exploration episodes before testing the policy. Discuss the limitations of Q-learning in this simple setup.
