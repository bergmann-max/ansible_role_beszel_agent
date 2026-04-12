# ansible_role_beszel_agent

[![Ansible](https://img.shields.io/badge/ansible-%3E%3D%202.17-EE0000?logo=ansible&logoColor=white)](https://www.ansible.com/)
[![Platform](https://img.shields.io/badge/platform-Ubuntu-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Beszel](https://img.shields.io/badge/beszel-agent-blueviolet?logo=docker&logoColor=white)](https://beszel.dev/)
[![License](https://img.shields.io/badge/license-Unlicense-blue)](LICENSE)

An Ansible role that deploys the Beszel agent via Docker Compose to monitor a host with a Beszel hub instance.

## Requirements

- Ansible >= 2.17
- Docker installed on the target host
- `community.docker` collection

## Role Variables

Variables defaults (`defaults/main.yml`):

| Variable              | Default                        | Description                                      |
|-----------------------|--------------------------------|--------------------------------------------------|
| `beszel_agent_dir`    | `/opt/beszel-agent`            | Directory where the agent files are deployed     |
| `beszel_agent_owner`  | `""`                           | Owner of the agent directory and files           |
| `beszel_agent_group`  | `"docker"`                     | Group of the agent directory and files           |
| `beszel_agent_image`  | `"henrygd/beszel-agent:latest"`| Docker image to use for the Beszel agent         |
| `beszel_agent_port`   | `45876`                        | Port the agent listens on                        |
| `beszel_agent_key`    | `""`                           | Public key from the Beszel hub for authentication|
| `beszel_hub_url`      | `""`                           | URL of the Beszel hub instance                   |

## Installation

Include via a `requirements.yml` and install with `ansible-galaxy`:

```yaml
# requirements.yml
roles:
  - name: beszel_agent
    src: git+ssh://git@github.com/bergmann-max/ansible_role_beszel_agent.git
    version: main
    scm: git
```

```bash
ansible-galaxy install -r requirements.yml
```

---

## Tags

| Tag     | Description                        |
|---------|------------------------------------|
| `beszel` | Runs all Beszel agent tasks       |

---

## Handlers

| Handler                  | Description                                              |
|--------------------------|----------------------------------------------------------|
| `Restart beszel-agent`   | Recreates the Docker Compose stack when config changes   |

---

## License

Unlicense

---

## Dependencies

No dependencies.

---

## Author Information

Max Bergmann
