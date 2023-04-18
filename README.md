# IPC-2023


1. MDPS VS POMDPS
- MDPS: fully observable, assume that the state of the system is fully observable i.e. the agent has complete knowledge of the current state of the system and can use this information to make decisions. e.g. Chess.
- POMDPS: partially observable environment, the agent only has access to partial observations of the state, and must maintain a belief state to reason about the true state of the system. e.g. Super Mario game

2. MDPS might not be valid in real world problems where the past history may be relevant to the future state - POMDPS and RNN, etc are used in that case.  
