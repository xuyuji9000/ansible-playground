This project test out ansible.

# Before Start

1. Create a server on aliyun

2. Copy hosts.default as hosts

3. Add the public ip to hosts

# Commands

- check server availability

    `ansible -i hosts all -m ping -u root`

- list all hosts

    `ansible -i hosts --list-host all`

- check server uptime

    `ansible all -i hosts -m command -a 'uptime' -u root`

