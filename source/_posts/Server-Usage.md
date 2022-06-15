---
title: Server-Usage
auther: yuran
date: 2022-06-15 10:02:05
categories:
tags:
---

This is a memo for lab GPU cluster usage  

## Self-intro
Yamagishi Junichi
Xin Wang
Jian Wang

## Guidance
- Two link in the description of the slack channel
    - One is for IT issues
    - The other is a manual
- Network Organization
    - Four Layers
        - Internet (home, eduroam)
        - NII Network
            - nii-auth wifi
            - devices like printer
        - Lab Network
            - devices like Apple TV etc.
            - LAN cable
            - Two location, Jinbocho and Kashiwa
            - 136.187.?.?
        - Cluster Network
            - Head Node 136.187.108.7
                - All work shall be submitted to this
- Hardware
    - Head node 
        - Ubuntu 18.04
        - no heavy jobs
        - ` $ show_res.sh `
    - Network attached storage (NAS)
        - for file management
        - ` $ df -h | grep nas `
        - /local/ works as cache
        - /home/smg
    - Software
        - Bright cluster manager
        - Slurm

## SSH key generate
    generate ssh key and send to Mr.yousuke kosuda

## Slurm commands
- login_private.sh
- sbatch -p qgpu

## Decision Tree
- Do not need GPUs
    - Use CPU Nodes!
- Need GPUs
    - Stable Code
        - Submit with sbatch through the head node
    - Work in progress
        - Test before submit
            - Shortly use public node
        - Developing
            - Use a private node

## Login Method
### sbatch
### public
### private
