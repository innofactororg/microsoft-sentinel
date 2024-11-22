# Microsoft Sentinel and Microsoft Defender XDR

- [About Repository](#about-repository)
- [Default Branch Protection](#default-branch-protection)
- [Approved Branch](#approved-branch)
- [Approved Branch Protection](#approved-branch-protection)

## About Repository

This repository is a fork of the [Azure-Sentinel](https://github.com/Azure/Azure-Sentinel)
repository. It exist for the following reasons:

- Allow us to contribute changes and new content to the community.
- Approve content for use by the
  [Innofactor MDR Service](https://github.com/innofactororg/innofactor-mdr).

Only the `master` branch has been forked.

## Default Branch Protection

The `default` branch is protected by the following rules:

- **Bypass list**:
  - Repository admin (Role)
  - MDR Sentinel Write (App)
- **Restrict deletions**
- **Require linear history**
- **Require a pull request before merging**:
  - Required approvals: 1
  - Dismiss stale pull request approvals when new commits are pushed
  - Require approval of the most recent reviewable push
  - Require conversation resolution before merging
- **Require status checks to pass**
- **Block force pushes**

## Approved Branch

The `approved` branch exist for the following reasons:

- No changes will be made by us to the `master` branch.
- Keep our approved content files separate from the `master` branch.
- Keep the size small for checkout in deployment workflows.

The `approved` branch was created as orphan using the following commands:

```bash
url='https://github.com/innofactororg/microsoft-sentinel.git'
git clone --filter=tree:0 --no-checkout $url
cd microsoft-sentinel
git switch --orphan approved
git commit --allow-empty -m "Initial commit on orphan branch"
git push origin approved
git push --set-upstream origin approved
```

## Approved Branch Protection

The `approved` branch is protected by the following rules:

- Bypass list:
  - Repository admin (Role)
  - MDR Sentinel Write (App)
- **Restrict creations**
- **Restrict updates**
- **Restrict deletions**
- **Require linear history**
- **Require a pull request before merging**:
  - Required approvals: 1
  - Dismiss stale pull request approvals when new commits are pushed
  - Require approval of the most recent reviewable push
  - Require conversation resolution before merging
- **Require status checks to pass**
- **Block force pushes**
