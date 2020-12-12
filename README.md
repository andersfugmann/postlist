# Simple postfix mail list

After trying to keep mailman running,
and to setup sympia, I created this little script.

Its a very simple script, which will create a simple
dmarc complient mailing list.

## Installation

To install run;
```
$ make install
```
Now edit /etc/postlist.conf
each section defines a mailing list,
and must contain:

```
[<list address without domain>]
description = Some description
subscribers = fully qualified addresses of all list subscribers
```

After editing, run
```
$ sudo postlist setup
```
to complete the setup. Every time you make changes to the
configuration, it its adviced to repeat this step.

### Postfix integration

in `/etc/postfix/main.cf` append `hash:/etc/postfix/postlist` (or
whereever you configured the postlist file to be generated)

E.g.:
```
alias_database = hash:/etc/aliases, hash:/etc/postfix/postlist
```

Then load postfix: `postfix reload`

## Archives
All received mails are stored in `<archive_dir>/<list name>/archive`.
There is no webui to read these yet.
