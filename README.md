# AgentAPI Plugin for Dify

**Author:** [Steven Lynn](https://github.com/stvlynn)
**Version:** 0.0.1
**Type:** tool

## Description

This plugin allows Dify to interact with an [AgentAPI](https://github.com/coder/agentapi) server. AgentAPI provides a unified HTTP interface to control various coding agents like Claude Code, Goose, Aider, and Codex.

With this plugin, you can:

*   Get the current status of the connected agent.
*   Retrieve the full conversation history.
*   Send messages to the agent, either as conversational input or as raw terminal commands.

## AgentAPI Server Setup

Before using this plugin, you need to set up and run an AgentAPI server.

1.  **Download the binary:**
    Go to the [AgentAPI releases page](https://github.com/coder/agentapi/releases) and download the appropriate binary for your operating system.

2.  **Make it executable and move to PATH:**
    Open your terminal, navigate to the download location, and run the following commands:

    ```bash
    # Make the binary executable
    chmod +x ./agentapi-your-os-arch

    # Move it to a directory in your PATH
    sudo mv ./agentapi-your-os-arch /usr/local/bin/agentapi
    ```

3.  **Start the server:**
    You can now start the AgentAPI server with your desired agent. For example, to run it with Claude, use:

    ```bash
    agentapi server -- claude
    ```

    The server will start on `http://localhost:3284` by default.

## Plugin Installation and Configuration

1.  Install this plugin in your Dify instance.
2.  When adding the tool, you will be prompted to enter the **AgentAPI Server URL**. Provide the full URL of your running server (e.g., `http://localhost:3284`).

## Tools

The plugin provides the following tools:

### 1. Get Agent Status

*   **Description:** Fetches the current status of the agent.
*   **Returns:** `{"status": "stable"}` or `{"status": "running"}`.

### 2. Get Conversation History

*   **Description:** Retrieves the entire conversation history with the agent.
*   **Returns:** A JSON object containing a list of message objects.

### 3. Send Message

*   **Description:** Sends a message to the agent.
*   **Parameters:**
    *   `content` (string, required): The message content.
    *   `type` (select, required): The message type. 
        *   `user`: For conversational messages that are logged to the history.
        *   `raw`: For sending raw keystrokes or escape sequences directly to the agent's terminal (e.g., Ctrl+C).

## Feedback and Issues

If you encounter any problems or have suggestions for improvements, please open an issue in the [plugin's GitHub repository](https://github.com/stvlynn/agentapi-dify-plugin).
