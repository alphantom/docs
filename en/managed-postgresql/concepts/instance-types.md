# Host classes

The host class defines the computing power and storage space that is allocated for each host in the cluster. When you change the host class for a cluster, characteristics of all existing hosts change, too.

The available storage does not depend on the host class.  For storage limitations, see the section [[!TITLE]](limits.md).

## Available host classes {#available-flavors}

Hosts in the cluster [!KEYREF mpg-name] are deployed on virtual machines in [!KEYREF compute-full-name]. These virtual machines can be created on any of the platforms that are supported by [!KEYREF compute-name]. Platforms are described in detail in the section [[!TITLE]](../../compute/concepts/vm-platforms.md).

The full list of possible host configurations on each of the platforms is provided below.

| Host class name | Number of CPUs | CPU performance | RAM, GB |
| ----- | ----- | ----- | ----- |
| **Intel Broadwell** |  |
| b1.nano | 2 | 5% | 2 |
| b1.micro | 2 | 20% | 2 |
| b1.medium | 2 | 50% | 4 |
| s1.nano | 1 | 100% | 4 |
| s1.micro | 2 | 100% | 8 |
| s1.small | 4 | 100% | 16 |
| s1.medium | 8 | 100% | 32 |
| s1.large | 16 | 100% | 64 |
| s1.xlarge | 32 | 100% | 128 |
| **Intel Cascade Lake** |  |  |
| b2.nano | 2 | 5% | 2 |
| b2.micro | 2 | 20% | 2 |
| b2.medium | 2 | 50% | 4 |
| s2.micro | 2 | 100% | 8 |
| s2.small | 4 | 100% | 16 |
| s2.medium | 8 | 100% | 32 |
| s2.large | 12 | 100% | 48 |
| s2.xlarge | 16 | 100% | 64 |
| s2.2xlarge | 24 | 100% | 96 |
| s2.3xlarge | 32 | 100% | 128 |
| s2.4xlarge | 40 | 100% | 160 |
| s2.5xlarge | 48 | 100% | 192 |

