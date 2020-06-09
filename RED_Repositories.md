# RED Repositories

RED Repositories are the collection of critical and important repositories that are present in this organization.

Some examples of RED repositories include :

- [android_bootable_recovery](https://github.com/PitchBlackRecoveryProject/android_bootable_recovery)
- [vendor_pb](https://github.com/PitchBlackRecoveryProject/vendor_pb)
- [manifest_pb](https://github.com/PitchBlackRecoveryProject/manifest_pb)
- [android_build](https://github.com/PitchBlackRecoveryProject/android_build)


## Branch Naming Conventions for RED Repositories

_Almost_ all repositories should be named by their android versions. For example: `android-10.0`. Every android version must be regularly maintained and updated. Along with the mainstream branches, it is mandatory to create a developemnt branch with the postfix of `-dev`. For example: `android-10.0-dev`.

## Pushing Conventions for RED Repositories

Commits will never be pushed directly to their mainstream branches instead a Pull Request should merge the commits under the review of atleast one Core Developer. Make sure PR's description, label is defined correctly. PBRP CI will be used in case of any testing required. Once the commits is flagged green, then only it will be merged to mainstream branches.

> NOTE: Only Core Developers have the authority to merge the Pull Request.




