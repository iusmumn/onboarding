# team-guide

Our guidebook for how we do engineering! This guide is intended to help you get started with our projects!

If you have any questions or if things are not clear, please create an issue or a pull request to clear it up or ask the question.

# Getting Started

Please follow the instructions below to install necessary software we need for developing our projects.

## Software Installation

Please intsall the following software on your computer:

- [Docker](https://www.docker.com/products/docker-desktop) - Docker is how we will run the applications we build

- [Insomnia](https://insomnia.rest/download) - Insomnia is how we will test our backend code

- [pgAdmin 4](https://ftp.postgresql.org/pub/pgadmin/pgadmin4/v5.3/macos/pgadmin4-5.3.dmg) - pgAdmin is how we will view our database tables and records

- [Visual Studio Code](https://code.visualstudio.com/) - or "VS code" for short, will be our code editor
    - Extensions (open VS Code and download from extensions marketplace):
        - Python
        - Docker
        - Atom One Dark Theme _(optional)_
        - Material Icon Theme _(optional)_

**Optional**

- [iTerm2](https://iterm2.com/downloads.html) - An alternative terminal to the native Mac terminal

- [Postman](https://www.postman.com/downloads/) - The alternative to [Insomnia](https://insomnia.rest/download)

## Setup Git SSH

We will be using [git](https://git-scm.com/downloads/) to manage our code on our machines and on [github.com/iusmumn](https://github.com/iusmumn).

To avoid having to type in our username/password _every_ time we do something like a `git push`, follow the steps below. (If you've already have ssh setup on your GitHub account, please skip this section).

### 1.) Generating a new SSH key

1. Open Terminal.

1. Copy and paste the text below, and REPLACE the example email below with your **GitHub email address**. (Note: do not include the `$` symbol below when copying).

    ```bash
    $ ssh-keygen -t ed25519 -C "your_email@example.com"
    ```
    This creates a new ssh key, using the provided email as a label.
1. When you're prompted to _"Enter a file in which to save the key,"_ just press ENTER. This accepts the default file location.

    ```
    > Enter a file in which to save the key (/Users/your_username/.ssh/id_ed25519): [Press Enter]
    ```
1. At the prompt, just press Enter. No need to type a secure passphrase.

    ```
    > Enter passphrase (empty for no passphrase): [Press Enter]
    > Enter same passphrase again: [Press Enter]
    ```

### 2.) Adding your SSH key to the ssh-agent

1. Start the ssh-agent in the background.

    ```bash
    $ eval "$(ssh-agent -s)"
    > Agent pid 59566
    ```

1. If you're using macOS Sierra 10.12.2 or later, you will need to modify your `~/.ssh/config` file to automatically load keys into the ssh-agent and store passphrases in your keychain.

    - First, check to see if your `~/.ssh/config` file exists in the default location:

        ```bash
        $ open ~/.ssh/config
        > The file /Users/you/.ssh/config does not exist.
        ```

        If you do not have the `open` command, use `vi` instead:

        ```bash
        $ vi ~/.ssh/config
        > The file /Users/you/.ssh/config does not exist.
        ```

    - If the file `~/.ssh/config` doesn't exist, create the file:

        ```bash
        $ sudo touch ~/.ssh/config
        ```

        You may be prompted to enter your computer's password in order to create the file.

    - Open the `~/.ssh/config` file, then modify the file to contain the following lines.

        ```
        Host *
        AddKeysToAgent yes
        UseKeychain yes
        IdentityFile ~/.ssh/id_ed25519
        ```

1. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace _id_ed25519_ in the command with the name of your private key file.

    ```bash
    $ ssh-add -K ~/.ssh/id_ed25519
    ```
### 3.) Add the SSH key to your account on GitHub

1. Copy the SSH public key to your clipboard.

    ```bash
    $ pbcopy < ~/.ssh/id_ed25519.pub
    # Copies the contents of the id_ed25519.pub file to your clipboard
    ```

    If you do not have `pbcopy`, just open the file and copy its contents.

1. Navigate to your GitHub account's Settings > [SSH and GPG keys](https://github.com/settings/keys)

1. Click on the green `New SSH key` button and paste in the contents of your file. The title can be `Personal Macbook`


Hooray! 🎉 You're done. Now you can interact with GitHub through your machine using `git` without having to enter in your username and password all the time!