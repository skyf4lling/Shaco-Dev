# Shaco

<p align="center">
<img src="https://github.com/souzomain/Shaco/assets/92044641/0576991d-0676-4587-86f0-7107c914f76d" alt="Shaco Generation" />
</p>

Shaco is a minimal C linux Agent for the Havoc-Framework (https://github.com/HavocFramework/Havoc).
Shaco communicate over http to the Havoc Teamserver using a hardcoded socket.

# Commands Available

These are the commands that the agent is supporting:

- shell { command }
- upload { localfile remotefile }
- download { remotefile } - download file from remote
- sleep { time } 
- jitter { time }
- cd { path } - change directory
- checkin - register again the agent and show informations
- pwd - show the location
- exit

# Features

Features of the Shaco agent

- Random Connect ( randomint(sleep, sleep + jitter) )
- Random hash from http send to avoid rules
- Hardcoded Http client
- Custom Memory Management
- Minimal
- No dependencies
- InLine syscall
- Hide Cmdline changing for a random process in the target

# Running and Configuration/Compilation

1. Clone

```
git clone --recurse-submodules https://github.com/souzomain/Shaco.git
```

2. Install Websocket if not existing

```
pip3 install websocket-client
```

3. After clone this repo, you can execute the python handler

```bash
python handler.py
```

4. Create a http havoc listener on Havoc, check out:

https://havocframework.com/docs/listeners

5. To compile this, you can use the havoc payload generator "Attack" -> "Payload" and Chose Shaco as option

https://havocframework.com/docs/agent

# Issues

The upload option don't work if the size of file is > 7000 because http is hardcoded and is not working with chunk, on havoc 0.6 I work on this

# TODO

TODO of the project

- Implement python support ( ex: pyload cme.py <args> )
- Implement in memory file exec ( after havoc 0.6 I work on this )
- Implement shared library injection to migrate process
- Better compilation using havoc
- Update shell command to execute async
- Create "job" command equals demon job
- Implement time to exec, ex: run_time 2020/02/02:10.05 rm -rf /
- Configure compilation to compile for macos and android 
- Implement Crypt to the communication ( after havoc 0.6 I work on this )
- Automatic agent update ( optional )
