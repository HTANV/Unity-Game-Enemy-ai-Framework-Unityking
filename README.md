# Unity-Game-Enemy-ai-Framework---Unityking
Unity Game Enemy AI Framework
(FSM • Behavior Trees • Perception System)
Author: Unity King
Website: https://unityking.com
 
1. Introduction
The Unity Game Enemy AI Framework by Unity King is a modular, production-ready foundation for building intelligent enemy behavior in Unity games. The framework is designed to be flexible, extensible, and easy to understand, supporting both small prototypes and large-scale productions.
This framework combines three powerful AI concepts:
• Finite State Machines (FSM)
• Behavior Trees (BT)
• Perception Systems (Vision-based sensing)

Together, these systems allow developers to create believable, scalable, and maintainable enemy AI.
 
2. Core AI Concepts
2.1 Finite State Machine (FSM)
FSM is used to manage high-level enemy states such as Idle, Patrol, Chase, and Attack. Each state is isolated and handles its own logic, making behavior predictable and debuggable.
2.2 Behavior Trees (BT)
Behavior Trees are used for decision-making inside states. They provide flexible control over complex logic using nodes such as Selectors, Sequences, and Action Nodes.
2.3 Blackboard
The Blackboard is a shared memory structure that stores runtime data such as the current target, distance to the player, vision status, and attack range.
 
3. Project Structure Overview
The framework follows a clean and scalable folder structure:

Assets/
 ├── Scripts/
 │    ├── EnemyAI/
 │    │    ├── Core/
 │    │    │    ├── EnemyAIController.cs
 │    │    │    ├── EnemyBlackboard.cs
 │    │    ├── FSM/
 │    │    │    ├── IState.cs
 │    │    │    ├── StateMachine.cs
 │    │    │    ├── IdleState.cs
 │    │    │    ├── PatrolState.cs
 │    │    │    ├── ChaseState.cs
 │    │    │    └── AttackState.cs
 │    │    ├── BehaviorTree/
 │    │    │    ├── BTNode.cs
 │    │    │    ├── Selector.cs
 │    │    │    ├── Sequence.cs
 │    │    │    └── ActionNode.cs
 │    │    ├── Perception/
 │    │    │    ├── EnemyPerception.cs
 │    │    │    └── VisionSensor.cs
 │    │    └── Movement/
 │    │         └── EnemyMovement.cs

Each folder has a single responsibility, ensuring maintainability and ease of extension.
 
4. EnemyAIController
EnemyAIController is the central brain of the AI system. It connects FSM, Perception, Blackboard, and Movement systems together.

Example:
public class EnemyAIController : MonoBehaviour
{
    public StateMachine stateMachine;
    public EnemyBlackboard blackboard;

    void Update()
    {
        stateMachine.Update();
    }
}

 
5. Finite State Machine (FSM)
FSM handles macro-level behavior. States can be easily extended or replaced.

Example Idle State:
public class IdleState : IState
{
    public void Tick()
    {
        // Wait for target
    }
}

State transitions are controlled inside Tick() based on Blackboard data.
 
6. Behavior Trees
Behavior Trees are used to implement decision logic such as attacking, chasing, or retreating.

Example Action Node:
ActionNode attackNode = new ActionNode(() =>
{
    if (!blackboard.isInAttackRange)
        return BTNode.State.Failure;

    Attack();
    return BTNode.State.Success;
});

 
7. Perception System
Perception allows enemies to sense the environment. Currently, the framework provides a VisionSensor.

VisionSensor scans the area using Physics.OverlapSphere
to detect potential targets.

 
8. Enemy Movement
EnemyMovement is responsible for physically moving the enemy towards a target.

movement.MoveTo(target.position);

 
9. Extending the Framework
You can extend the framework by:
• Adding new FSM states (Flee, Search)
• Adding new sensors (Hearing, Damage)
• Adding BT Decorators (Cooldown, Inverter)
• Integrating NavMesh for pathfinding

 
The Unity Game Enemy AI Framework by Unity King provides a strong foundation for creating intelligent, scalable enemy behavior. It is suitable for indie developers, studios, and R&D teams.
For updates and advanced systems, visit https://unityking.com

