# Commands to use to rebuild image and push to docker
podman build -f ansible_runner_github.Dockerfile -t excalibrax/ansible_github_runner:latest
podman push excalibrax/ansible_github_runner:latest

# privledged pod creation
# If you are seeing permision denied errors, this needs to be run.
oc adm policy add-scc-to-user privileged -z default -n github-runner-tower
