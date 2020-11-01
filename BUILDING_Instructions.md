# Building Instructions for Maintainers

We use [CircleCI](https://circleci.com/) for on-demand testing and releasing recoveries. It uses our Customized Docker Image to handle the Build Environment.
Any Maintainer who have access to the _GREEN Repositories_ inside this organization as-well-as Developers can use our Free Plan to build the Official Releases. You might just need to follow proper commit convention to start things up.

The CI system works with a _config_ which controls the build.

The [Sample CI Config](https://github.com/PitchBlackRecoveryProject/vendor_pb/blob/pb/__sample.circleci.yml) has pointed out almost everything that you need to configure according to your device. But mind the _Pushing Conventions_ as tests should be done only on non-master branches.

> NOTE: It is a better approach to build using CircleCI on your personal account first. Then push changes onto the repository in the organization.

## How To Use CircleCI For Individual Developers

You have to have an user account in __CircleCI__. Then add the CI Config as the `.circleci/config.yml` file in the repo.
```yaml
version: 2.1

executors:
  worker:
    docker:
      - image: fr3akyphantom/droid-builder:latest
        auth:
          username: "$DOCKERHUB_USERNAME"
          password: "$DOCKERHUB_PASSWORD"

jobs:
  build:
    executor: worker
    environment:
      # The below variables are Required. Build will not start if any of them are unset or absent
      MANIFEST_BRANCH: "" # REQUIRED:: Put as 'android-X.Y' format as-in "manifest_pb" repository
      VENDOR: "" # REQUIRED:: Input Product Vendor or Manufacturer
      CODENAME: "" # REQUIRED:: Input Device Codename
      FLAVOR: "" # REQUIRED:: Input eng or userdebug. BUILD_LUNCH variable is DEPRICATED and Could be Removed In The Future.
      # This variable is Optional
      PBRP_BRANCH: "" # OPTIONAL:: If not default 'android-9.0', define other bootable_recovery branch
      # This might depend on the bootable branch. Keep an eye on the Version Info
      VERSION: '3.0.0' # as of now, the current PBRP version. THIS WILL BE DEPRICATED IN THE FUTURE.
      # Only for Organisation users/Maintainers. THIS WILL BE DEPRICATED IN THE FUTURE.
      MAINTAINER: '@########' # REQUIRED:: Replace your Telegram ID, if unavailable then use GitHub Username
      # Choose only one of the 3 variables. Only for Organisation users/Maintainers.
      TEST_BUILD: "true"   # For Dev/Test Builds Only
      BETA_BUILD: "true"   # For Beta Release Builds Only
      PB_OFFICIAL: "true"  # For Official Organisation Builds
      # Want to extend the build script? Wanna add some command just before lunch? Use any command inside this -
      EXTRA_CMD: "" # OPTIONAL:: Whatever commands you wanna run inside working directory
      # Wanna truncate all other languages except English? Use this -
      PB_ENGLISH: 'true' # OPTIONAL:: If you want only English Language. This Could be Removed In The Future.
      # Want to add some fancy/informative Changelog while publishing Official Build? Use 2-space formatting instead of tabs, please.
      CHANGELOG: |
        What's been done?
        - Update done for xx
        What's fixed?
        - Fixed yy things
          - Which is actually Changed by ZZ
        And something else
    working_directory: /home/builder/pitchblack

    steps:
      - run:
          name: AIO Build
          command: |
            wget -q https://raw.githubusercontent.com/PitchBlackRecoveryProject/vendor_utils/pb/build.sh
            source build.sh

workflows:
  version: 2
  build_and_test:
    jobs:
      - build:
          filters:
            branches:
              only: "REPLACE CURRENT BRANCH NAME WITHIN QUOTE"
          context: org-global ## ONLY FOR TEAM DEVELPERS
          ## If you are not in Team, then you have to add $GitHubMail, $GitHubName and $GITHUB_TOKEN in the environment variables
          ## You also need to signup on dockerhub and use $DOCKERHUB_USERNAME and $DOCKERHUB_PASSWORD in the environment variables
```

#### If you wanna build with Android 10 source code

Replace these parts of lines with the new ones to build with Android Q sources.

BEWARE: This process is too slow. It will consume around 2 hours of your precious time for one recovery build.
> Don't blame me. The Remote Docker has only 2x1 CPU Threads, but gives 8GB RAM & 100GB SSD Space to use.

```diff
---    working_directory: /home/builder/pitchblack
+++    working_directory: /home/builder
---
---    steps:
---      - run:
---          name: AIO Build
---          command: |
---            wget -q https://raw.githubusercontent.com/PitchBlackRecoveryProject/vendor_utils/pb/build.sh
---            source build.sh
+++    steps:
+++      - setup_remote_docker:
+++          version: 19.03.13
+++      - run:
+++          name: "ALL IN REMOTE"
+++          command: |
+++            curl -sL https://raw.githubusercontent.com/PitchBlackRecoveryProject/vendor_utils/pb/remote_build.sh -o build.sh
+++            source build.sh
```

Don't forget to remove all our comments from inside the config.

Now, just add the repo in CircleCI to build.

Happy Building :smirk:

