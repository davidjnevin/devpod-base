# Devpod :- base image

Devpod base settings for future more customized versions.

Using `mise`, `chezmoi` and `devcontainers`.

## Prerequisits:

`Docker` and `devpod cli` installed.

## To use:

Clone the repo onto your machine.

```bash
git clone git@github.com:davidjnevin/devpod-base.git .
cd devpod-base
```

Edit the devcontianer json file to set your username.

This will define both the name of the user with sudo priviledges and the folder strucutre.

**NB**: The remoteUser and the USERNAME in the devcontainer.json must match.

```json
{
  "build": {
    "context": "..",
    "dockerfile": "Dockerfile",
    "args": {
      "USERNAME": "david"  <--- must match
    }
  },
  "remoteUser": "david",  <-- must match
  "containerUser": "root",
  "postCreateCommand": "scripts/setup"
}

Then run the following commands from within the devpod-base folder.

Cavat: This assumes you have a dot files repo setup for use with mise. See this repo for my early attempts at this.

Also I use nvim in my devpods, so my ide is set to none. Other options include openvscode or vscode.

The full documentation is available at


```bash
devpod provider add docker
devpod up . --ide none --dotfiles git@github.com:<github_username>/<dotfiles-repo>  (--recreate) # start/mount a devpod using the current directory, no ide set and a specified dotfiles repo. (recreate rebuilds the container)
devpod ssh  # give a list of available containers to ssh into
```


```

