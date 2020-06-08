## Scope

Bastillion aws instances named bastillion1.int.flyzipline.com bastillion2.int.flyzipline.com.

### Upgrade bastillion to release 3.10.00.

This release is required to fix the bug reported here: https://flyzipline.atlassian.net/browse/INF-154.

### Remove snap support from instance.
We do not need snapd and it creates an additional attack surface.

#### Assumptions
Subsequent vendor provided ami will be updated to 3.10.00 release of bastillion.

#### Stakeholders

Team-engineering slack channel members.

#### Procedure

Prior to window do the following. Bastillion2 is considered our non-production representative environment. 

* Update ansible to remove the custom patch that this patch supersedes.
* Disable db sync crontab.
* On bastillion2, shutdown the bastillion process and create a tarball backup of /opt/bastillion.
* Follow the vendor upgrade instructions detailed here: https://github.com/bastillion-io/Bastillion/releases/tag/v3.10.00
* Restart bastillion.

Disable the snapd service as documented here: http://landofnightandday.blogspot.com/2018/06/disable-snap-core-service-on-ubuntu-1804.html

#### Testing

Create a new test user on bastillion2. Ensure they are added to the default profile group.
Connect to a remote host using bastillion.
View the audit logs of that connection.

Assuming tests pass, do the following:

Notify stakeholders that maintenance on production bastillion will occur during the scheduled window.

#### Rollback Notes
Stop the bastillion service, move the upgraded release out of the way and extract the backup tarball. Restart the bastillion service.

