# Fix Errant Timezones

This simple pipeline provides to methods to fix bad timezones:

1) Using a CSV lookup file with `host` and `adj` columns. The `adj` column is expected to be in seconds. For example, 10800 would be a 3 hour adjustment. Any host that matches would have its time adjusted by the value in `adj`.

2) Using the difference between `now()` and the event time (aka `_time`), try to figure if the gap is very near to a timezone boundary. For example, if the difference between `now()` and `_time` is 3h00m07s, or 10807 seconds, we can probably assume the event has the wrong TZ and adjust by 10800 seconds to correct.

The pipeline can be used as is, in a Chain function from another pipeline, or as a pre-processing pipeline.

Enjoy, and feel free to submit PRs for bug fixes or improvements.

Jon
