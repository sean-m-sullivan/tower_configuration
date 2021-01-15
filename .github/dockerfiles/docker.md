# Commands to use to rebuild image and push to docker
podman build -f ansible_runner_github.Dockerfile -t excalibrax/ansible_github_runner:latest
podman push excalibrax/ansible_github_runner:latest

# privledged pod creation
# If you are seeing permision denied errors, this needs to be run.
oc adm policy add-scc-to-user privileged -z default -n github-runner-tower

# Required for Ansible tower install for various creation privledges.
oc adm policy add-cluster-role-to-user cluster-admin developer