# 4castr

This is my fork of the 4castr project I have been working on as part of UCLA's Datares Research team.

Currently, 4castr uses [Stable Baselines](https://stable-baselines.readthedocs.io/en/master/) and [Optuna](https://optuna.org/) to train [Proximal Policy Optimization](https://openai.com/blog/openai-baselines-ppo/) (PPO) agents. The rather complicated algorithm has several tools that can help the agent learn.

For instance, it can generate TensorBoard plots of all the agent's training stats.

Additionally, by default, the agent takes OHLCV (Open, High, Low, Close, and Volume. They're metric that have to do with how a stock did that day) values of AAPL (Apple's ticker) and attempts to maximize a reward, which corresponds to the net profit throughout the trading window (in days).

As part of the Trader team, we've been investigating mainly two issues we've encountered so far:
1. Reducing the number of features in order to reduce state complexity (currently the model takes something like around 10M steps which could be cut down quite a lot, we've heard stories of people getting good predictions with only a couple thousand)
2. We're also researching new features to engineer into our data. Some of these come from the [Technical Analysis Library in Python](https://github.com/bukosabino/ta), but we've been testing our own as well


## Set up and installation

To run, create a conda environment

```bash
conda create -n datares_4castr python==3.7
```

Then clone the repo

```bash
git clone https://github.com/datares/4castr.git
```

Finally, update your conda env with the specs that are necessary to run the project

```bash
cd 4castr
conda env update --name datares_4castr --file environment_root.yml
```

## Running the project

To run the project with optuna, run:

```bash
conda activate datares_4castr
python run.py -m optimize -n your_model_name
```
