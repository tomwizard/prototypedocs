# DNS+ Vantage Point addition

During our maintenance update on May 14, 2014 we will be updating our validation rules for DNS+ Vantage Points, to remove a constraint which was unnecessarily causing a number of open resolvers used in DNS+ to be removed from the list.

**Please note that we expect this change to increase the number of vantage points available by 30-50%**

This will result in a large number of additional vantage points appearing - and being used by our DNS+ tests - during the hours following our maintenance.  New countries, new networks, and higher densities of vantage points inside each will become available.

This may affect global results somewhat, given the number of new caches being added to the list.  In most cases, the reference metrics will vary by similar margins as shown by your results.

If you have alerts configured for DNS+ tests which are not tied to the reference metrics, we strongly recommend a review of those alert rules.  As a reminder, availability alerts can be configured to be bound to both the Availability and Reference availability metrics, such that alerts are triggered only when availability of your target domain name drops by a certain percentage relative to the reference availability.

IMAGE MISSING

If you have any questions related to this change, [contact the ThousandEyes Customer Success team.](mailto:support@thousandeyes.com)

