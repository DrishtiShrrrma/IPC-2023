# IPC-2023


1. MDPS VS POMDPS
- MDPS: fully observable, assume that the state of the system is fully observable i.e. the agent has complete knowledge of the current state of the system and can use this information to make decisions. e.g. Chess.
- POMDPS: partially observable environment, the agent only has access to partial observations of the state, and must maintain a belief state to reason about the true state of the system. e.g. Super Mario game

2. MDPS might not be valid in real world problems where the past history may be relevant to the future state - POMDPS and RNN, etc are used in that case.  



### Trained for 100k epochs
FOR LEARNING RATE = 0.01, train_return=-0.000180 test_return=-0.000187

FOR LEARNING RATE = 0.001, train_return=-0.000029 test_return=-0.000036

FOR LEARNING RATE = 0.0001, train_return=0.000003 test_return=-0.000004

FOR LEARNING RATE = 0.0003, train_return=-0.000004 test_return=-0.000011


### Trained for 1000 epochs
FOR LEARNING RATE = 0.01, train_return=-0.000052 test_return=-0.000059

FOR LEARNING RATE = 0.001, train_return=-0.000030 test_return=-0.000037

FOR LEARNING RATE = 0.0001, train_return=0.000003 test_return=-0.000004

FOR LEARNING RATE = 0.0003, train_return=-0.000004 test_return=-0.000011

