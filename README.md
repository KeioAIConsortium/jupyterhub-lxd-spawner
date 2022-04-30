# JupyterHub LXD Spawner for KeioAIConsortium

JupyterHub Spawner for LXD.

## Development

```bash
pipenv install
```

## Behaviors of functions

behaviors of functions and situations to be called

### launch

After logging in, if your container doesn't exist, this function will be called.

Container will be created and its status will be "stopped".

### start

After loggin in, ordinarily this will be called.

If container is already running, restart the jupyterhub-singleuser process.

If container is not running, assign one gpu to it and start it.(If you want to know more details about gpu assignment program, refer to [Iris](https://github.com/KeioAIConsortium/iris) )

### poll

Check jupyterhub-singleuser program is running.

Only when the program is running, return None. Otherwise, return the number representing error message.

## short tips

### config

```python
iris_url = Unicode(
    config=True,
    help='Iris Application URL'
)
```

You can retrive the config in Spawner like above.

```python
c.LXDSpawner.iris_url = 'http://iris'
```

If your host name is `ubuntu`, Spawner calls the API, which url is `http://iris-ubuntu.lxd`.

In `jupyterhub_config.py`, configure as above.
