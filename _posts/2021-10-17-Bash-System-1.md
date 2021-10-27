---
title: "Bash System 1"
categories:
- writeUp
tags:
- security
- hacking
- root-me
- wargame
- system
- script
last_modified_at: 2021-10-20T01:50:00+09:00
---

## Bash-System

```
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
 
int main(void)
{
    setreuid(geteuid(), geteuid());
    system("ls /challenge/app-script/ch11/.passwd");
    return 0;
}
```
