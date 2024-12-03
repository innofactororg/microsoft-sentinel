# Microsoft Sentinel and Microsoft Defender XDR

- [About Repository](#about-repository)
- [Repository Settings](#repository-settings)
  - [Default Branch Protection](#default-branch-protection)
  - [Tag Protection](#tag-protection)
- [Approved Branch](#approved-branch)
- [Approved Branch Protection](#approved-branch-protection)

## About Repository

This repository is a fork of the [Azure-Sentinel](https://github.com/Azure/Azure-Sentinel)
repository. It exist for the following reasons:

- Allow us to contribute changes and new content to the community.
- Approve content for use by the
  [Innofactor MDR Service](https://github.com/innofactororg/innofactor-mdr).

Only the `master` branch has been forked.

## Repository Settings

This repository allow squash merging with the default commit message set to the
pull request title and description.

### Default Branch Protection

The `default` branch is protected by the following rules:

- **Bypass list**:
  - Repository admin (Role)
  - MDR Sentinel Write (App)
- **Restrict deletions**
- **Require linear history**
- **Require a pull request before merging**:
  - Required approvals: 2
  - Dismiss stale pull request approvals when new commits are pushed
  - Require approval of the most recent reviewable push
  - Require conversation resolution before merging
- **Require status checks to pass**
- **Block force pushes**
- Restrictions:
  - Restrict commit metadata:
    - **Conventional commits** must match a given regex pattern:

      ```text
      ^(build|chore|ci|docs|feat|fix|perf|refactor|revert|style|test)
      {1}(\([\w\-\.]+\))?(!)?: ([\w ])+([\s\S]*)
      ```

  - Restrict branch names:
    - **Windows compatible branch names** must match a given regex pattern:

      ```text
      \A[0-9a-z-_]$
      ```

### Tag Protection

All tags are protected by the following rules:

- **Bypass list**:
  - Repository admin (Role)
- **Restrict deletions**
- **Require linear history**
- **Block force pushes**
- Restrictions:
  - Restrict tag names:
    - **Semantic versioning** must match a given regex pattern:

      ```text
      ^v(([1-9]\d*)|(0|[1-9]\d*)\.(0|[1-9]\d*)\.(0|[1-9]\d*)(?:-((?:0|[1-9]\d*|
      \d*[a-zA-Z-][0-9a-zA-Z-]*)(?:\.(?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*))
      *))?(?:\+([0-9a-zA-Z-]+(?:\.[0-9a-zA-Z-]+)*))?)$
      ```

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
git commit --allow-empty --message "chore: initial commit on orphan branch"
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
  - Required approvals: 2
  - Dismiss stale pull request approvals when new commits are pushed
  - Require approval of the most recent reviewable push
  - Require conversation resolution before merging
- **Require status checks to pass**
- **Block force pushes**
- Restrictions:
  - Restrict commit metadata:
    - **Conventional commits** must match a given regex pattern:

      ```text
      ^(build|chore|ci|docs|feat|fix|perf|refactor|revert|style|test)
      {1}(\([\w\-\.]+\))?(!)?: ([\w ])+([\s\S]*)
      ```

  - Restrict branch names:
    - **Windows compatible branch names** must match a given regex pattern:

      ```text
      \A[0-9a-z-_]$
      ```
