# Contribution

Thank you for your interest in contributing to our projects!

Feel free to dive in. Read the following sections to learn about our workflow and standards. Whether you're looking to write code, contribute to documentation, report bugs, or just ask questions, we appreciate all forms of contribution.

All members of our community are expected to follow our **[Code of Conduct](./CODE_OF_CONDUCT.md)**. In all our interactions, let's make sure to create a welcoming and friendly space for everyone.

We're really glad you're reading this! Volunteer developers can help us quickly reach our goals and make our projects come to fruition.

## Setup

### .gitmessage

We recommend that every repository provides a `.gitmessage`.
Once you create this `.gitmessage`, please add it into your `.git/config` with the following command:

```shell
> git config commit.template /path/to/.gitmessage
```

## General Workflow

Follow this workflow when working on our repositories:

1. Select or create an issue.
   - Note: If the "issue" is straightforward, you do not need to create a new issue.
2. Create a new branch for this issue.
3. On the new branch, make your changes to solve the issue.
   - If you work on the code...
     1. Use the [Google Style Guides](http://google.github.io/styleguide/) to standardize your code.
     2. Test your code against...
        - A formatting tool
        - A lint tool
        - Unittests
4. Commit your changes following our rules below.
5. Open a pull request for all your commits.
6. Request and wait for reviews on your pull request.
7. Fix any problems from comments or reviews received.

The last reviewer will merge and close the PR once an `Approve` review is given by every other reviewer and the CI has finished running.

## Issues

The best way to contribute to our projects is by opening a new issue or tackling one of the existing issues.

## Branch Names

Branch names must only consist of `[a-z|0-9|-|/]` characters and be in the form `<type>/<subject>`.

- `<type>` : One of the defined [Commit Types](#commit-type) we use.
- `<subject>` : Starts with an imperative verb. Explains the goal of this branch.

An example of a viable branch name is `feat/implement-xyz`.

## Commit Messages

We follow the standards of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/), but have adapted some of the conventions to better fit our needs. Differences and more detailed explanations of some rules are included below.

### Commit Type

The commit type must be one of the following:

- **build**: Changes that affect the build system or external dependencies.
- **chore**: Changes that fix typos (Does not change the production code).
- **ci**: Changes to our CI configuration files and scripts.
- **docs**: Documentation only changes.
- **feat**: A feature addition or removal.
- **fix**: A bug fix (Note that fixing a typo must instead be labelled as `chore`).
- **perf**: A code change that improves performance.
- **refac**: A code change that improves readability or code structure.
  This change could increase performance, but should not be labelled as the `perf` type if performance improvement is not the goal.
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
  Other examples include sorting build targets or headers.
- **test**: Adding missing tests or correcting existing tests.

**NOTE:** Some repositories only need to use one type of commit, such as `.github` with `docs` commits. In these cases, the commit type may be omitted from commit messages and branch names.

### Commit Scope

In general, include the scope of the commit in the commit header (e.g. feat(zk)...).
You may omit the scope when:

- The change affects more than one scope (e.g. feat: add Colosseum contract).
- The commit type is `docs` (e.g. docs: update contracts/README.md.).

### Additional Rules

- The commit subject should always start with an imperative verb.
- Both the commit header and body should not exceed 80 characters.

## Testing Changes

## For Go developers

Please make sure your changes pass the command below.

```shell
> go test ./...
```

## For NodeJS developers

We use [yarn](https://yarnpkg.com/) as a package manager tool. Please make sure your changes pass the commands below.

```shell
> yarn lint
> yarn test
```

## For C++ developers

We use **[cpplint](https://github.com/cpplint/cpplint)** and **[clang-format](https://clang.llvm.org/docs/ClangFormat.html)** to keep our code clean and readable. If you want to make sure your code passes our checks and follows our rules, follow the guide below.

### Formatter: [clang-format](https://clang.llvm.org/docs/ClangFormat.html) (version 17)

Please install clang-format (version 17) and run it before committing your changes.
Ensure you use version 17 to prevent conflicts.

**For MacOS** (see [install guide](https://formulae.brew.sh/formula/clang-format)):

```shell
> brew install clang-format@17
```

**For Ubuntu** - Version 14 is the default version for Ubuntu, so you will need to upgrade to version 17:

```shell
> wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key | sudo apt-key add -
> sudo add-apt-repository "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-17 main"
> sudo apt update
> sudo apt install clang-format clang-format-17
> sudo update-alternatives --install /usr/bin/clang-format clang-format /usr/bin/clang-format-17 100 --slave /usr/share/man/man1/clang-format.1.gz clang-format.1.gz /usr/share/man/man1/clang-format-17.1.gz
[sudo] password for <user>:
update-alternatives: using /usr/bin/clang-format-17 to provide /usr/bin/clang-format (clang-format) in auto mode
> sudo update-alternatives --install /usr/bin/clang-format clang-format /usr/bin/clang-format-14 20 --slave /usr/share/man/man1/clang-format.1.gz clang-format.1.gz /usr/share/man/man1/clang-format-14.1.gz
> sudo update-alternatives --config clang-format
```

**Using pip**:

1. Download the [source code](https://github.com/ssciwr/clang-format-wheel/releases/tag/v17.0.4).
2. Unzip the source code.
3. Run the following commands.

```shell
> cd path/to/source/code/clang-format-wheel-17.0.4
> pip install .
```

**Run clang-format:**

```shell
> git diff --name-only HEAD origin/<branch-name-to-be-merged> | grep '\.\(cc\|h\)$' | xargs clang-format -style=file -i
```

### Linter: [cpplint](https://github.com/cpplint/cpplint)

Cpplint is a tool for checking C++ code against Google's style guide. We've configured it to ignore certain warnings (`legal/copyright`, `whitespace/line_length`, `build/namespaces`, `runtime/references`) for our project.

Before committing, ensure your changes pass the cpplint checks.

**Install cpplint:**

```shell
> pip install cpplint
```

**Run cpplint:**

```shell
> git diff --name-only HEAD origin/<branch-name-to-be-merged> | xargs cpplint --filter=-legal/copyright,-whitespace/line_length,-build/namespaces,-runtime/references
```

### [Buildifier](https://github.com/bazelbuild/buildtools/blob/master/buildifier/README.md)

Buildifier is a tool for formatting bazel `.bazel` and `.bzl` files with a standard convention.

Ensure you use version 6.4.0 to prevent conflicts. Check the appropriate release for your local environment [here](https://github.com/bazelbuild/buildtools/releases/tag/v6.4.0).

**For MacOS:**

```shell
> curl -lo https://github.com/bazelbuild/buildtools/releases/download/v6.4.0/buildifier-darwin-amd64
> chmod +x buildifier-darwin-amd64
> sudo mv buildifier-darwin-amd64 /usr/local/bin/buildifier
```

**For Ubuntu:**

```shell
> wget https://github.com/bazelbuild/buildtools/releases/download/v6.4.0/buildifier-linux-amd64
> chmod +x buildifier-linux-amd64
> sudo mv buildifier-linux-amd64 /usr/local/bin/buildifier
```

**Run Buildifier:**

```shell
> find tachyon/ -iname "*.bazel" -o -iname "*.bzl" | xargs buildifier --lint=fix
> find tachyon/ -iname "*.bazel" -o -iname "*.bzl" | xargs buildifier --mode=check
```

## Pull Requests

### Before opening a PR

Before opening a pull request for all your commits, we request that you run a final self-check to reduce the amount of potentially trivial errors.
Please ensure these rules are met:

- No typos in the header and body of your commits.
- The changes in each commit do not encompass more than one type of commit. (e.g. A commit that includes `style` and `test` changes should be separated into two different commits)
- The subject of each commit accurately explains the changes made.
- Your PR does not contain any intermediate changes (e.g. An error is made in one commit and rectified in the next commit) among commits.

### Reviews

Reviews should be an interactive experience between the PR author and the reviewers. Unless, the review type is `Approve`, the PR author and the reviewers should acknowledge and work together on the reviews.

Reviews should follow the following process:

1. A reviewer leaves a `Comment` or a `Request Changes` review.
2. The PR author acknowledges the review and/or asks follow-up questions.
3. Once the PR author has all the information they need, they resolve the problem with new changes.
4. The PR author re-requests the reviewer to check their new changes.
5. Based on the reviewer's response, the process starts again or finishes.
   1. Start again - More review is needed and the reviewer submits another `Comment` or `Request Changes` review.
   2. Finish - All new changes are good and reviewer resolves their review.

Note: Comments and reviews may only be resolved by their authors!

Once a reviewer is satisfied with the commits, they will leave an `Approve` review with a comment such as "LGTM."

## Useful Tips

### Before Committing

Before any commits, we recommend to rebase your local repository to prevent any conflicts.

```shell
> git fetch origin -p
> git rebase origin/dev
```

### How to check your changes

Use the following `git` commands to check your changes by category.
You can check your overall status with `git status`.

- Changes not staged for a commit: check with `git diff`.
- Changes to be committed: check with `git diff --cached`.
- Committed changes: check with `git log -p`.

## Other

### CI (Github Actions)

We use GitHub Actions to verify that the code in your PR passes all our checks.

When you submit or update your PR, a CI build will automatically start. A note will be added to the PR that will indicate the current status of the build.
