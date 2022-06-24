# 000 - autorestart, log disable/enable

## Auto restart when crash

### Windows - batch

```batch
@echo off

::Start server
:Start 
C:\path\to\application.exe

:: Wait 1 second before restarting if crash
TIMEOUT /T 1
GOTO:Start
```

### Linux - systemd

example:

{% content-ref url="../../../linux/systemd/create-git-lan-server-service.md" %}
[create-git-lan-server-service.md](../../../linux/systemd/create-git-lan-server-service.md)
{% endcontent-ref %}

## Disable/Enable Logs

{% content-ref url="../../../dev/rust/basics/log.md" %}
[log.md](../../../dev/rust/basics/log.md)
{% endcontent-ref %}
