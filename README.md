# Heroku Accounts

Helps use multiple accounts on Heroku.

## Motivation

Forked from: https://github.com/ddollar/heroku-accounts

But the original author stopped maintaining it, because he started a Heroku competitor called Convox.

I'm also not promising to maintain this. But at least this has a README :)


## Installation

    $ heroku plugins:install git://github.com/freeauto/heroku-accounts.git

## Usage

To add accounts:

    $ heroku accounts:add personal
    Enter your Heroku credentials.
    Email: <your email>
    Password: ******

    Add the following to your ~/.ssh/config

    Host heroku.personal
      HostName heroku.com
      IdentityFile /PATH/TO/PRIVATE/KEY
      IdentitiesOnly yes

Or you can choose a fully-automated approach:

    $ heroku accounts:add work --auto
    Enter your Heroku credentials.
    Email: work@example.org
    Password: ******
    Generating new SSH key
    Generating public/private rsa key pair.
    Your identification has been saved in ~/.ssh/identity.heroku.work.
    Your public key has been saved in ~/.ssh/identity.heroku.work.pub.
    Adding entry to ~/.ssh/config
    Adding public key to Heroku account: work@example.org

To switch an app to a different account:

    # in project root
    heroku accounts:set personal

To list accounts:

    $ heroku accounts
    personal
    work

To remove an account:

    $ heroku accounts:remove personal
    Account removed: personal

Set a machine-wide default account:

    $ heroku accounts:default personal

To clone a git repository from Heroku, change 'heroku.com' to the Host of the desired account defined in your .ssh/config:

    $ git clone git@heroku.work:repository.git

If you want to switch the account for an app:

    $ heroku accounts:set work

This also changes the URL of the git origin `heroku` to make sure you're using the correct SSH host.
