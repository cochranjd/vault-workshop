
# Core Entities
## Tasks
Tasks are actionable items to be accomplished. Tasks should be granular enough to be completed in a single effort. If this is not possible, I should break the task down into pieces. For instance, a 5 file PR could be represented by a single "Review PR 123 for John Doe", while a larger 500 file PR would be best broken down as "Review 10 files from PR 123 for John Doe" (in this case, a more appropriate task may be "Request John Doe decompose PR 123 into smaller PRs).

### Associated Dates
#### Start Date
Some tasks may have optional start dates. If provided, a start date provides the first day in which this becomes _actionable_. Start dates are a way to _hide_ a task until a specified period of time.

#### Due Date
Some tasks may have optional due dates. If provided, a due date provides the day on which a task is required to be finished. These should only be used in cases where they truly represent a final acceptable date. Otherwise, overuse of this can begin to provide too much noise to detect an appropriate signal when deciding which tasks require action.

### Examples of tasks:
- Finish cyber security training course
	- due date: next Friday
- Enroll in benefits
	- start date: 2025-11-15
	- due date: 2025-11-19
- Input quarterly goals for John Doe
	- start date: 2026-01-01
- Add e2e test coverage to survey component
	- no associated dates
- Get everyone on the team added to Snowflake
	- no associated dates

### Collection/Tracking Rules
- Tasks can be created in any document using the task formatting approach `[] task name`
- Tasks with no associated dates **MUST** be surfaced via **REGULAR REVIEWS**
- Use tag `doit` to mark items as expected to be completed _today_
* Tasks should be tagged with associated people using `people/john-doe` style tags
* Tasks should be tagged with associated topics using `topics/some-project` style tags

## Ideas
Ideas are non-actionable items that need to be expanded, researched, etc. These will generally represent high level ideas that can be decomposed into many tasks, a project charter and other supporting documents. The primary concern with ideas is that they are easily surfaced when necessary.

### Examples of ideas:
- Move e2e tests to Cypress
- Change max PR size to 100 lines
- Move to Vite for front end build

### Collection/Tracking Rules
- Ideas should be in their own documents with a frontmatter tag `core/idea`
- Ideas should include a `status` attribute set to one of `open, completed, closed`
	- `open` will be the default value and indicates an idea that has been logged, but not acted upon
	- `completed` represents an idea that has been processed and either completed or converted to a project
	- `closed` represents an idea that has been closed without taking any actions
- Ideas should end up in the `XX - Ideas` folder, though they may start in the `XX - Inbox`
- Ideas that are `open` should be surfaced via **REGULAR REVIEWS**

## Notes
Notes are documentation about _things_. This could be meeting minutes, research documentation, planning sessions, scratch pads, etc.

### Examples of notes:
- NGIE triage meetings
- Useful SQL queries for performance
- OpsGenie rotation planning notes

### Collection/Tracking Rules
- Notes can be more freeform
- If applicable, tags should be provided in the front matter to make notes easily surfaced by topic
- **Meeting Minutes** has specific rules called out below

### Notes::Meeting Minutes
Meetings minutes are a type of note that represent documentation of a particular meeting. These notes should provide information that helps connect this meeting to the broader topic, along with the individuals involved with the meeting.

The attributes for meetings should include:
- topic
	- what is being discussed
- attendees
	- attendees list in the form of `people/john-doe` so these are tied directly to folks attending
- when
	- the date & time of the meeting
- tags
	- There should be at least one tag of the form `topics/some-project`
	- `core/minutes`

### Collection/Tracking Rules
- Meeting minutes should end up in `XX - Minutes`


## Projects
A project is simply a trackable item that can contain multiple associated documents that make sense to be colocated. A project should have the following:
- A subfolder in `XX - Projects`
- A project charter, which is the "home page" for the project and contains the following
	- title
	- description
	- due date (if applicable)
	- status
		- open
		- in-progress
		- completed
		- closed
	- An index of all associated todos
	- An index of all associated notes
### Collection/Tracking Rules
- Projects in the `open` or `in-progress` state should be surfaced in **REGULAR REVIEWS**

## Daily Notes
Daily notes are the engine behind the entire system. Daily notes are responsible for letting me easily see my day and should surface:
- Tasks that need to be done today via due date (due within the next 3 days)
- Tasks that have been marked with `doit` (meaning I've consciously decided to do these)
- Meetings I have on the calendar today with links to their notes
- PTO of team members

It is important not to let Daily Notes become a repository for _everything_, which makes it hard to take anything meaningful from them.

When possible, daily notes should default to dynamic queries so that they pick up content.

# Tags
Tags are very important to the system as they allow Obsidian to easily find all relevant data for a given topic.

It is important to approach tags with consistency.

## Types of tags
- references to people `people/first-last`
- references to topics `topics/some-topic`
- references to projects `topics/project`

### Notes about tags
If tags are too granular, it can become hard to gather all relevant items. For this reason, projects should share the `topics/xyz` form. If a project is a subset of a broader topic, it should take on a name that allows it to be easily separated. For instance if `topics/ngie` represents a common tag, but we're working on a project for live response images, perhaps `topics/ngie-live-response-images` would be appropriate. Additionally, adding _both_ may make sense if I'd like `ngie` searches to also surface `ngie-live-response-images` related work.
# Structure
The below structure is proposed for tracking items.

- 00 - Inbox
	- This represents a default landing spot for all things. Ideally, this should be empty, only serving as a repository for incoming documents that have not had the opportunity for processing.
- 01 - Daily Notes
	- This contains the automated daily notes
- 02 - Meetings
	- This contains meeting minutes notes
- 03 - Ideas
	- This contains ideas
- 04 - Projects
	- This contains projects
- 05 - Notes
	- This contains notes that do not have a separate place to live (not meeting minutes, ideas or projects)
- 06 - Tracking
	- 00 - PTO
		- Tracks PTO entries from team members
	- 01 - Key Dates
		- Tracks key dates
- 99 - Meta
	- 00 - Documentation
		- Documentation about the system
	- 01 - Templates
		- This contains templater templates to support the workflows
	- 02 - Scripts
		- This contains JS scripts to support the workflows