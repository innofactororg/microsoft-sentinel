# Microsoft Sentinel and Microsoft Defender XDR

- [Branch: master](#branch-master)
  - [Branch protection for master](#branch-protection-for-master)
- [Branch: approved](#branch-approved)
  - [Branch protection for approved](#branch-protection-for-approved)

## Branch: master

This fork of the [Azure-Sentinel](https://github.com/Azure/Azure-Sentinel) repository exist for the following reasons:

- Allow us to contribute changes and new content to the community.
- Approve content for use by the
  [Innofactor MDR Service](https://github.com/innofactororg/innofactor-mdr).

Only the `master` branch has been forked. No changes will be made by us to this branch.

### Branch protection for master

The `default` branch is protected by the following rules:

- **Bypass list**:
  - Repository admin (Role)
- **Restrict deletions**
- **Require linear history**
- **Require a pull request before merging**:
  - Required approvals: 1
  - Dismiss stale pull request approvals when new commits are pushed
  - Require approval of the most recent reviewable push
  - Require conversation resolution before merging
- **Require status checks to pass**
- **Block force pushes**

## Branch: approved

This branch exist to store approved content files.

To keep the size as small as possible, the `approved` branch was created as orphan using the following commands:

```bash
git clone --filter=tree:0 --no-checkout https://github.com/innofactororg/microsoft-sentinel.git
cd microsoft-sentinel
git switch --orphan approved
git commit --allow-empty -m "Initial commit on orphan branch"
git push origin approved
git push --set-upstream origin approved
```

### Branch protection for approved

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
