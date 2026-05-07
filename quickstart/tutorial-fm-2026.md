---
layout: default
title: DRV Tutorial
---

## Distributed Runtime Verification in Proximity-based Networks: A Tutorial on the Aggregate Programming Approach

WORK IN PROGRESS

### Installation

#### Obtaining the source code

To retrieve the source code clone the repository with the following command:

```bash
git clone https://github.com/fcpp-experiments/past-ctl-monitoring.git
```

#### Build the demos

The repository contains the source code of simulations running past-CTL monitors to verify different properties.

Launching the bash script without additional input showcase the list of available
simulations:

```bash
./make.sh
```


To build and run the drone recognition example execute the following command:

```bash
./make.sh drone_recognition
```

### Running a simulation

When launching a simulation it is initially paused by pressing the **P key** you can pause/unpause the execution.

You can toggle the grid visualization with the **G key** and toggle the link
visualization with the **L key**.

You can move the view around using the **W,A,S,D keys** and increase or decrease
the zoom factor using the **Q,E keys**.

Simulation speed can be increased or decreased using the **I,O keys** and by pressing the **H key** or any unmapped key the help menu is presented pausing the
simulation. To exit from the help menu press the **P key** again.

By **clicking** on a node in the simulation is possible to inspect the current
state of the storage memory of a node.

#### Checking monitor results

After a simulation ends inside the **plot** folder the corresponding file are
created. These file show the evolution of the monitors values over time
accumulated using the specified function (e.g. counting, average value, min value,
max value).

## Challenge

In this section we introduce the simulations used for the challenge, how you
can modify different parameters to change the setting and behaviour of the
simulation and the past-CTL properties that we want to verify as part of the
challenge.

!TODO Add loop video

### Scenario

The simulation emulates a smart-grid connecting a **energy source** (star-shaped
node) to a **user node** (triangular-shaped node).

The intermediate node can be in one of the following state:

- **BLUE**  online and connected to both the source and the user;
- **GREEN** online but not connected to both nodes;
- **BLACK** offline, blocking communications.

There are 100 nodes placed in a grid layout, and by default the node with UID 0 is set as **source** and the node with UID 99 is set as **user**.

Every 10 seconds intermediate nodes:

- if online have a 10% chance of going offline.
- if offline have a 40% chance of going online.

#### Customize the scenario

By modifying the constant values in **lib/smart\_grid.hpp** you can modify the
evolution of the simulation.

The following table explain the different parameters:

|Parameter name| Description | Default Value|
|-|--|-|
|SOURCE|UID of the source node| 0|
|USER| UID of the user node | 99|
|FAIL\_CHANCE| Probability of failure for the intermediate nodes |10|
|REPAIR\_CHANCE| Probability of repairment for the intermediate nodes |40|
|UPDATE\_TIME| How often nodes can change state, since nodes have a 10Hz frequency 100 corresponds to 10s | 100|
|COMM\_RANGE| Maximum distance for communication between nodes |75|
