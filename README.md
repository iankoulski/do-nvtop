# [do-nvtop](https://github.com/iankoulski/do-nvtop)

A [depend-on-docker](https://github.com/iankoulski/depend-on-docker/tree/to) [nvtop](https://github.com/Syllo/nvtop) container, based on [Ubuntu](https://ubuntu.com) and the [do-framework](https://bit.ly/do-framework)

# Usage

Run locally using `docker`:

```bash
docker run -it --rm iankoulski/do-nvtop nvtop
```

Run on Kubernetes using `kubectl`:
```bash
kubectl apply -f https://bit.ly/do-nvtop-daemonset
```

When running on Kubernetes, to view metrics, run:

```bash
kubectl exec -it $(kubectl get pods | grep htop | head -n 1 | cut -d ' ' -f 1) -- nvtop
```

# Details

This project is configured with defaults which work in most cases. To change the default settings, execute `./config.sh` or just edit the `.env` file. One of the settings in the project is the target orchestrator `TO`. This setting configures the container to run locally using docker, or on a kubernetes cluster, using kubectl. Switching to a different orchestrator is as simple as configuring the `TO` setting.

The project contains the following scripts:
* `config.sh` - open the configuration file .env in an editor so the project can be customized
* `build.sh` - build the container image
* `test.sh` - run container unit tests
* `push.sh` - push the container image to a registry
* `pull.sh` - pull the container image from a registry
* `run.sh [cmd]` - run the container, passing an argument overrides the default command
* `status.sh` - show container status - running, exited, etc.
* `logs.sh` - tail container logs
* `exec.sh [cmd]` - open a shell or execute a specified command in the running container

# License
Please see the [LICENSE](LICENSE) file for details.

# References

* [do-framework](https://bit.ly/do-framework)
* [depend-on-docker](https://bit.ly/do-docker-project)
* [Ubuntu](https://ubuntu.com)
* [nvtop](https://github.com/Syllo/nvtop)

