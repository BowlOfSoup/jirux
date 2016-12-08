jirux
=====
With these set of scripts you can do several Jira related actions from the commandline. 
Read the help text (command -h) for the scripts if you would like more detail.

Scripts that currently work: 
* **jirux-create**, Create a set of pre-defined subtasks for a parent story.
* **jirux-edit**, Edit a subtask for a given parent story. Add a comment, Transition and/or assign.

Installation
------------
`git clone https://github.com/Faiawuks/jirux.git ~/jirux`

### Configuration
You will need a `config.ini` file in the `jirux` directory which has the following format:

```bash
[jira]
url=
user=
```

### Make available
Run the following installation script (in Jirux dir) to make the jirux scripts available from anywhere.

`./helpers/install`

### Uninstall
Remove the jirux directory, and if you used the install script, remove the entry from your _~/.bash_profile_. 

What does it do?
----------------
### jirux-create

With this script you can create a **set** of subtasks, or just one task, for a given story.
You can create your own set of tasks by creating a %tasksetname% file and run the script with the -f command.
If you do not provide any arguments for the script it will run interactively.

```
Usage: jirux-create [options]
    -h This help text
    -s Storynumber
    -u Jira Username, If not given, script will take current username.
    -p Jira Password, If not given, script will ask.
    -k Projectkey, Key before - (dash) in Storynumber. If not given, script takes configured, or logged-in user.
    -t File with a taskset,  File within the 'tasks' with defined tasks, one task per line.
    -o One subtask, give summary and create only one subtask.

Example:
    $ jirux-create -s TB-1111 -k TB -u your.username -t task/default
    $ jirux-create -s TB-1234 -o "One new subtask"

If you incorrectly enter your password twice, you manually have to login into Jira again!
```

### jirux-edit

With this script you can edit a (given) story or subtask. Check the actions below (e.g. transition, assign, add comment).
If you do not provide any arguments, the script will be interactive.

```
Usage: jirux-edit [options]
    -h This help text
    -s Storynumber
    -u Jira Username, If not given, script will take current username.
    -p Jira Password, If not given, script will ask.

   Actions:
    -t Transition a subtask trough the workflow.
    -a Assign a subtask to the given username (or current logged-in user).
    -c Add a comment on a subtask.
    
If you incorrectly enter your password twice, you manually have to login into Jira again!
```
