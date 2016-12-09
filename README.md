# Ansible Role: AWS SDK

[![Build Status](https://travis-ci.org/gametize/ansible-role-aws-sdk.svg?branch=master)](https://travis-ci.org/gametize/ansible-role-aws-sdk)

This role will install the `boto3`, the [Python SDK recommended by Amazon AWS](https://aws.amazon.com/sdk-for-python/), via `pip`.

`pip` will be installed if absent, via the `get-pip.py` script (default) or thru the OS package managers.

## Requirements

If using RedHat/CentOS, make sure you have the EPEL repository installed prior to using this role (you can install it using the `geerlingguy.repo-epel` role).

## Role Variables

#### Optional variables

  - `aws_sdk_boto3_version`: Version of `boto3` to install. If this variable is not provided, pip will install the latest listed in PyPI.

#### Default values (see `defaults/main.yml`)

    aws_sdk_pip_use_package_manager: false

Pip will be installed using the `get-pip.py` script. If set to `true`, pip will install using *apt* (Debian) or *yum* (Red Hat).

#### Variables (see `vars/main.yml`)

```
aws_sdk_pip_script_url: https://bootstrap.pypa.io/get-pip.py
aws_sdk_tmp_script_path: /tmp/get-pip.py
aws_sdk_apt_cache_valid_time: 300    # Skip apt update if cache is less than 5 min.
```

## Dependencies

None

## Example playbook

```
- hosts: all
  roles:
    - gametize.aws-sdk
```

## Tests

Travis tests (`.travis.yml`) are set up according to this [article](http://www.jeffgeerling.com/blog/2016/how-i-test-ansible-configuration-on-7-different-oses-docker) by geerlingguy.

Gitlab CI tests are set up similarly, and can be run with [gitlab-runner](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner). Example of running this locally:

    gitlab-ci-multi-runner exec shell test_centos7

## License

MIT

## Author Information

LIM EnSheng (ensheng@gametize.com)
