# SongLei 😉

``` python
from time import sleep
import school_env_builder
from random import randint


class Agent:
  """Define a agent named to interact with the environment.
  
  We define the agent named Song Lei. He is a very foolish agent that need to 
  interact with the school environment to be learn knowledge. After study, 
  he will take a break.
  """
  
  def __init__(self):
    self.agent_name = 'SongLei'
    self.env = school_env_builder.build()
    
  def study(self, epochs):
    for _ in range(epochs):
      state = self.env.reset()
      while True:
        action = randint(0, self.env.action_space.size()-1)
        next_state, reward, done, _ = self.env.step(action)
        if reward < 0:
          print('You are so stupid')
        if done:
          break
        state = next_state
        
  def take_a_break(self, epochs):
    for _ in range(epochs):
      sleep(1)
        
        
if __name__ == '__main__':
  sl = Agent()
  sl.study(0)
  sl.take_a_break(10000000000)
```
