# Simple Spec Builder
Ssb is a skill that helps in the decomposition and exploration of user stories arising from a task, while also allowing the definition of specifications for the stories that the development agent will generate.

## Recommended Workflow

1. Create a `.tasks` folder within the root of the repository.
1. Create a subfolder with the ID of the task to be performed, for example: `.tasks/EXA-1001`.
1. Within the subfolder created in step 2, create a file named `raw-requirement.md` where we place the contents of the requirement to be worked on in this task.
1. Run the skill to decompose the requirement into user stories and specifications for each of them. It will generate an `index-spec.md` file containing the execution order of the specs, and an `open-questions.md` file to resolve inconsistencies, ambiguities, and other issues that arose during decomposition.
1. It will also generate a `solution-diagrams.md` file with sequence, class, and other supporting technical design diagrams. These diagrams help audit the flow to be implemented before making the change.
1. Resolve each of the questions in `open-questions.md` to explore the solution. At this point, the specs generated in the previous step can be refined and corrected.
1. Run the agent again to help refine the user story specifications.
1. Once the ambiguity resolution loop is closed, proceed to plan mode.
1. With a finalized plan, run the agent to build the solution.
