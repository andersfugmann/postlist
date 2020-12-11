= Simple postfix mail list =

After trying to keep mailman running,
and to setup sympia, I created this little script.

Its a very simple script, which will create a simple
dmarc complient mailing list.

It integrates well with postfix.

To install run; `make install`
Now edit /etc/postlist.conf
each section defines a mailing list,
and must contain:

[list]
description = Some description
address = fully qualified address of the mailing list
subscribers = fully qualified addresses of all list subscribers

list will be the address of the list on the server.
After editing, run postlist setup as root to complete the setup.
