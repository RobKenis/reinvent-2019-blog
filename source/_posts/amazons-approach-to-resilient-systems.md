---
title: Amazons approach to resilient systems
# cover_index: 2019/12/03/amazons-approach-to-resilient-systems/index.jpg
tile_color: '#bafc03'
date: 2019-12-02 22:29:16
tags:
---
{% asset_img banner.jpg "Venetian Theatre" %}

## The cultural side
<!-- - Everyone has operational tasks
- Dont shoot the firefighter. This doesnt close the loop of improvements and makes being honest harder.
- Management and 'architects' have to get out of the office and interact with the developing and operating people. -->
Achieving resilient systems and technical excellence is not all about the newest tools and fastest technology. It's also about the culture in the team and the broader organization. To start, everyone should participate in operational tasks, not just the *operations people*. By the way, don't shoot the firefighter and operations when something goes wrong. This doesn't close the loop of improvement and only makes it harder to be honest when talking about issues. The third important thing is that non-developing architects and management have to get out of their office and interact with developers that build and operate the systems.

## The technical side
<!-- - Retries
- Exponential backoff
- Introduce jitter. When everything does something at round timestamps, like midnight, the system is under high load at peaks and idles between peaks. Try to keep a steady load by introducing random delays before executing something. -->
Retries, retries, retries. Systems fail all the time, and consuming systems should be built to retry their actions when it happens. But make your retries a little smarter than just a while-loop. Use exponential backoff, give the failing system time to recover. To limit the chance of constantly bombarding the system with requests, followed by requests from the retries, introduce jitter. Add a random amount of time before executing an action. Don't just do this for retries, use this on more places in an application, crontab is a perfect example of consistent bombarding.

<!-- ## The loop of improvements -->
<!-- - It's about fixing failures before they occur. Keep the loop small. -->
