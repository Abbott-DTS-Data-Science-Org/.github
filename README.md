

**best practices**
  - branch protection rules
    - main branch protection
      - requires 2 reviewer approvals
  - pull request (see pull request process below)
  - commits
    - adding meaningful commit message
    - enforcing squash commits to maintain a clean commit history
  - branching strategy
    - dev (develop)
    - main
  - sending email notifications
    - making changes in pull request
      - adding comments, approving PR, github actions, new release, etc.
  - github user groups
    - DS group - entire project lifetime
    - DE group - mainly during prototype phase
  - release strategy
  - webhooks
  - github issues
  - github actions
    - helps keep dependencies in check


**README.md**
  - required information:
    - Status
      - should be updated throughout project's lifeline
      - also list if the POC is moving forward to prototype. if not, clearly list why it is not moving forward
    - POC Name
    - Division
    - Function
    - Problem Statement
    - Timeline
      - clearly state the timeline per project phase if applicable
      - e.g. POC: 01-NOV-2023 - 04-DEC-2023, Prototype: 01-JAN-2024 - 04-MAY-2024
    - Code collaborators
    - Tags
      - simple tags to help identify characteristics of the project, helping with if the code/project can be repurposed
  - supplemental information
    - deeper description of what is contained in each folder, should the project move past POC and/or further


**repo structuring process**
  - initially used with the assumption that the project is currently a POC
  - README.md MUST BE INITIALIZED WITH THE 8 REQUIRED INFORMATION PROMPTS
  - if the POC moves to prototype,
    1. update README
    2. create a folder named "POC" which will contain all currently existing code/material within it
    3. initialize a folder named "Prototype" which will contain all code/material for prototype phase
  - if the POC does not move to prototype
    1. update README
    2. create a folder named "POC" which will contain all currently existing code/material within it
    3. make sure README contains why the POC is not moving forward


**commits**
  - concise, meaningful message of what was done for title
  - relevant and supplemental information for the description
  - consider the questions that reviewers ask during pull request


**pull request process**
  - always from dev to main
  1. meaningful commit name
    - short, concise message of what was done
  2. elaborate a bit more on the commit description
    - was there a specific date that the code needed to be merged for? important iteration? key client-defined milestones?
    - relevant, supplemental information
  3. reviewers
    - Liz
    - lead/supporting data scientists on the project
    - items to consider when reviewing:
      - are the updates in the pull request relevant?
      - will the code still run/work properly? (github does a good job with its own testing, but visual inspection may be needed)
      - is the code optimized?
        - does the code have any unnecessary lines? (e.g. testing code, extra EDA that would not be helpful for the code's original purpose)
      - could the code be more object-oriented?
      - does the code have meaningful, descriptive comments?
      - is the README sufficiently up-to-date?
  4. assignees
    - whoever is creating the pull request
  5. notify the reviewers
    - github should automatically send email notifications if you are added to the pull request, but messaging the reviewers directly increases visibility without blocks
  6. once reviewers give the go-ahead, the person initiating the pull request must then merge the pull request themself
