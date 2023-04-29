# IPC-2023


1. MDPS VS POMDPS
- MDPS: fully observable, assume that the state of the system is fully observable i.e. the agent has complete knowledge of the current state of the system and can use this information to make decisions. e.g. Chess.
- POMDPS: partially observable environment, the agent only has access to partial observations of the state, and must maintain a belief state to reason about the true state of the system. e.g. Super Mario game

2. MDPS might not be valid in real world problems where the past history may be relevant to the future state - POMDPS and RNN, etc are used in that case.  



### Trained for 100k epochs, Optimizer = Rmsprop
FOR LEARNING RATE = 0.01, train_return=-0.000180 test_return=-0.000187

FOR LEARNING RATE = 0.001, train_return=-0.000029 test_return=-0.000036

FOR LEARNING RATE = 0.0001, train_return=0.000003 test_return=-0.000004

FOR LEARNING RATE = 0.0003, train_return=-0.000004 test_return=-0.000011


### Trained for 1000 epochs, Optimizer = RMSprop
FOR LEARNING RATE = 0.01, train_return=-0.000052 test_return=-0.000059

FOR LEARNING RATE = 0.001, train_return=-0.000030 test_return=-0.000037

FOR LEARNING RATE = 0.0001, train_return=0.000003 test_return=-0.000004

FOR LEARNING RATE = 0.0003, train_return=-0.000004 test_return=-0.000011



### Trained for 1000 epochs, Optimizer = adam

FOR LEARNING RATE = 0.01, train_return=-0.000039 test_return=-0.000045

FOR LEARNING RATE = 0.001, train_return=-0.000030 test_return=-0.000037

FOR LEARNING RATE = 0.0001, train_return=0.000002 test_return=-0.000005

FOR LEARNING RATE = 0.0003, train_return=0.000006 test_return=-0.000001


### Trained for 1000 epochs, Optimizer = adagrad

FOR LEARNING RATE = 0.01, train_return=0.000000 test_return=-0.000006

FOR LEARNING RATE = 0.001, train_return=0.000006 test_return=-0.000001

FOR LEARNING RATE = 0.0001, train_return=-0.000359 test_return=-0.000366

FOR LEARNING RATE = 0.0003, train_return=-0.000195 test_return=-0.000201




# ------------------------------------------- SAY HELLO TO JaxDeepReactivePolicy(topology = [256, 128]) ----------------------------------------------

### Trained for 1000 epochs, Optimizer = rmsprop, JaxDeepReactivePolicy

FOR LEARNING RATE = 0.01, train_return=-0.000024 test_return=-0.000031

FOR LEARNING RATE = 0.001, train_return=-0.002088 test_return=-0.001904

FOR LEARNING RATE = 0.0001, train_return=-0.001759 test_return=-0.001705

FOR LEARNING RATE = 0.0003, train_return=-0.003328 test_return=-0.003029

















Note: planner.optimize() returns a generator that yields a dictionary callback at the end of each training epoch. The dictionary contains various performance metrics, such as train_return and test_return, as well as the current model parameters, which are stored under the key params. So, if you want to access the final model parameters after training, you can simply use callback['params'].


policy_weights is a dictionary with keys representing the names of the actions in the policy, and values representing the weight to be assigned to each of those actions.

In the context of reinforcement learning or decision-making problems, the weights in a policy are typically used to balance exploration and exploitation. A higher weight indicates that the corresponding action should be chosen more often, which can lead to more exploration of the state space. Conversely, a lower weight indicates that the corresponding action should be chosen less often, which can lead to more exploitation of the current knowledge about the state space.

In the example you provided, the actions are 'cut-out' and 'put-out', and they are assigned equal weights of 10.0 each. This means that the planner will attempt to balance exploration and exploitation by choosing these two actions roughly equally often.


It seems that the variable "subs" is of type "NoneType" and therefore has no attribute "items". The code is trying to iterate over the items of the "subs" dictionary, but since it is None, it is causing the error.

# initialize the planner
# note that actions should be constrained to [-1, 1] for Racecar
planner = JaxRDDLBackpropPlanner(
    model,
    plan=JaxDeepReactivePolicy(topology = [256, 128]),
    batch_size_train=32,
    rollout_horizon=5,
    optimizer=optax.rmsprop,
    optimizer_kwargs={'learning_rate': 0.001})

