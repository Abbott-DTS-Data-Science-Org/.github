
latest revised date: 11-DEC-2023


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


**allow auto-merge**
  - QOL for PRs
  - go to your repo -> settings -> scroll down to pull requests section -> check allow auto-merge


**setting up commit signing**
  - https://docs.github.com/en/authentication/managing-commit-signature-verification
  - displaying commit verification in github web interface
    - click on your profile top right -> settings -> access -> ssh and gpg keys -> vigilant mode -> enable flag unsigned commits as unverified
  1. open Git Bash
  2. check for existing gpg keys: `gpg --list-secret-keys --keyid-format=long`
    - if something returns, move to step #2.7
    - else,
      1. generate a key via gpg: `gpg --full-generate-key`
      2. specify type of key (default is fine. just hit enter)
      3. specify key size (default is fine. just hit enter)
      4. enter length of time key should be valid (0 is fine in most cases- hit enter)
      5. verify selections are correct, enter user ID information, and enter a passphrase
      6. get gpg key ID: `gpg --list-secret-keys --keyid-format=long`
      7. copy the longform of the gpg key ID (line with "sec")
        - in below example, gpg key id = 3AA5C34371567BD2\
          >$ gpg --list-secret-keys --keyid-format=long\
          /Users/hubot/.gnupg/secring.gpg\
          \--------------------------------\
          sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]

      8. run `gpg --armor --export 3AA5C34371567BD2`, and copy entire output including "-----BEGIN PGP PUBLIC KEY BLOCK-----" and "---END PGP PUBLIC KEY BLOCK-----"
      9. move to github web interface and navigate to profile top right -> settings -> access -> ssh and gpg keys -> New GPG Key
      10. enter a name (doesn't really matter what it is), and paste output from #8
  3. tell github about the signing signature
    1. using ID from step #2.7 above, run `git config --global user.signingkey 3AA5C34371567BD2`
      - MAKE SURE TO REPLACE THE GPG KEY ID STRING WITH YOUR UNIQUE ID FROM STEP #2.7 ABOVE
    2. configure Git to sign all commits by default: `git config --global commit.gpgsign true`
    3. verify GPG is set to the necessary path
      1. locate gpg. run: `where gpg`
      2. verify gpg has the proper path. run: `git config --global gpg.program "C:\Program Files\Git\usr\bin\gpg.exe"`
          - the path string should be what step #3.3.1 outputted
          - the path string must be in quotes


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
