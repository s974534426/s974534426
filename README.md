# SongLei 😉

``` python
from time import sleep
from algorithms import SAC
import school_env_builder


class Agent:
  """Define a agent named to interact with the environment.
  
  We define the agent named Song Lei. He is a very foolish agent that need to 
  interact with the school environment to be learn knowledge using an algorithm 
  called soft actor-critic. After study, he will take a break.
  """
  
  def __init__(self):
    self.agent_name = 'SongLei'
    self.env = school_env_builder.build()
    self.sac = SAC()
    
  def study(self, epochs):
    for _ in range(epochs):
      state = self.env.reset()
      while True:
        action = self.sac.select_action(state)
        next_state, reward, done, _ = self.env.step(action)
        if reward < 0:
          print('You are so stupid')
        self.sac.push(state, action, reward, next_action)
        self.sac.update_parameters()
        if done:
          break
        state = next_state
        
  def take_a_break(self, epochs):
    for _ in range(epochs):
      sleep(1)
        
        
if __name__ == '__main__':
  agent = Agent()
  agent.study(0)
  agent.take_a_break(10000000000)
```
