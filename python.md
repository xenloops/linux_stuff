# Random Python stuff

## Use different version than the system-installed one

Debian slogs in getting newer versions of Python into its main repo -- that's why it's so excruciatingly stable. But we can install newer versions if a project requires it.

1. Install Dependencies

    ```
    sudo apt update
    sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev git
    ```

1. Install pyenv

    ```git clone https://github.com/pyenv/pyenv.git ~/.pyenv```

2. Configure Shell Environment

    ```
    echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
    echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
    ```

3. Reload the shell to apply the environment

    ```exec "$SHELL"```

4. Install Python Versions

    ```
    pyenv global <ver> # Set as default global version
    pyenv local <ver>  # Set for the current directory
    ```

5. 

