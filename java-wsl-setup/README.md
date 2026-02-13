# Java Environment Setup with SDKMAN version manager

This project uses SDKMAN!
 to manage Java versions on WSL (Windows Subsystem for Linux). To ensure proper functionality, especially with VS Code's Maven extension, a few environment setup steps are required.

## Prerequisites

1. WSL installed (Ubuntu or other Linux distribution).
1. SDKMAN! installed. Follow the official guide: https://sdkman.io/install
1. VS Code with the Maven Extension.

## Setup Instructions

1. Open your WSL terminal.
1. Add the following to your ~/.profile file (creates a global environment for all shells):
    ```bash
    # --- SDKMAN! & Java global environment for all shells ---
    export SDKMAN_DIR="$HOME/.sdkman"
    if [ -s "$SDKMAN_DIR/bin/sdkman-init.sh" ]; then
        source "$SDKMAN_DIR/bin/sdkman-init.sh"
    fi

    # Force JAVA_HOME and PATH globally
    export JAVA_HOME="$SDKMAN_DIR/candidates/java/current"
    export PATH="$JAVA_HOME/bin:$PATH"
    ```
1. Reload your profile:
    ```bash
    source ~/.profile
    ```
1. Verify that Java is correctly set:
    ```bash
    java -version
    echo $JAVA_HOME
    ```

You should see the version installed via SDKMAN! and the correct JAVA_HOME path.

## Notes

* Adding this to ~/.profile ensures that VS Code and its Maven extension can detect the Java environment correctly.
* SDKMAN! allows you to easily switch between multiple Java versions using:
    ```bash
    sdk list java
    sdk use java <version>
    sdk default java <version>
    ```

This setup ensures a consistent Java environment across all WSL shells and tools.
