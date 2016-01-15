# Rationale

Github bills per repository.
[AWS CodeCommit][codecommit], on the other hand, charges per-user (mostly).

You can save money on your Github subscription by moving unused projects
to CodeCommit.

# About

The `migrate` script will move all unmerged branches in a repository
to AWS CodeCommit from Github.
It will also create a JSON file for the issues and pull requests open
on Github and check those files into the master branch of the project
in CodeCommit.

# Is it any good?

Yes.

It saves you money.

# Setup

Install the [AWS Command Line Tools][cli] and configure a user profile.
You should already be familiar with hosting code with CodeCommit,
and have your SSH key attached to your IAM user account and
have your .ssh/config settings in place.

The script assumes you are using [Two Factor Authentication][tfa].
You'll need the current code (one time password),
see `GH_OTP` below.
Otherwise, you can create your own OAuth token and pass it in as `GH_TOKEN`.

# Running

    export GH_USERNAME=todd
    export GH_PASSWORD=secret
    export GH_OTP=123456

    ./mirror xtoddx/github-codecommit-archive

# Cleanup

The script doesn't delete the repository from Github.
Take a moment and say your goodbyes.

# License

MIT. Contributions welcome.


[codecommit]: https://aws.amazon.com/codecommit/
[cli]: https://github.com/aws/aws-cli
[tfa]: https://help.github.com/articles/about-two-factor-authentication/
