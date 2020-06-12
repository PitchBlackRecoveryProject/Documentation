# GREEN Repositories

GREEN Repositories are the collection of Device Tree repositories that are present in this organization.

## All Device Tree Repositories must follow the following order

`android_device_<vendor/OEM>_<codename>-pbrp`

See example :
### android_device_xiaomi_rolex-pbrp


## Branch Naming Conventions for GREEN Repositories

_Almost_ all repositories should be named by their android versions. For example: `android-10.0`. Every android version must be regularly maintained and updated. Along with the mainstream branches, it is mandatory to create a developemnt branch with the postfix of `-dev` or `-testing` as this must for the current working branch. For example: `android-10.0-dev`.

## Pushing Conventions for GREEN Repositories

Commits should never be pushed directly to their mainstream branches without testing. First Maintainer must test there changes using `dev` or `test` branches.
Use proper commit messages even on the testing branches. If you have done some mistake on the last commit, try to `git commit --amend` & fix changes & `git push --force`. You can do it either from PC of from Android via Termux. This is a good approach. But if you can't, do the normal way. But make sure to test the commits & their changes along with their messages before pushing.

Once the commits are flagged green by Core Developers, then push changes to the main branch. If there are more than one commit, _Squash & Merge_ the Changes into one commit by using Pull Request from the test branch onto HEAD branch. Then push the squashed single commit with a meaningful commit message to the main branch.

Every pushed commit for _Official Build_ must have a valid and informative _Changelog_. The Changelog must be provided as the `CHANGELOG` part in the config.yml. That will be displayed in the Release Post on the Channel.

> NOTE: Device specific maintainers or core devs can made changes in their repos.




