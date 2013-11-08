# Git Way

High-level wrappers for our lightweight and opinionated git workflow.

## Installation

    ./install

This will create `git feature` and `git fix` aliases in your `~/.gitconfig`.

## Usage

```
usage: git <command> <subcommand> [<identifier>]

<identifier> will try to match one of existing feature or fix branches. It is
assumed that they are prefixed with 'feature/' and 'fix/' respectively, but the
prefix must not be included in the <identifier>, it is inferred from <command>.

Numeric <identifier> matches in the following way: '40' will match feature/40-foo
but not feature/404.

Non-numeric <identifier> matches any portion of the branch name. E.g. 'foo' will
match feature/foo, feature/foobar and feature/40-foo.

If the current branch is a feature or fix branch you can omit the <identifier>.


Commands:
  feature     Makes subcommands work on feature branches.

  fix         Makes subcommands work on fix branches.


Subcommands:
  open        Switches to branch specified by <identifier>. It will be created
              if needed and automatically track respective remote branch if it
              exists.

  release     Merges branch specified by <identifier> into master branch and pushes
              to remote. Both local branch and its tracked remote branch will be
              deleted afterwards.

  stage       Merges branch specified by <identifier> into staging branch and
              pushes to remote.

  sync        Synchronizes local branch with its tracked remote branch, i.e.
              rebases local branch onto remote and pushes changes to remote.
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
