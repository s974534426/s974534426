# SongLei 😉

``` python
from time import sleep
import school_env_builder
from random import randint


class FoolishStudent:
  
  def __init__(self, agent_name):
    self.agent_name = agent_name
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
  sl = FoolishStudent('songlei')
  for day in range(365):
    sl.study(0)
    sl.take_a_break(10000000000)
```
