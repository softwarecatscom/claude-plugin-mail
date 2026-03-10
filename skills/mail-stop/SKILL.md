---
name: stop
description: Stop the mail polling loop. Use when the user says "stop mail", "stop polling", "cancel mail loop", or wants to end the recurring mail check.
---

# Stop Mail Loop

Stop the recurring mail polling loop started by the mail:loop skill.

## Steps

1. List active cron jobs using CronList to find the mail polling job
   (look for jobs with "check mail" in the prompt).

2. Delete it with CronDelete using the job ID.

3. Confirm to the user that polling has stopped.
