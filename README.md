# BACHAI Google Drive MCP Server

This repository contains a simple landing page, privacy policy, and terms of service for the BACHAI Google Drive MCP Server.

## Overview

The BACHAI Google Drive MCP Server allows listing, reading, and searching files on Google Drive. It integrates with the Model Context Protocol (MCP) to provide a standardized interface for accessing Google Drive data.

## Getting Started

1.  **Google Cloud Project:** Create a new Google Cloud project.
2.  **Enable Google Drive API:** Enable the Google Drive API for your project.
3.  **OAuth Consent Screen:** Configure the OAuth consent screen in the Google Cloud Console.
    *   Set the app name, user support email, application home page, privacy policy link, and terms of service link.
    *   Add the `https://www.googleapis.com/auth/drive.readonly` scope.
4.  **OAuth Client ID:** Create an OAuth Client ID for application type "Desktop App".
5.  **Download OAuth Keys:** Download the JSON file of your client's OAuth keys.
6.  **Rename and Place Keys:** Rename the key file to `gcp-oauth.keys.json` and place it in the root of the `servers/src/gdrive` repository (i.e., `servers/src/gdrive/gcp-oauth.keys.json`).
7.  **Build the Server:** Navigate to the `servers/src/gdrive` directory and run `npm run build` or `npm run watch`.
8.  **Authentication:** Authenticate the server with Google Drive using either Node.js or Docker:

    *   **Node.js:** `node ./dist/index.js auth`
    *   **Docker:**
        ```bash
        docker run -i --rm --mount type=bind,source=/path/to/gcp-oauth.keys.json,target=/gcp-oauth.keys.json -v mcp-gdrive:/gdrive-server -e GDRIVE_OAUTH_PATH=/gcp-oauth.keys.json -e "GDRIVE_CREDENTIALS_PATH=/gdrive-server/credentials.json" -p 3000:3000 mcp/gdrive auth
        ```

9.  **Configuration:** Integrate the server with your desktop application by adding the appropriate configuration to your app's server configuration file (see the original repository's `README.md` for examples).

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact

For questions or support, please contact dalkeith@golden.net.
