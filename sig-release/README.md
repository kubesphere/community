# Release Special Interest Group

The release SIG is to ensure quality KubeSphere releases, and coordinate different feature SIG to choose proper features/fixes in each release plan and make it deliver as planned.

## Roadmap and Releases

KubeSphere versioning is in such a way that x.y.z where x represents the major edition providing big feature components such as multi-cluster management in 3.0.0, y represents the minor version of the x edition with new features for existing components, and z is the fixpack with bugfix only added in. You can reference the [notes](./release) of each release so far.

## Scope

- Production of KubeSphere releases on a reliable schedule
- Ensure there is a consistent group of community members in place to support the release process across time
- Provide guidance and tooling to facilitate the production of automated releases
- Serve as a tightly integrated partner with other SIGs to empower SIGs to integrate their repositories into the release process

### In scope

- Ensuring quality KubeSphere releases
  - Coordinating, Defining and staffing release roles to manage the resolution of release blocking criteria
  - Coordinating, Defining and driving development processes (e.g. merge queues, cherrypicks) and release processes
  - Coordinating and working with each component group,  managing the creation of release specific artifacts, including:
    - Code branches
    - Binary artifacts
    - Release notes
- Continually improving release and development processes
  - Working closely with SIG Contributor Experience to define and build tools to facilitate release process (e.g. ks-console)
  - Working closely with SIG Testing to determine and implement tests, automation, and labeling required for stable releases
  - Working with downstream communities responsible for packaging KubeSphere releases
  - Working with other SIGs to agree upon the responsibilities of their SIG with respect to the release
  - Defining and collecting metrics related to the release in order to measure progress over each release
  - Facilitating release retrospectives

### Out of scope

#### Support

SIG Release itself is not responsible for end user support or creation of patches for support streams. There are support forums for end users to ask questions and report bugs, subject matter experts in other SIGs triage and address issues and when necessary mark bug fixes for inclusion in a patch release.

## Members

- [@calvinyv](https://github.com/calvinyv), Lead
- [@rayzhou2017](https://github.com/rayzhou2017), Lead
- [@liuyp2018](https://github.com/liuyp2018), Member

## Meetings

[Meeting notes](https://docs.google.com/document/d/1IzkvpZlkc_4hKTyvWWyTfLgPFTWGaowOEAfh0li9qZQ/)

## Contact

- Slack [#sig-release](https://kubesphere.slack.com/messages/sig-release)
- [Mailing list](https://groups.google.com/forum/#!forum/kubesphere)
- [Open Community Issues/PRs](https://github.com/kubesphere/community/sig%2Frelease)