step=   0 train_return=-0.122401 test_return=-0.103662
step= 100 train_return=-0.012848 test_return=-0.012794
step= 200 train_return=-0.012316 test_return=-0.011414
step= 300 train_return=-0.001971 test_return=-0.001878
step= 400 train_return=-0.007678 test_return=-0.007355
step= 500 train_return=-0.003496 test_return=-0.003103
step= 600 train_return=-0.002336 test_return=-0.002142
step= 700 train_return=-0.004687 test_return=-0.004558
step= 800 train_return=-0.002448 test_return=-0.002241
step= 900 train_return=-0.003806 test_return=-0.003678
step=1000 train_return=-0.002963 test_return=-0.002827
step=1100 train_return=-0.001406 test_return=-0.001191
step=1200 train_return=-0.002099 test_return=-0.001991
step=1300 train_return=-0.001522 test_return=-0.001346
step=1400 train_return=-0.000721 test_return=-0.000610
step=1500 train_return=-0.000368 test_return=-0.000344
step=1600 train_return=-0.000146 test_return=-0.000153
step=1700 train_return=-0.000311 test_return=-0.000256
step=1800 train_return=-0.000751 test_return=-0.000614
step=1900 train_return=-0.000487 test_return=-0.000419
step=2000 train_return=-0.000468 test_return=-0.000363
step=2100 train_return=-0.000327 test_return=-0.000256
step=2200 train_return=-0.000145 test_return=-0.000117
step=2300 train_return=-0.000087 test_return=-0.000071
step=2400 train_return=-0.000575 test_return=-0.000448
step=2500 train_return=-0.000567 test_return=-0.000463
step=2600 train_return=-0.000288 test_return=-0.000229
step=2700 train_return=-0.000369 test_return=-0.000294
step=2800 train_return=-0.000352 test_return=-0.000288
step=2900 train_return=-0.000201 test_return=-0.000182
step=3000 train_return=-0.000206 test_return=-0.000180
step=3100 train_return=-0.000257 test_return=-0.000240
step=3200 train_return=-0.000496 test_return=-0.000434
step=3300 train_return=-0.000551 test_return=-0.000488
step=3400 train_return=-0.000531 test_return=-0.000463
step=3500 train_return=-0.000533 test_return=-0.000468
step=3600 train_return=-0.000526 test_return=-0.000469
step=3700 train_return=-0.000417 test_return=-0.000372
step=3800 train_return=-0.000333 test_return=-0.000310
step=3900 train_return=-0.000341 test_return=-0.000329
step=4000 train_return=-0.000216 test_return=-0.000222
step=4100 train_return=-0.000020 test_return=-0.000027
step=4200 train_return=-0.000030 test_return=-0.000037
step=4300 train_return=-0.000030 test_return=-0.000037
step=4400 train_return=-0.000030 test_return=-0.000036
step=4500 train_return=-0.000029 test_return=-0.000036
step=4600 train_return=-0.000029 test_return=-0.000036
step=4700 train_return=-0.000029 test_return=-0.000036
step=4800 train_return=-0.000028 test_return=-0.000035
step=4900 train_return=-0.000028 test_return=-0.000035
step=5000 train_return=-0.000028 test_return=-0.000035
step=5100 train_return=-0.000028 test_return=-0.000035
step=5200 train_return=-0.000028 test_return=-0.000034
step=5300 train_return=-0.000027 test_return=-0.000034
step=5400 train_return=-0.000027 test_return=-0.000034
step=5500 train_return=-0.000027 test_return=-0.000034
step=5600 train_return=-0.000027 test_return=-0.000034
step=5700 train_return=-0.000027 test_return=-0.000033
step=5800 train_return=-0.000026 test_return=-0.000033
step=5900 train_return=-0.000026 test_return=-0.000033
step=6000 train_return=-0.000026 test_return=-0.000033
step=6100 train_return=-0.000026 test_return=-0.000033
step=6200 train_return=-0.000026 test_return=-0.000033
step=6300 train_return=-0.000026 test_return=-0.000033
step=6400 train_return=-0.000026 test_return=-0.000032
step=6500 train_return=-0.000025 test_return=-0.000032
step=6600 train_return=-0.000025 test_return=-0.000032
step=6700 train_return=-0.000025 test_return=-0.000032
step=6800 train_return=-0.000025 test_return=-0.000032
step=6900 train_return=-0.000025 test_return=-0.000032
step=7000 train_return=-0.000025 test_return=-0.000032
step=7100 train_return=-0.000025 test_return=-0.000032
step=7200 train_return=-0.000025 test_return=-0.000032
step=7300 train_return=-0.000025 test_return=-0.000031
step=7400 train_return=-0.000025 test_return=-0.000031
step=7500 train_return=-0.000024 test_return=-0.000031
step=7600 train_return=-0.000024 test_return=-0.000031
step=7700 train_return=-0.000024 test_return=-0.000031
step=7800 train_return=-0.000024 test_return=-0.000031
step=7900 train_return=-0.000024 test_return=-0.000031
step=8000 train_return=-0.000024 test_return=-0.000031
step=8100 train_return=-0.000024 test_return=-0.000031
step=8200 train_return=-0.000024 test_return=-0.000031
step=8300 train_return=-0.000024 test_return=-0.000031
step=8400 train_return=-0.000024 test_return=-0.000031
step=8500 train_return=-0.000024 test_return=-0.000031
step=8600 train_return=-0.000024 test_return=-0.000031
step=8700 train_return=-0.000024 test_return=-0.000031
step=8800 train_return=-0.000024 test_return=-0.000030
step=8900 train_return=-0.000024 test_return=-0.000030
step=9000 train_return=-0.000024 test_return=-0.000030
step=9100 train_return=-0.000023 test_return=-0.000030
step=9200 train_return=-0.000023 test_return=-0.000030
step=9300 train_return=-0.000023 test_return=-0.000030
step=9400 train_return=-0.000023 test_return=-0.000030
step=9500 train_return=-0.000023 test_return=-0.000030
step=9600 train_return=-0.000023 test_return=-0.000030
step=9700 train_return=-0.000023 test_return=-0.000030
step=9800 train_return=-0.000023 test_return=-0.000030
step=9900 train_return=-0.000023 test_return=-0.000030
step=9999 train_return=-0.000034 test_return=-0.000041



The rollout_horizon is a hyperparameter that controls the length of the plan generated by the planner. It determines how many steps into the future the planner will try to generate a plan for. A longer rollout_horizon can allow the planner to generate more detailed and potentially more effective plans, but can also increase the computational cost and the risk of the plan becoming inaccurate due to unforeseen events.

A good approach to selecting the rollout_horizon hyperparameter is to start with a small value and gradually increase it while monitoring the performance of the planner. This will allow you to find a balance between accuracy and computational cost that works best for your specific task. It's also worth noting that the optimal rollout_horizon may vary depending on the complexity of the task and the performance of the model being used by the planner.
