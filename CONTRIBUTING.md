# Contribution

Contributions are always welcome! You can report issues or bugs, suggest features
or even implement and send pull request!

## Code of Conduct

Please read and follow our [Code of Conduct](./CODE_OF_CONDUCT.md)!

## Prerequisite

Please add `.gitmessage`.

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

1. Leave the issues.
2. Create a new branch with the issue number above like `feat/implement-xyz`.
   Branch name should consist of [a-z|0-9|-]. The prefix keyword should be one of followings defined (Commit type)(#commit-type)
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
- **feat**: A new feature.
- **fix**: A bug fix.
- **perf**: A code change that improves performance.
- **refac**: A code change that improves readability or code structure.
- **test**: Adding missing tests or correcting existing tests.
