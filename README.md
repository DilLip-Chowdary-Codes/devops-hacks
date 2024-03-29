# devops-hacks
DevOps-Hacks is a public repository of solutions and tips related to backend development, DevOps, Linux, and cloud computing.

Contents:
- AWS
  - AWS Codeartifact
    - [Codeartifact Authentication automation](https://github.com/DilLip-Chowdary-Codes/devops-hacks/edit/main/README.md#codeartifact-authentication-automation)

## AWS

### CodeArtifact

#### Codeartifact Authentication automation:

Codeartifact authentication token will only valid for 12 hrs only, and to install/publish packages to codeartifact we need to authenticate again.

We used to run the codeartifact cli commands to authenticate when the token expires, now you can run the command generated by below script which will add the authencation commands to ~/.profile file, so that everytime you login to your device, codeartifact token will be updated.

Disclaimer: This will only work if you're working less than 12 hrs once login to developer system.

You can find the [script here](https://gist.github.com/DilLip-Chowdary-Codes/6d5e72546c62306b80d10df5befc97b4)

#### Prerequisites:

- Make sure aws cli is upto date, run the below command to update the aws cli.

  ```bash
  pip3 install -U awscli
  ```
#### Usage:

Run the below attached script `codeartifact_auth_automation_cmds_generator.py` to generate commands which automate the codeartifact authentication.

##### For npm Auth

```bash
python3 codeartifact_auth_automation_cmds_generator.py --aws-profile <profile>  --codeartifact-domain <domain> --npm-namespaces "dc kc" --npm-auth --pypi-auth
```

##### For pypi Auth

```bash
python3 codeartifact_auth_automation_cmds_generator.py --aws-profile <profile>  --codeartifact-domain <domain> --pypi-auth
```

#####  For both npm and pypi:

```bash
python3 codeartifact_auth_automation_cmds_generator.py --aws-profile <profile>  --codeartifact-domain <domain> --npm-namespaces "dc kc" --npm-auth --pypi-auth
```

**Script Args**:

- `--aws-profile`: AWS Profile
- `--codeartifact-domain`: codeartifact domain name (specific to aws account)
- `--npm-namespaces`: space seperated npm namespaces to authenticate( for example: "ib rn")
- `--npm-auth`: bool field to specify to generate  npm auth related commands
- `--pypi-auth`: bool field to specify to generate pypi auth related commands
