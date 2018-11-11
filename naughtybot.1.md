# naughtybot(1)

## SYNOPSIS

    naughtybot [help]
    naughtybot setup
    naughtybot mail-check
    naughtybot mail-mark-all-as-read
    echo MESSAGE | naughtybot queue
    echo MESSAGE | naughtybot send
    naughtybot flush
    naughtybot auto-flush
    naughtybot auto-check

    ---------------------------------------------
    naughtybot-state.json
    naughtybot-secret.json

## DETAILS

send = queue + flush
queue: Put message from stdin into sending queue.
flush: Send queued message to telegram. This is blocking operation.
setup: Edit or create naughtybot-secret.json.
mail-check: Check new mails, format properly, and put into send queue.
mail-mark-all-as-read: On your first run, mark all existing mails as read. Otherwise, all your old mails will be send.
auto-flush: Start a systemd transient user unit to monitor changes to the queue. Flushing will happen automatically when the queue is modified.
auto-check: Start a systemd transient user unit to check mail every 10 seconds.

## FILES

naughtybot-secret.json

    {
        "bot": {
            "token": <BOT-TOKEN>,
            "chat": <CHAT-ID>
        },
        "mail-pop3s": {
            "server": <POP3-SSL-server>,
            "port": <POP3-SSL-port>,    // optional. default to 995
            "insecure": false,          // optional. default to false. When true, add `-k` to curl (do not validate SSL certificate)
            "username": <username>,
            "password": <password>
        }
    }

