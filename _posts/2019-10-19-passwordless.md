---
layout: post
title:  "Password less Login in Linux"
date:   2019-10-19
excerpt: " "
tag:
- Linux
comments: true
---

In order to log into a Linux machine without a password, follow the following steps:

1. On a client machine, run the command "ssh-keygen".
2. Enter the passphrase if required. Else, leave it blank and press Enter.
3. A new SSH key will be generated.
4. Use the command "ssh-copy-id server1/172.25.1.11" (enter either the hostname or IP) to copy the command to the server.
5. Once the above command is entered, the user who is currently logged in on a client machine would be able to access the server machine without a password.
6. Check if a login without a password works using the command "ssh student@server1". If all is setup correctly then you should be able to log in without a password and should a terminal window of the server machine.
