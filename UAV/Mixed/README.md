
### How to improve the returns?

1. Tweaking planning params: batch_size, rollout_horizon, optimizer setting, different optimizers --> RMSProp, AdaGrad, Adam, SGD, etc
2. Modifying Plan: JaxStraightLinePlan, JaxDeepReactivePolicy, etc.
3. Increasing/Decreasing Training Epochs
4. Adjusting the Learning Rate
5. Adjusting Reward: Ensure that the rewards provide meaningful feedback to the planner and are aligned with the objectives of UAV mixed domain problem - to guide the planner towards desired behaviors.
6. Model Analysis: Analyze the planner's behavior by observing its planning decisions, trajectories, or other intermediate outputs- can provide insights into potential issues/limitations of the planner and guide in making improvements.  



### Reward Adjustment:
1. UAV successfully achieves its goal - Incentivize/ Positive Reward
2. Gradually increase the reward as the UAV gets closer to the goal. This encourages the planner to make progress towards the goal
3. Encourage the UAV to complete tasks quickly by incorporating a time-based reward component. Penalize longer durations or reward shorter durations, depending on the specific requirements of problem.
4. Negative rewards or penalties for actions that violate safety constraints or result in undesirable outcomes. For example, penalize collisions, violations of altitude limits, or excessive energy consumption.
5. If UAV has limited resources (e.g., battery life), consider incorporating a reward component that encourages efficient resource usage. Penalize actions that consume excessive resources or reward actions that conserve resources.
6. Reward smooth and stable flight behaviors by penalizing abrupt changes in velocity, acceleration, or attitude. This can help promote safe and controlled UAV movements.
7. Tailor the reward function to the specific objectives of UAV mixed domain problem. Identify key performance indicators or metrics that reflect the desired behavior and design the reward function to optimize those objectives.
8. Incorporate intermediate sub-goals or shaping rewards to guide the planner towards desired behaviors. Break down complex tasks into smaller sub-goals and provide rewards for achieving each sub-goal. This can help the planner learn step-by-step strategies and improve overall performance.
9. Encourage exploration by providing additional rewards for discovering new areas, collecting information, or visiting unexplored regions. This can prevent the planner from getting stuck in local optima and promote exploration of the environment.

reward = -sum_{?a : aircraft} [CONTROLLABLE(?a) * sqrt[pow[(pos-x(?a) - GOAL-X(?a)),2] +
                                   pow[(pos-y(?a) - GOAL-Y(?a)),2] +
                                   pow[(pos-z(?a) - GOAL-Z(?a)),2]] ];
