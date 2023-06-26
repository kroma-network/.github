# Contribution

Contributions are always welcome! You can report issues or bugs, suggest features
or even implement and send pull request!

## Code of Conduct

Please read and follow our [Code of Conduct](./CODE_OF_CONDUCT.md)!

## Prerequisite

Each repository is recommended to provide a `.gitmessage`
If the repository contains `.gitmessage`, please add `.gitmessage` and follow the convention.

```shell
> git config commit.template /path/to/.gitmessage
```

## For go developers

Please make sure your changes pass below commands.

```shell
> go test ./...
```

## For nodeJS developers

We use [yarn](https://yarnpkg.com/) as a package manager tool. Please make sure your changes
pass below commands.

```shell
> yarn lint
> yarn test
```

## Coding style

We follow [google coding style](http://google.github.io/styleguide/).

## Steps to commit

1. Leave the issues. (If the issue is a straightforward one, it is indeed possible to skip this process.)
2. Create a new branch whose name starts with an imperative verb above like `feat/implement-xyz`.
   Branch name should consist of [a-z|0-9|-]. The prefix keyword should be one of followings defined [Commit type](#commit-type)
3. Make your changes.
4. Run a formatting tool if you make changes to codes.
5. Run a lint tool if you make changes to codes.
6. Run unittests if you make changes to codes.
7. Rebase your local repository.

  ```shell
  > git fetch origin -p
  > git rebase origin/dev
  ```

## What to check

Before Pull Request, you have to check followings first.

- Whether there is typo in the subject and body of your commit.
- Whether the subject of your commit explains well about your changes.
- Whether your commits are well split in semantics.
- Whether your PR contains any intermediate changes among commits.

## How to check your changes

You can check above with `git` commands. just follow this guideline. you meet one of situations below.
You can check your status by `git status`.

- Changes not staged for commit: check with `git diff`.
- Changes to be committed: check with `git diff --cached`.
- Committed: check with `git log -p`.

## Commit Message Format

We follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

### Commit Type

Must be one of the following:

- **build**: Changes that affect the build system or external dependencies.
- **chore**: Fixes typo; no production code change.
- **ci**: Changes to our CI configuration files and scripts.
- **docs**: Documentation only changes.
- **feat**: A feature addition or removal.
- **fix**: A bug fix. Just a fixing typo must be typed as a `chore`.
- **perf**: A code change that improves performance.
- **refac**: A code change that improves readability or code structure.
  This may incur internal features. Also, this may increase performance, but it's different
  from `perf` type in that performance improvement is not the goal.
- **test**: Adding missing tests or correcting existing tests.

**NOTE:** Some repositories such as `.github` itself only contain documents. So it may be
redundant to add commit type. In this case, the commit type may be omitted and branching
rule is also loosened, too.

### Commit Scope

Exceptionally, commit type `docs` may omit scope. e.g, docs: update contracts/README.md.
If the change affects more than one scope, the commit scope may be omitted.
e.g, feat: add Colosseum contract

## How to merge

If a PR author receives `Comment` from reviewers, not `Request changes`, it is recommended
to wait for the comment authors to confirm the changes that the PR author made after the review.
Therefore, once the PR author has reflected all the requested changes, please re-request
for the comment authors to review again so that they can review and `Approve` the changes.
The PR author should merge and close the PR after receiving `Approve` from all comment authors.
