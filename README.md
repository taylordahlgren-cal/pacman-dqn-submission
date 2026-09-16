# pacman-dqn-submission

- **My choices:** exploration = 0.20, episodes = 100, learning rate = 0.0001.
- **My prediction:** I expected these settings to show marginal improvement to my score because I believed the exploration rate to be reasonable but not too high, allowing some ability for the agent to learn without taking too much random risk. I chose 100 episodes since it didn't seem like it would take too long to run, but would allow for more attempts for my agent to learn. I went with the recommended learning rate, primarily because I didn't really understand what it was intended to do and what the potential impact could be.
- **What happened:** mean score before = 492; after = 800. In the gameplay, I noticed scores improved initially, but then it actually looks like they were all over the place. The score wasn't actually grandually improving as if the agent was learning with certainty. 
- **One limitation:** It seems the major limitation is not having enough episodes to really support learning to result in better play. I ran this game a few times and scores were all over so I think this one is higher in part because of random luck.
- **My next experiment:** change only episodes to 250 and keep the other two settings fixed.

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
