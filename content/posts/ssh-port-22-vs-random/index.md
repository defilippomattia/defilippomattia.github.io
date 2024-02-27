---
title: "SSH Login Attempts on Default (22) and Random (48931) Port"
draft: false
date: 2024-02-27T09:16:45.000Z
description: "Exploring how changing the default SSH port affects login attempts."
---

## Introduction

I wanted to see how changing the default SSH port affects login attempts. I have 2 servers running on AWS with public IP addresses. One server has SSH running on the default port (22) and the other server has SSH running on a random port (48931). I left the servers running for 48 hours and then checked the logs.

## Results

The analysis was done using the `/var/log/secure` log file and some basic Linux commands. The results are as follows:

### Default port 22

| Description                   | Command                                                                                      | Result                                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Number of lines               | `wc -l secure_22.log`                                                                        | 430                                                                                                             |
| Number of unique IP addresses | `grep -o "[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+" secure_22.log \| sort -u \| wc -l`             | 44\*                                                                                                            |
| Number of unique usernames    | `grep -oP 'sshd._?user ._? from' secure_22.log \| awk '{print $(NF-1)}' \| sort -u \| wc -l` | 16                                                                                                              |
| Usernames                     | `grep -oP 'sshd._?user ._? from' secure_22.log \| awk '{print $(NF-1)}' \| sort -u`          | admin, baikal, contador, ftpuser, git, odoo, oracle, pi, test, test1, test2, ubnt, ubuntu, user, usuario, vinod |

### Random port 48931

| Description                   | Command                                                                                         | Result      |
| ----------------------------- | ----------------------------------------------------------------------------------------------- | ----------- |
| Number of lines               | `wc -l secure_48931.log`                                                                        | 96          |
| Number of unique IP addresses | `grep -o "[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+" secure_48931.log \| sort -u \| wc -l`             | 0\*         |
| Number of unique usernames    | `grep -oP 'sshd._?user ._? from' secure_48931.log \| awk '{print $(NF-1)}' \| sort -u \| wc -l` | 0           |
| Usernames                     | `grep -oP 'sshd._?user ._? from' secure_48931.log \| awk '{print $(NF-1)}' \| sort -u`          | (no output) |

\* The number of unique IP addresses are substracted by 2 because in the logfile there is a 0.0.0.0 address and my public IP address.

## Conclusion

As you you can see, changing the default SSH port from 22 to a random port reduces the number of login attempts (not a single one in 48 hours). It would be interesting to see how much time it takes for the first login attempt on a random port.

GitHub repository is available here: https://github.com/defilippomattia/misc/tree/main/ssh-22-vs-random (not much to see, just the terraform script that creates the 2 servers on AWS)
