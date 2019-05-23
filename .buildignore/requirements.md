requirements
================

    From: Lao, Suzanne
    Sent: Tuesday, April 30, 2019 2:47 PM
    To: Lepore, Mauro <LeporeM@si.edu>; Shameema Jafferjee Esufali (shameemaesufali@gmail.com)
    <shameemaesufali@gmail.com>
    Cc: Krizel, Lauren <KrizelL@si.edu>
    Subject: RE: Building R stem tables for the upcomming workshop

> When making the R stem tables, please note the following comments when
> determining the status variable.

1.  DFstatus is exactly the same as the status variable in
    ViewFullTable.

2.  The status variable in the R tables is calculated as follows for
    stems:

| status\_in\_viewfulltable | status\_after\_rtbl |
| :------------------------ | :------------------ |
| alive                     | A                   |
| dead                      | D                   |
| broken below or stem dead | G                   |
| missing                   | M                   |

> Also, do the following:

3.  Give an Rstatus of P -“prior”, if a stem does not appear in the
    first censuses, i.e. stem is first measured in a later census.

Propagate `status == P` forward in all censuses until it first appears.

4.  Propagate the Rstatus D (dead) forward, even if the stem disappears
    in later censuses.

5.  G - “gone” - propagate forward (even if stem disappears in later
    censuses) until the stem is measured again in a later census.

6.  If a stem was dead in a census, then later found alive, go back and
    change all the Rstatus ‘D’ to ‘A’.

> Stems may go through the following Rstatuses and in this order:

`P (prior) -> A (alive) -> G (gone) -> D (dead)`

P, G, and/or D may be missing.

> Problems that have to be fixed in the Rstatus sequence:

7.  P should NEVER follow any of the other Rstatuses. It should be the
    first Rstatus, or not appear at all.

8.  P should not go directly to G or D, without first going to A.

9.  D should never be followed by A or G.

10. Stems should not start with a G, they should start with P or A.
    Somemes they start with a D when the site tags and measures dead
    stems

> The folder called “onecensus” contains the data from sites for which I
> have one census only. You may not need to make R tables for these
> sites, since the R tables that already exist should be fine. You may
> still want to make them to compare with those that are on the server.