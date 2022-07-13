# Gopa

Gopa (Good Old Preupgrade Assistant) is a fork of the [Preupgrade Assistant](https://github.com/upgrades-migrations/preupgrade-assistant) (PA) framework originally developed for [Red Hat Upgrade Tool](https://github.com/upgrades-migrations/redhat-upgrade-tool) (RUT) in-place upgrades to Red Hat Enterprise Linux 7 (RHEL7). Gopa is actually more of a reincarnation than a fork as the original PA and RUT source repos are now archived with a "Disclaimer: It was fun. R.I.P. :-)" note attached.

PA and RUT are replaced with [Leapp](https://leapp.readthedocs.io/en/latest/) for doing in-place upgrades to RHEL8 and later, so why do we need Gopa now? The answer lies in one of the PA frameworks's best features: its support for dropping in custom modules. Many RHEL users developed custom modules for their RHEL6 to RHEL7 in-place upgrade projects. With Gopa, they can reuse that work as they move on to RHEL8 and RHEL9. Some RHEL users also developed custom reporting that would aggregate the PA results to tools like ELK or Splunk. Gopa can be used to wrap the results from a Leapp preupgrade so those reporting integrations still work as is.

## Todo

Right, this isn't much more than just an idea yet. Time to get to work!
