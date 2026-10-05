# GAME_PROGRAM-EX--7

# AIM
To create an AI character in Unreal Engine that roams randomly within a NavMesh area and chases
the player when they come within a certain range, using Behavior Trees, Blackboard, and AI
Perception.

## STEPS
1. Setup Navigation
Add a NavMeshBoundsVolume to your level and scale it to cover the roamable area.
Press P to confirm the green nav area is visible (indicating navigable space).
2. Create AI Character
Create a Blueprint character (e.g., BP_AIEnemy ) with a skeletal mesh and AIController class.
Create an AI Controller Blueprint (e.g., BP_AIController ) and assign it to the character.
3. Enable AI Perception
In BP_AIController , add an AIPerception component.
Configure a Sight sense (set detection range, lose sight range, peripheral vision angle).
Bind OnPerceptionUpdated to update a blackboard value
(e.g., CanSeePlayer and PlayerActor ).
4. Set Up Blackboard
Create a Blackboard with the following keys:
TargetLocation (Vector)
PlayerActor (Object)
CanSeePlayer (Bool)
5. Create Behavior Tree (BT_AI)
Structure it like this:
AI Random Roam with Chase - Unreal Engine 🎯 Aim

## Procedure
Root
Selector

Sequence (Chase Player)

Blackboard Check: CanSeePlayer == truTask: Find Random Location → TargetLocation
Move To: TargetLocation

6. Custom Task: Find Random Location
Create a new BTTask_BlueprintBase to get a random reachable point using:
Set the result to the TargetLocation blackboard key.

8. Test the AI
Add a player character to the level.
Place the AI enemy in the map and assign its controller and behavior tree.
Press Play: the AI should roam when the player is far and chase the player when within
sight.
UNavigationSystemV1::GetRandomReachablePointInRadius()


The AI character roams randomly within a defined area. When the player enters its sight range, the
AI stops roaming and begins to chase the player until the player is out of sight, after which it
resumes roaming.

## Output
<img width="1041" height="531" alt="Screenshot 2026-10-05 203546" src="https://github.com/user-attachments/assets/592c0225-ee9a-4814-8f64-e1e4f5accee5" />
<img width="1046" height="438" alt="Screenshot 2026-10-05 203622" src="https://github.com/user-attachments/assets/1c527131-ea56-43de-89d9-2def76ecab1d" />
<img width="1042" height="392" alt="Screenshot 2026-10-05 203635" src="https://github.com/user-attachments/assets/ff8e8397-5188-471f-848f-79c5aa7594c4" />






## Result
The AI character roams randomly within a defined area. When the player enters its sight range, the
AI stops roaming and begins to chase the player until the player is out of sight, after which it
resumes roaming.

