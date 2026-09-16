# pacman-dqn-submission

- **My choices:** exploration = 0.20, episodes = 100, learning rate = 0.0001.
- **My prediction:** I expected these settings to show marginal improvement to my score because I believed the exploration rate to be reasonable but not too high, allowing some ability for the agent to learn without taking too much random risk. I chose 100 episodes since it didn't seem like it would take too long to run, but would allow for more attempts for my agent to learn. I used the notebook's suggested reference value of 0.0001 because it's a standard, well-tested starting point for this type of network (and in truth, this is an input I didn't fully understand so I thought... best to go with what's suggested). Claude told me it was large enough to learn within a short run, small enough to avoid destabilizing training.
- **What happened:** mean score before = 492; after = 800 — a net improvement of +308. But looking at the five individual games rather than just the mean, the picture isn't so clear... four of five seeds improved substantially (for example - seed 3 went from 320 to 1000, seed 4 from 800 to 1520), while one seed (490 to 290) actually got worse after training. This suggests the agent learned a policy that performs well in some situations but not yet consistently across all of them, or even most of them.

-   Game     Before      After
     1        350        570
     2        500        620
     3        320       1000
     4        800       1520
     5        490        290
  Mean      492.0      800.0
Change in mean score: +308.0

- **One limitation:** My main limitation was not training long enough. The agent didn't get enough practice to settle into one reliable way of playing. I saw this in two ways: the five test games in a single run had very different scores from each other (some doubled, one actually got worse), and when I ran the whole notebook again with the exact same settings, I got noticeably different results each time.
- **My next experiment:** change only episodes to 500 and keep the other two settings fixed.

- ## Actual training run
- Episodes completed: 100 of 100 requested (status: completed)
- Learning updates: 14261
- Total decisions: 58043
- Elapsed time: 228.66553284199927
- Hardware: cuda

- 
  "status": "completed",
  "completed_episodes": 100,
  "total_decisions": 58043,
  "learning_updates": 14261,
  "elapsed_seconds_including_periodic_demos": 228.66553284199927

Results/comparison.json

The agent observes four screens, chooses a joystick action, and receives game rewards.
Lower training loss does not necessarily mean a higher game score. Report lack of progress if that is what happened.

### implementation notes and sources

This is a small, readable DQN experiment, not a reproduction of a large Atari benchmark.
Replay is deliberately small for laptops. Epsilon stays constant after warm-up. Checkpoints support playback;
rerunning starts a new experiment, rather than resuming the optimizer, replay memory, or an interrupted game.
GPU results can vary even with fixed seeds.

- [ALE installation and Gymnasium registration](https://ale.farama.org/getting-started/)
- [Gymnasium Atari preprocessing](https://gymnasium.farama.org/api/wrappers/misc_wrappers/#gymnasium.wrappers.AtariPreprocessing)
- [Gymnasium frame stacking](https://gymnasium.farama.org/api/wrappers/observation_wrappers/#gymnasium.wrappers.FrameStackObservation)
- [DQN paper: Human-level control through deep reinforcement learning](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf)
