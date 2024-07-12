# Ansible role abclinuxu_weekly

Ansible role for configuration and deployment of [abclinuxu.weekly].

## Requirements

This role does install some packages like `git` and `python3`.

## Role variables

See `defaults/main.yml`.

## Dependencies

There are no extra dependencies as far as Ansible goes. However, note that you
must setup cron jobs by yourself eg. use another Ansible role.

Example cron job setup with [ansible-cron]:


```yaml
---
cron_tasks:
  - name: abclinuxu-weekly-articles
    cron_file: abclinuxu-weekly-articles
    day: '*'
    hour: '23'
    job: "/opt/abclinuxu.weekly/venv/bin/python3 /opt/abclinuxu.weekly/src/abclinuxu_weekly.py -a --mail-from 'root@example.com' --mail-to 'user@example.com'"
    minute: '45'
    month: '*'
    state: present
    user: root
    weekday: 'sun'
  - name: abclinuxu-weekly-news
    cron_file: abclinuxu-weekly-news
    day: '*'
    hour: '23'
    job: "/opt/abclinuxu.weekly/venv/bin/python3 /opt/abclinuxu.weekly/src/abclinuxu_weekly.py -n --mail-from 'root@example.com' --mail-to 'user@example.com'"
    minute: '50'
    month: '*'
    state: present
    user: root
    weekday: 'sun'
```

## License

MIT

[abclinuxu.weekly]: https://github.com/zstyblik/abclinuxu.weekly
[ansible-cron]: https://github.com/weareinteractive/ansible-cron
