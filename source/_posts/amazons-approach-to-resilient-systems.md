---
title: Amazons approach to resilient systems
cover_index: 2019/12/DAY/TITLE/index.jpg
tile_color: '#fea832'
date: 2019-12-03 09:34:16
tags:
---
{% asset_img banner.png "Description goes here" %}

# The cultural side
- Everyone has operational tasks
- Dont shoot the firefighter. This doesnt close the loop of improvements and makes being honest harder.
- Management and 'architects' have to get out of the office and interact with the developing and operating people.

# The technical side
- Retries
- Exponential backoff
- Introduce jitter. When everything does something at round timestamps, like midnight, the system is under high load at peaks and idles between peaks. Try to keep a steady load by introducing random delays before executing something.

## The loop of improvements
- It's about fixing failures before they occur. Keep the loop small.