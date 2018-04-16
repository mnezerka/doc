
Mutt
====
This is a quick guide to setting up mutt to work with GMail's IMAP interface.

Essentials: configuration options
---------------------------------
Settings::

    set imap_user = 'yourusername@gmail.com'
    set imap_pass = 'yourpassword'
    
    set spoolfile = imaps://imap.gmail.com/INBOX
    set folder = imaps://imap.gmail.com/
    set record="imaps://imap.gmail.com/[Gmail]/Sent Mail"
    set postponed="imaps://imap.gmail.com/[Gmail]/Drafts"

You probably want to::

    set `record=""`

if you're using the GMail SMTP server, as it handles saving the sent mail anyway. You can also set the mbox::

    set mbox="imaps://imap.gmail.com/[Gmail]/All Mail"

...which means that when you exit mutt, it will prompt you to archive your read messages.
If you are using the  trash_folder patch::
    
    set trash="imaps://imap.gmail.com/[Gmail]/Trash"

Googe Contacts
--------------
Use goobook for it::
    yum install python-pip
    pip install goobook
    goobook config-template >> .goobookrc

    [DEFAULT]
    email: michal.nezerka@gmail.com
    password: blueboyonthehill76

Modify .muttrc::

    set query_command="goobook query '%s'"
    macro index,pager a "<pipe-message>goobook add<return>" "add sender to google contacts"
    bind editor <Tab> complete-query

Sending msmtp
-------------
::
    ~/.msmtprc
    account default
    host smtp.gmail.com
    port 587
    from "michal.nezerka@gmail.com"
    tls on
    tls_starttls on
    tls_trust_file /etc/ssl/certs/ca-bundle.crt
    auth on
    user "michal.nezerka"
    password "blueboyonthehill76"
    logfile ~/.msmtp.log

Do ~/.muttrc::

    set sendmail="/usr/bin/msmtp"

test::
    
    echo “Ahoj” | msmtp “email”

Group addresses
---------------
Create a file with the following content::

    alias my_alias1 recipient1@email, recipient1@email alias my_alias2 recipient3@email, recipient4@email
    
Source it from your mutt config with source path/to/alias_file.

Mailing on Linux
================

Postfix on Fedora
-----------------

Disable TLS::

    /etc/postfix/main.cf
    smtp_tls_security_level=none
    smtpd_tls_security_level=none
    mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 172.17.0.0/16 (this is docker subnetwork)

Restart Postfix::

    sudo /etc/init.d/postfix restart

Check status::

    journalctl - and scroll to the bottom
