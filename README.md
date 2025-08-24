# Red Team Notebooks
A way to share and iterate on tradecraft.

Goals:
- Distill complex tradecraft into Jupyter notebooks
- Optimize routine workflows and tasks related to red teaming
- Group related tradecraft together

Prereqs: Install Jupyterlab using something like the following.

```
# install jupyterlab through pipx
pipx install jupyterlab --include-deps

# inject some extra packages into the venv created by pipx --
# the jupyterlab_execute_time is handy for having timestamps
# in logs. install other packages like pandas you want to use.
pipx inject jupyterlab jupyterlab_execute_time pandas

pipx ensurepath

# start jupyter with `jupyter-lab --no-browser`
```

How it works:

Start by installing and configuring Jupyterlab on the machine you want to execute tradecraft / commands from. This is often a disposable, cloud hosted VM. This might be a recon box, attack box, or serve some other function in the red team operation. Anyway, SSH into the machine like normal, but set up a local port forward on the way in that pointed to the Jupyter web UI. Using the port forward, log in through the web browser on the device physically in front of you. From here, you can execute commands in a notebook using:

`! cat /etc/hosts`

The `!` at the beginning tells Jupyter to execute the command -- https://stackoverflow.com/questions/38694081/executing-terminal-commands-in-jupyter-notebook#48529220

Why use notebooks? 

Notebooks are useful for collaboration and refinement. There are many ways to perform red team operations. Establishing an SSH session into a VM, starting a `screen` session with logging, and then performing actions that lead to accomplishing an objective is one way. This works, but searching `screen` or `tmux` logs is a pain. Jupyter notebooks can be executed and saved with command output and timestamps. This makes for easy ingest into reporting tools like Ghostwriter.
