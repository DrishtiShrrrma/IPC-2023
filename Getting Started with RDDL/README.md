1. domain.rddl --> more like a template/blueprint of the task/problem which we are trying to model/optimize ---> doesn't include specifics --> just defines the underlying structure   --- The file specifies the properties of the objects in the domain and the relationships between them, without referring to specific instances of those objects.
2. instance.rddl ---> includes specifics
- could include intial state, but not necessarily
- objectives
- additional constraints

3. What's the need of defining multiple instances of a planning problem?
- Sensitivity Analysis: to test how sensitive the solution is to changes in the initial state or other problem parameters, we could define multiple instances of the problem with different initial states or parameter values, and then run the planner on each instance to compare the results.
- Multi-objective optimization: In some planning problems, there may be multiple objectives that we want to optimize simultaneously. We could define multiple instances of the problem, each with different weightings or priorities assigned to the objectives, and then compare the solutions to see which objective weighting yields the best overall performance.
- Scenario planning: In some domains, the environment may be subject to different scenarios or conditions that affect the behavior of the system. We could define multiple instances of the problem, each representing a different scenario or condition, and then run the planner on each instance to generate plans that are tailored to each scenario.
- Online learning: In some applications of planning, we may be learning the properties of the environment as we go, and need to update the planning problem as we learn more. We could define multiple instances of the problem, each representing a different stage of the learning process, and then use the planner to generate plans that are adapted to the current stage of learning.

4.  We can define multiple instances of the planning problem - we can choose to use only a subset of the instances, or you may use all of them - depending on the application and the goals of the planning process

5. For modelling dynamic env using RDDL - multiple instances that represent different scenerios/conditions but you may only use the instances that are relevant to the current situation.
- For example, if you are planning for an autonomous vehicle that operates in different weather conditions, you might define instances for clear weather, rain, snow, and fog, but only use the instance that corresponds to the current weather.

6. It is desirable for a planning system to perform well across all instances of a planning problem. However, in many practical applications of planning, it may not be feasible or necessary to optimize for all instances.

Reason:
- Computational constraints: In some cases, the computational resources required to optimize for all instances may be prohibitive. For example, if we have a large number of instances or if each instance requires significant computation, it may not be practical to optimize for all of them.

- Domain-specific considerations: In some domains, there may be certain instances that are more important or representative than others. For example, in a planning problem for an autonomous vehicle, the instance that corresponds to rush hour traffic may be more important than the instance that corresponds to light traffic.

- Goal-specific considerations: In some cases, we may have specific goals or objectives that are only relevant to certain instances. For example, if we are optimizing a planning system for a disaster response scenario, we may want to prioritize instances that correspond to high-risk areas or emergency situations.
