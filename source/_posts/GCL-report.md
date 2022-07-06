---
title: GCL-report
auther: yuran
date: 2022-07-06 16:22:27
categories:
tags:
---
Hello everyone. Today I would like to give a brief introduction to mahjong AI. My name is Yuran QIU.

Here is the content for today.
Let's get started with the first, mahjong as a game.

So, most of us here today might have heard of this game, mahjong is a mind-sport with 3 or 4 players.

In game theory, there are two sorts of games. Complete info games and incomplete info ones.
Complete information games are those in which everything in the game is common knowledge.
While inversely, in an incomplete info ones, players may possess private information.

It is clear that chess, Go, etc., are complete info games, AI already toped these games.
Then incomplete info games like mahjong and starcraft become a challenge.
In this case bayesian equilibrium is useful.

But why do we choose mahjong?
First, it is an incomplete info game.
Second, as we can see in the chart, its state space is quite large.
Third, the reward machanism is fairly complex.

The first AI method I would like to introduce is bakuuchi.

It is developed by UTokyo, and have several achievements listed here.

It used pretty simple algorithms, which is nice. However there are too many details to be refined, and its strategy is too simple.

The second I would like to introduce is Microsoft Suphx.

It is the best mahjong AI for now, developed by MSRA.
It solve the problem by deep reinforcement learning.

Here is the working flow of Suphx.
We can see it have different models for winning, kong, etc.

And the model structure is shown here.

The result is here, we can see that Suphx reached an extremely high stable rank, than any other methods, including top humans.

Let's get to the summary.
Mahjong is an incomplete info game, which is a challenge.
Deep reinforcement learning is applied in suphx and reached better performance than most of human players
We can foresee that mahjong AI can teach players brand new strategy.
Sometimes AI take weird choices, which need further explanation, but time is limited, I will not dive deep into this.

That's all for me today, thanks for listening.

