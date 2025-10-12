---
{"dg-publish":true,"permalink":"/0-inbox/odin-project-git/","created":"2024-01-07T17:00:29.788+07:00","updated":"2025-10-12T21:19:46.495+07:00"}
---


## cs50

we can host git, but most famous one is to host on github
### Why Git?
- track change of code by saving snapshots
- synchronize code between different people
- test changes to code without losing original
- revert back to old version of the code




## project odin
> Please refer to [[0 Inbox/Introduction to Version control with Git\|Introduction to Version control with Git]] for the Datacamp note. This one is only from the Project Odin.

Git comes installed with most linux distribution, but it won't be accessible via Windows Powershells or Commands Prompt unless installed
## The seven rules of a great Git commit message
![Git-Goodcommiting.png|550](/img/user/3%20Resources/Attachment/Git-Goodcommiting.png)
> [!note] Keep in mind: This has all been said before.
- Separate subject from body with a blank line
- Limit the subject line to **50 characters**
- Capitalize the subject line
- Do not end the subject line with a period 
- Use the imperative mood in the subject line
	- This commit will `___________` , **it should fit this sentence!**
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how


## Basic Commands
- create repo via `git init`
- delete repo via `rm .git -f -r` (just remove .git folder)
- `git status`
- `git push` = `git push origin main`
	- origin = name of the remote (destination)
	- main = name of the local branch that you're pushing, and the branch name you want to update on the origin (remote)
		- if the branch does not exist on the origin, it will create a new one.
- `git add`
- `git status`

## Terminology
- origin, is a remote name (a nickname that git give to the remote repository when you clone a repo)

## SSH Private vs Public Key
- **Private key** = your secret stamp to sign challenges (never sent).
- **Public key** = the copy GitHub stores to verify those signatures.
- You can use `ssh-keygen -t ed25519` to generate SSH key (it will be stored at `~/.ssh/id_ed25519`)