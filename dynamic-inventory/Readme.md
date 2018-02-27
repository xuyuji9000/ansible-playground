# Before Start

1. Create a server on aliyun

2. Copy hosts.default as hosts

3. Add the public ip to hosts

# SetUp python environment

1. `virtualenv -p python3 venv`

2. `source ./venv/bin/activate`

3. smoke test`./ec2.py --list`

# Commands

## Basic

- check server availability

    `ansible -i hosts all -m ping -u root`

- list all hosts

    `ansible -i hosts --list-host all`

- check server uptime

    `ansible all -i hosts -m command -a 'uptime' -u root`

- get servers public ip

    `aliyuncli ecs DescribeInstances --RegionId cn-shanghai --output text --filter Instances.Instance[0].PublicIpAddress.IpAddress`

- run command on server

    `ansible -i hosts -u root all -a "/bin/echo 'test'"`

- disable host key checking

    `export ANSIBLE_HOST_KEY_CHECKING=False`


## Get AWS dynamic inventory

1. set up python virtual environment, activate

    ```
    virtualenv -p python3 venv
    source ./venv/bin/activate
    ```

2. set environment variable

    ```
    export AWS_ACCESS_KEY_ID='access_key'
    export AWS_SECRET_ACCESS_KEY='secret_access_key'
    ```

3. list dynamic inventory

    `ansible -i ec2.py -u ubuntu --list-hosts ap-southeast-1`