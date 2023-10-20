# Discussion

## Questline

- Questline is a solution to user "choice exhaustion" in larger graphs. Alot of "ready" tasks in a graph can overwhelm the user when they try and pick a task to work on, especially when other tasks rely on completion.
	- The software will pick for you, and provide a gamification of the system in the form of quests. Each quest will be a seperate branch of the graph, allowing the user to systematically work up towards the goal without having to decide what to work on.

### Does the problem matter? 

- Large graphs in the Mikado Method can lead to clutter and be disorganized. Without some sort of guided task tracker for the user, the UI will become overwhelmind and give the user "choice exhaustion"
	- It was brought up to the client and he liked the idea, as he had dealt with large graphs before (on paper)

- Multiple customers will use the feature as each graph will eventually grow in size as a project progresses or new requirements are added. We will advertise this feature in the software, and since we aim to make it intuitive as possible, we beleive that most people will use this feature
	- Except when working on small graphs, then the feature is not needed.
		- People will not use it initially, but will eventually see the need for it.

### Is the appetite right?

- Depending on some features for the questline system, 6 weeks may not be feasable. We needed to ask ourselves a couple questions regarding the questline system.

- Should the questline look into subgraphs?
	- Looking into subgraphs would require alot of database changes. It would also significantly slow down performance, as there is a possbility of the quest being infinitely large due to subgraphs not having a depth limit. It would also be too cluttered to defeat the purpose of quests if the quest itself is very large.

- An explanation of the questline system was asked for. Daanish provided a drawing shown below, with each circle being designated as a quest. The goal node is special, and every branch not related to each other is a questline.

![Questline Partition Example](./questpartition.png)

- It was mentioned that implementation might be difficult if we have to detect which trees are seperate. A new algorithm would have to be developed and that would take a significant amount of time.
	- An alternative solution was suggested, where each primary node coming off of the goal node is considered the "parent" to a questline. Any children related to seperate questlines are shared and are processed seperately based on which quest is chosen.
		- This solution was chosen as it would be simpler to implement and we already have some of the business implemented.

- How do we order tasks?
	- The initial suggestion was to use a "depth-first" approach, where the lowest ready task in the branch would be used first
		- However, that would include searching, an expensive task and would not be responsive on large graphs

	- Alternate solution was proposed: since we have node types (ready, completed, blocked), we only need to sort by ready tasks. This saves us time and effort in both implementation and runtime.

- What UI are we implementing?
	- A overlay and a toolbar/modal to display the current task and the toolbar to switch quests.
	- Syncrhonization issues were brought up where the graph can change if a new task is added
		- Solution: use the graph as the source of truth and rerender on any changes.

- Are we going to draw the questline/display it?
	- No, we are just going to display the current task on the graph itself.

- Conclusions: From the discussion above, we have decided the appetite is right with the constraints and solutions we applied.

### Is the solution attractive?

- The real estate used would just be an overlay on the bottom right side of the screen so the user could determine what to work on at-a-glance.
	- It was brought up that the overlay would conflict with the "add node FAB" on mobile.
		- Solution: Move it to the top left.

- Since its a small space & questlines are an essential part of our system, the space used will be kept for the future.

- Concludes that the solution is attractive.

### Is this the right time?

- We are still in development, and no major features are currently being implemented, only just polishing previous ones (splash of news with a new feature)
	- We aim to deliver this feature at the end of the 6 week cycle

- Concludes that this is the right time for the task.

### Are the right people available?

- We have multiple people that do not have work at the moment, as we all have just been polishing UI/UX. We have individuals who can work on fullstack, as well as the concrete UI design of the feature.

- We have the expertise, midterms are almost over, and everyone has been doing small batch and want to do a big batched feature.

- Concludes that the right people are available.

