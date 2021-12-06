
<style>
    body {
    counter-reset: section;
    }

    h1 {
    counter-reset: subsection;
    }
    h2 {
    counter-reset: subsection2;
    }
    h3 {
    counter-reset: subsection3;
    }
    h4 {
    counter-reset: subsection4;
    }
    h1::before {
    counter-increment: section;
    content:  " ";
    }

    h2::before {
    counter-increment: subsection;
    content: counter(subsection) " ";
    }
    h3::before {
    counter-increment: subsection2;
    content: counter(subsection) "." counter(subsection2) ;
    }
    h4::before {
    counter-increment: subsection3;
    content:  counter(subsection) "." counter(subsection2) "." counter(subsection3) ;
    }
    h5::before {
    counter-increment: subsection4;
    content:  counter(subsection) "." counter(subsection2) "." counter(subsection3)"." counter(subsection4) ;
    }
</style>
# Multi-agent reinforcement learning algorithm and environment
**[en/[cn](README_cn.md)]**


Pytorch implements multi-agent reinforcement learning algorithms including IQL, QMIX, VDN, COMA, QTRAN (QTRAN-Base and QTRAN-Alt), MAVEN, CommNet, DYMA-Cl, and G2ANet, which are among the most advanced MARL algorithms. SMAC is a decentralized micromanagement scenario for StarCraft II.

Project Address:
https://github.com/starry-sky6688/StarCraft

## Run:

` python main.py --map=3m --alg=qmix`

Run directly, and then the algorithm will start training on the map.

MRL environment configuration
Starcraft II environment: https://github.com/oxwhirl/smac

### Install StarCraft II
SMAC based on the complete game of StarCraft II (version >= 3.16.1). To install the game, follow the command below.

1. Linux

Please use [blizzard repository] (https://github.com/Blizzard/s2client-proto#downloads) download the Linux version of starcraft II. By default, the game should be in a directory. This can be changed by setting environment variables. ~/StarCraftII/SC2PATH

2. MacOS/Windows

From Battle.net, please install [starcraft II] (https://starcraft2.com/zh-tw/). The free starter version is also available. If you use the default installation location, PySC2 will find the latest binaries. Otherwise, like the Linux version, you need to set the environment variables with the correct location of the game. `SC2PATH`

### SMAC map
SMAC consists of a number of battle scenarios with pre-configured maps. Before SMAC can be used, these maps need to be downloaded into the StarCraft II directory. Maps

Download the [SMAC map] (https://github.com/oxwhirl/smac/releases/download/v0.1-beta1/SMAC_Maps.zip) and unzip it to your directory. If you have SMAC installed with Git, simply copy the directory from the directory to the directory.

Create a new folder Maps under the root directory

Save the file to the StarCraft Maps folder.
## run
`python main.py --map=3m --alg=qmix`

Environment configuration, feel a bit of a problem, actually change the python folder in the address, do not need to configure any environment variables.
Error file, click to find C: change to F: can be.
### result

<div align=center><img width = '600' height ='300' src ="https://www.mmrsl.cn/download/img/xmu/1.png"/></div>
<div align=center><video src="https://www.mmrsl.cn/download/video/1.mp4"   controls="controls"></video></div>


<div align=center>
Win 8 times on average, run 3m independently --difficulty=7(VeryHard)</div>

<div align=center><img width = '600' height ='300' src ="https://www.mmrsl.cn/download/img/xmu/overview_3m.png"/></div>



## MADDPG
Git are not running, found on the test for a long time, on the basis of the https://github.com/starry-sky6688/MADDPG changed, run successfully.

- the corresponding papers: [Multi - Agent Actor - Critic for Mixed Cooperative - Competitive Environments] (https://arxiv.org/abs/1706.02275)
- the corresponding environment: (MPE) (https://github.com/openai/multiagent-particle-envs)

### multi-agent environment
[MPE](https://github.com/openai/multiagent-particle-envs)
Installation Method 1:

`cd into the root directory and type pip install -e .`

2 installation method 2:
https://www.pettingzoo.ml/mpe

`pip install pettingzoo[mpe]`

### Requirements
Python = 3.6.5
Multi-Agent Particle Environment(MPE)
The torch = 1.1.0

### result

`python main.py --scenario-name=simple_tag --evaluate-episodes=10`

<div align=center><img width = '600' height ='300' src ="https://www.mmrsl.cn/download/img/xmu/2.png"/></div>


Py --scenario-name=simple_tag --evaluate-episodes=10

Modify the 'simple_tag' replacement environment.

### result

In this task, two blue agents gain a reward by minimizing their closest approach to a green landmark (only one needs to get close enough for the best reward), while maximizing the distance between a red opponent and the green landmark. Red opponents are rewarded by minimizing their distance from green landmarks; However, in any given trial, it doesn't know which landmark is green, so it must follow the blue proxy. Therefore, the blue agent should learn to trick the red agent by overwriting two landmarks.
<div align=center><img src="https://www.mmrsl.cn/download/img/xmu/1.gif?raw=true" width="20%"> <img  src="https://www.mmrsl.cn/download/img/xmu/2.gif?raw=true" width="20%"> <img  src="https://www.mmrsl.cn/download/img/xmu/3.gif?raw=true" width="20%"></div>



<div align=center><video src="https://www.mmrsl.cn/download/img/xmu/1.mp4"   controls="controls"></video></div>