# GREEN Repositories

GREEN Repositories are the collection of Device Tree repositories that are present in this organization.

## All Device Tree Repositories must follow the following order

`android_device_<vendor/OEM>_<codename>-pbrp`

See example :
### android_device_xiaomi_rolex-pbrp


## Branch Naming Conventions for GREEN Repositories

_Almost_ all repositories should be named by their android versions. For example: `android-10.0`. Every android version must be regularly maintained and updated. Along with the mainstream branches, it is mandatory to create a developemnt branch with the postfix of `-dev` or `testing` as this must for the current working branch. For example: `android-10.0-dev`.

## Pushing Conventions for GREEN Repositories

Commits will never be pushed directly to their mainstream branches without testing. First Maintainer must test there changes using `dev` or `test` branches. Make sure the commits should be tested before pushing. Once the commits is flagged green, then push them to main branch, + `CHANGELOG` in the config.yml, that will continue to official release.

> NOTE: Device specific maintainers or core devs can made changes in their repos.




