---
layout: default
title: "Temporal difference learning for ultimate tic-tac-toe"
tags: temporal difference, ultimate tic-tac-toe
---

[repo]: https://github.com/keeeal/temporal-ut3

# Temporal difference learning for ultimate tic-tac-toe
###### 4 June 2019
In this post I will describe the implementation of temporal difference learning that can be found [here][repo]. This amazingly simple algorithm is able to learn entirely through self-play without *any* human knowledge at all except the rules of the game. By way of example, the game we will be playing is ultimate tic-tac-toe, but the same algorithm can be applied to almost any other game with varying degrees of success. This post will assume basic familiarity with machine learning and reinforcement learning concepts, and should be accessible if you understand neural network basics.

## What is ultimate tic-tac-toe?
It's like tic-tac-toe, but each square of the game contains another game of tic-tac-toe in it! Win small games to claim the squares in the big game. Simple, right? But there is a catch: Whichever small square you pick is the next big square your opponent must play in. [Read more...](https://docs.riddles.io/ultimate-tic-tac-toe/rules)

![ultimate tic-tac-toe gif](/img/ut3.gif)

## What is temporal difference learning?
Temporal difference (TD) learning is a reinforcement learning algorithm trained only using self-play. The algorithm learns by bootstrapping from the current estimate of the value function, i.e. the value of a state is updated based on the current estimate of the value of future states. [Read more...](https://en.wikipedia.org/wiki/Temporal_difference_learning)

## How to use

### Training

To begin training:

```bash
python train.py
```

or set the learning hyperparameters using any of the optional arguments:

```bash
python train.py --lr LEARN_RATE --a ALPHA --e EPSILON
```

### Playing

You can play against a trained model using

```bash
python player.py --params path/to/parameters.params
```

If no parameters are provided, the opponent will make moves randomly.

## Experiments

![ultimate tic-tac-toe results](/img/td-ut3-results.png)

Coming soon.

## To-do
 - [Scale the value of terminal results by the game length to prefer shorter games](https://medium.com/oracledevs/lessons-from-alphazero-connect-four-e4a0ae82af68).
 - Implement UT3 neural network in other frameworks, eg: TensorFlow.
 - Make asynchronous, i.e. do self-play, neural net training and model comparison in parallel.

## Requirements
 - [PyTorch](https://pytorch.org/)
 - [Progress](https://pypi.org/project/progress/)

## Thanks
 - [Sam Culley](https://github.com/swculley)
