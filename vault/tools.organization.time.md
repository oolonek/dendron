---
id: ec378025-0a54-4e50-b3c6-4def62b3a82a
title: Time
desc: ''
updated: 1609702316785
created: 1609702188544
---


Having a look at the My Time plugin because I wanted a time tracking solution and that this is currectly lacking from the excellent Todo+ plugin.

Created a snippet to directyl add current time 

```bash
    "now": {
        "prefix": "now",
        "scope": "markdown,yaml",
        "body": "- `$CURRENT_HOUR:$CURRENT_MINUTE` ",
        "description": "now in hour:min"
    }
```


- `20:00` Started work on machine A
- `20:29` // Went to have a piss
- `21:26` Started work on machine A
- `23:26` // Went to have a piss
- `23:45` Started work on machine B



| Time span          | Task                      |
| -----------------: | ------------------------- |
|          `01:00`   | Started work on machine A |
|          `00:15`   | Started work on machine B |
|        **`01:15`** | **Total**                 |

> _Last update 20:29_ / Lines [valid:3, comments:2, invalid:0]


| Time span          | Task                      |
| -----------------: | ------------------------- |
|          `01:00`   | Started work on machine A |
|          `00:15`   | Started work on machine B |
|          `02:30`   | Went to have a piss       |
|        **`03:45`** | **Total**                 |

> _Last update 20:28_ / Lines [valid:5, comments:0, invalid:0]
