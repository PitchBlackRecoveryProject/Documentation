# Building Instructions for Maintainers

We use [CircleCI](https://circleci.com/) for on-demand testing and releasing recoveries. It uses our Customized Docker Image to handle the Build Environment.
Any Maintainer who have access to the _GREEN Repositories_ inside this organization as-well-as Developers can use our Free Plan to build the Official Releases. You might just need to follow proper commit convention to start things up.

The CI system works with a _config_ which controls the build.

The [Sample CI Config](https://github.com/PitchBlackRecoveryProject/vendor_pb/blob/pb/__sample.circleci.yml) has pointed out almost everything that you need to configure according to your device. But mind the _Pushing Conventions_ as tests should be done only on non-master branches.

> NOTE: It is a better approach to build using CircleCI on your personal account first. Then push changes onto the repository in the organization.
