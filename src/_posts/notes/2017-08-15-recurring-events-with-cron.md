---
title: "Recurring execution of a script with cron"
excerpt: "Sending out a report of a scripts execution on pre-defined events."
tags: [linux, macos, cron, til]
# last_modified_at: 2018-02-01T23:12:06+01:00
categories: [notes]
---

I found a reliable way to remind myself of a recurring event that happens every second month
at the first saturday of that month.

``` bash
30  3 1-7 1,3,5,7,9,11 Sat /Users/dominic/tom/bin/notify.sh
```

The script runs on month `1,3,5,7,9` and `11` if it's a saturday and between day `1-7`.

This works quite good---but today I use another configuration.

``` bash
30  3 * 1,3,5,7,9,11 6  /Users/dominic/tom/bin/notify.sh
```

This version runs on every Saturday (`6`) on month `1,3,5,7,9,11`; the script itself checks if it's
the first saturday or not.

That way I get a notification on every execution (every saturday in above mentioned months) and the
report shows me more details. The report also contains the information if the actual function got
executed or not---it's easier to tell, if the script still runs correctly or not.


``` bash
# get the actual day in numbers form
TODAY="`date +%_d`"

# check if its the first saturday (the first saturday must be one of day 1-7)
if [ $TODAY -gt "7" ]; then
  # that means, $TODAY is greater than 7. Send a negative report and quit the script.
  ACTION='NO'
  # set a variable or silently quit the program
  #return 0
else
  # execute the final action/function
  # set special variables etc.
  ACTION='YES'
fi
# you can now decide what to do. read content of $ACTION and execute the correct functions here
# depending on the valued of $ACTION that we have set in our if-clause above. Or just quite the
# script silently in the proper branch of that if-clause.
```

{% notice info %}
Hopefully this information was quite understandable. I'm not a good english writer and this article was
quite hard to write. I might not have found the correct words every time so please feel free to comment
and improve that content.
{% endnotice %}
