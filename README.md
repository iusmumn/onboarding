# team-guide

Our guidebook for how we do engineering! This guide is intended to help you get started with our projects!

If you have any questions or if things are not clear, please create an issue or a pull request to clear it up or ask the question.

# Getting Started

Please follow the instructions below to install necessary software we need for developing our projects.

## Software Installation

Please intsall the following software on your computer:

- [Docker](https://www.docker.com/products/docker-desktop) - Docker is how we will run the applications we build

- [Insomnia](https://insomnia.rest/download) - Insomnia is how we will test our backend code

- [pgAdmin 4](https://www.postgresql.org/ftp/pgadmin/pgadmin4/v5.3/macos/) - pgAdmin is how we will view our database tables and records

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

### Generating a new SSH key

1. Open Terminal.

1. Paste the text below, substituting in your **GitHub email address**.

    ```
    $ ssh-keygen -t ed25519 -C "your_email@example.com"
    ```
    This creates a new ssh key, using the provided email as a label.
    ```
    > Generating public/private ed25519 key pair.
    ```
1. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

    ```
    > Enter a file in which to save the key (/Users/you/.ssh/id_ed25519): [Press enter]
    ```
1. At the prompt, type a secure passphrase.

    ```
    > Enter passphrase (empty for no passphrase): [Just press enter]
    > Enter same passphrase again: [Just press enter]
    ```

### Adding your SSH key to the ssh-agent

1. Start the ssh-agent in the background.

    ```
    $ eval "$(ssh-agent -s)"
    > Agent pid 59566
    ```

1. If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

    - First, check to see if your ~/.ssh/config file exists in the default location.

        ```
        $ open ~/.ssh/config
        > The file /Users/you/.ssh/config does not exist.
        ```

    - If the file doesn't exist, create the file.

        ```
        $ touch ~/.ssh/config
        ```

    - Open your `~/.ssh/config` file (can open with `vim`), then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.

        ```
        Host *
        AddKeysToAgent yes
        UseKeychain yes
        IdentityFile ~/.ssh/id_ed25519
        ```

1. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace _id_ed25519_ in the command with the name of your private key file.

    ```
    $ ssh-add -K ~/.ssh/id_ed25519
    ```
1. [Add the SSH key to your account on GitHub](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account).

Hooray! 🎉 You're done. Now you can interact with GitHub through your machine using `git` without having to enter in your username and password all the time!