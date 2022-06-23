# 001 - autorestart, log disable/enable

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

## Disable/Enable Logs

{% content-ref url="../../../dev/rust/basics/log.md" %}
[log.md](../../../dev/rust/basics/log.md)
{% endcontent-ref %}
