## Scope
Production nest servers

### Increase swap files from 4 GB to 8GB.
We have found that our swapfile sizes are too low and can lead to extreneous alerts.

#### Assumptions
There is sufficient headroom on the systems to avoid `swapoff failed: Cannot allocate memory`, when disabling swap in order to modify it.

#### Stakeholders
Team-engineering slack channel members.

#### Procedure
The proceedure to increase the amout of available swap is as follows:

On all servers:
1. Create the new swapfile: `sudo dd if=/dev/zero of=/swapfile bs=1M count=8192`
2. Disable swap with: `swapoff -a`
3. Set the new swapfile as swap: `mkswap /swapfile`
4. re-enable swap: `swapon /swapfile`

#### Testing
Testing was performed on `nest0-server-a` and `nest0-server-b`

#### Rollback Notes
To roll back the change repeat the process and in the `dd` stage set the count to the original size (4096 for 4GB swap, etc).
