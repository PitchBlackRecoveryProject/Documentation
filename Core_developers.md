# Core Developers - PBRP

Core Developers are the backbone of PBRP and making a better environment for them is very important.

## Roles

- Developers have the full control over every repository inside the organizaion but critical actions should always be reviewed by atleast 1 fellow core developers.
- Core Developers will directly manage device maintainers and collaborators by giving inputs regarding any updates/bugs/features.
- Communication plays a vital role for a Core Developer as he has to share every information to their fellow developers so that everyone is well aware what's going on and how to manage maintainers down the line.

## Guidelines for creating a Repository
- Repository and branch naming conventions to be followed for RED and GREEN repositories.
- As soon as developers create a repository, it's mandatory to first add a README, Description, Tags and website (if possible).
- If it's a GREEN Repository, immediately assign a Collaborator that will take care behind you.

## Pushing Conventions for RED Repositories

- Every RED repository will have 2 working branches, one is the `PB-2.9.1` and the other is `PB-2.9.1-dev`.
- Commits should never be commited directly to `PB-2.9.1` instead the commits should always be merged by a pull request from `PB-2.9.1-dev`. Optinally, its suggested to assign one of the developer to review it before merging.
- After a pull request, a subversion tag should be added for easy identification.

## Pushing Conventions for GREEN Repositories

Developer can directly commit to GREEN repositories, without the intervention of the maintainer. But it's equally important to notify the maintainer as soon as you commit.
