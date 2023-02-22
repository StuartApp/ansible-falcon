Role Name
=========

The purpose of this role is to download, install and configure CrowdStrike Falcon sensor it on our EC2 instances. The sensor must be downloaded from Crowdstrike Cloud using MFA.

In the first step, we will connect to the mentionced cloud environment to obtain a `Bearer token` which will be used to download the `pkg`. The distribution used is compatible with Ubuntu 16/18 and 20.

After downloading and installing the `pkg` - the `falcon-sensor` must be configured. According to the official documentation both the Customer ID (CID) and `provisioning-token` must be provided.

Requirements
------------

![Ansible](https://img.shields.io/badge/ansible-2.8.2-green)

Role Variables and Secrets
--------------

Supported variables:

* `falcon_cloud` - CrowdStrike API URL for downloading the Falcon sensor.
* `falcon_install_tmp_dir` - Where should the sensor file be downloaded to on Linux

Supported secrets:

This information can be found on under Falcon UI and won't be changed in the near future:

* `falcon_client_id` - CrowdStrike OAUTH Client ID
* `falcon_client_secret` - CrowdStrike OAUTH Client Secret
* `falcon_customer_id` - CrowdStrike Customer ID
* `falcon_provisioning_token` - Falcon Installation Token

Dependencies
------------

No dependencies

Example Playbook
----------------

Include the role in `requirements.yml` as follows to test the changes depending on the branch (master of the one to be tested)

```yaml
- src: https://github.com/StuartApp/ansible-falcon.git
  name: stuart.falcon
  version: < branch name >
```

After adding the role to the requirements and installing we can proceed to call it from a playbook:

```yaml
    - name: myplaybook
      hosts: servers
      roles:
        - {role: stuart.falcon, tags: role-falcon}
```

Author Information
------------------

This role was created while working for Stuart Delivery.
