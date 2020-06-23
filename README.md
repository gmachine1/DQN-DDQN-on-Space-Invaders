# DQN-DDQN-on-Space-Invaders
Implementation of Double Deep Q Networks and Dueling Q Networks using Keras on Space Invaders using OpenAI Gym. Code can be easily generalized to other Atari games.

## Prerequisites
You can install all the prerequisites for code use using 

```text
pip install -r requirements.txt
```

In China on Ubuntu, I used conda and some China mirrors for faster downloads. For `~/.condarc`,

```
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
  - conda-forge
```

Then

```
conda install tensorflow
conda install keras
conda install numpy
conda install opencv
conda install -c hcc gym
conda install -c likan999 atari_py
conda install -c jiayi_anaconda gym-atari
sudo apt-get install -y python-pygame
git clone https://github.com/lusob/gym-tetris.git
cd gym-tetris/
pip install -e .
```

### On windows

1. Download and install the appropriate `vc_redist.*.exe` file, which can be found [here](https://support.microsoft.com/zh-cn/help/2977003/the-latest-supported-visual-c-downloads).
2. Uninstall gym and atari-py (If already installed):
```
pip uninstall atari-py
pip uninstall gym[atari]
```
3. Download VS build tools [here](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)
4. Run the VS build setup and select "C++ build tools" and install it.
5. Restart PC.
6. Install cmake, atari-py and gym
```
pip install cmake
pip install --no-index -f https://github.
com/Kojoley/atari-py/releases atari_py
pip install gym[atari]
```

Now run the following code:
```python
import atari_py
print(atari_py.list_games())
```

and if everything worked then it should return a list of all games as shown below
```
['adventure', 'air_raid', 'alien', 'amidar', 'assault', 'asterix', 'asteroids', 'atlantis',
'bank_heist', 'battle_zone', 'beam_rider', 'berzerk', 'bowling', 'boxing', 'breakout', 'carnival',
'centipede', 'chopper_command', 'crazy_climber', 'defender', 'demon_attack', 'double_dunk',
'elevator_action', 'enduro', 'fishing_derby', 'freeway', 'frostbite', 'gopher', 'gravitar', 'hero',
'ice_hockey', 'jamesbond', 'journey_escape', 'kaboom', 'kangaroo', 'krull', 'kung_fu_master',
'montezuma_revenge', 'ms_pacman', 'name_this_game', 'phoenix', 'pitfall', 'pong', 'pooyan',
'private_eye', 'qbert', 'riverraid', 'road_runner', 'robotank', 'seaquest', 'skiing', 'solaris',
'space_invaders', 'star_gunner', 'tennis', 'time_pilot', 'tutankham', 'up_n_down', 'venture',
'video_pinball', 'wizard_of_wor', 'yars_revenge', 'zaxxon']
```
## Instructions on Use
Details about the code are covered in the blog [here](https://yilundu.github.io/2016/12/24/Deep-Q-Learning-on-Space-Invaders.html)

To run the code use
```python
  python main.py
```
with arguments where arguments are given by

```text
usage: main.py [-h] [-g GAME] -n NETWORK -m MODE [-l LOAD] [-s SAVE] [-x] [-v]

Train and test different networks on Space Invaders or Tetris

optional arguments:
  -h, --help            show this help message and exit
  -g GAME, --game GAME  Specify the game to train on. Defaults to space invaders
  -n NETWORK, --network NETWORK
                        Please specify the network you wish to use, either DQN or DDQN
  -m MODE, --mode MODE  Please specify the mode you wish to run, either train or test
  -l LOAD, --load LOAD  Please specify the file you wish to load weights from(for example saved.h5)
  -s SAVE, --save SAVE  Specify folder to render simulation of network in
  -x, --statistics      Specify to calculate statistics of network(such as average score on game)
  -v, --view            Display the network playing a game of space-invaders. Is overriden by the -s command
  ```
  
  For example, to test the pre-trained Double Deep Q Network architecture and view the network playing space invaders use
  
  ```text
    python main.py -n DDQN -m test -l saved.h5 -v
  ```
  
 or to train the Dueling Q Network architecture and then save the resulting video of the network playing in the test/ directory 
 use 
 
   ```text
    python main.py -n DQN -m train -s test
  ```
 

 *Note that as the model is trained, every 10000 images, the program saves the network weights in either saved.h5 of duel_saved.h5 for DDQN and DQN respectively*
