# Eitri Developer Documentation

![Build](https://github.tools.sap/naat/developer-docs/workflows/Build/badge.svg)

The documentation is available at this link: [click me!](https://pages.github.tools.sap/naat/developer-docs)

To work on the documentation ensure that you have cloned this repository locally

## Opening the project in Visual Studio Code

Open Visual Studio Code (VSC), click _File -> Open Folder_, navigate to the folder containing the user-docs project, Click **Open**.

The project will load in VSC.

## Getting Started

### Using macOS Native Python

The new documentation suite uses a light-weight markdown server _MkDocs_. To install on your Mac , please run the following command on your command line in a terminal, to install _MkDocs_ into your system package library.

`sudo pip3 install --upgrade mkdocs mkdocs-autorefs mkdocstrings mkdocs-mermaid2-plugin mike`

### Using the integrated Docker Developer Container

To use the integrated Docker Developer Environment, click on the small green Icon on the bottom left hand corner of the editor. ![Remote Icon](./docs/img/vsc-icon.png)

This will make the remote select dropdown appear.

![Remote Icon](./docs/img/vsc-remoteopen.png)

Chose **Remote-Containers: Reopen in Container**.

The project will now open in a docker container.

![Remote Icon](./docs/img/vsc-opening.png)

As this is the first time we are opening this container it will take a while to open, as the required images need to be downloaded from the VSO docker image hub, to build the container. I suggest a coffee.

The container will be fully loaded and ready to use when the icon in the bottom left switches from **Opening Remote** to **Dev Container: NAAT Docs** as shown.

![Remote Icon](./docs/img/vsc-remoteopened.png)

We can now test that the container is up and running by opening a terminal within VSC.  `CTRL+backtick` open the new terminal.

The command prompt of the new terminal will read:

``` bash
╭─vscode@naat-docs /app  <develop›
╰─➤
```

## Starting the Document viewer server

Open a _Terminal Window_  and run `mkdocs serve` at the prompt _in the base folder_ of the repository.

```nohighlight
╭──you@your mac ./nat-doc.github.tools.sap  ‹develop›
╰─➤  mkdocs serve
INFO     -  Building documentation...
INFO     -  MERMAID2  - Initialization arguments: {}
INFO     -  MERMAID2  - Explicit mermaid javascript library:
               https://unpkg.com/mermaid/dist/mermaid.min.js
INFO     -  Cleaning site directory
INFO     -  The following pages exist in the docs directory, but are not included in the "nav" configuration:
              - glossary/working-with-github.md
INFO     -  MERMAID2  - Page 'Starting ZTP': found 2 diagrams (with <pre><code='[language-]mermaid'>), converting to
            <div>...
INFO     -  MERMAID2  - Page 'Starting ZTP': found 2 diagrams, adding scripts
INFO     -  MERMAID2  - Page 'Statuses Explained': found 1 diagrams (with <pre><code='[language-]mermaid'>),
            converting to <div>...
INFO     -  MERMAID2  - Page 'Statuses Explained': found 1 diagrams, adding scripts
INFO     -  Documentation built in 0.54 seconds
INFO     -  [14:15:19] Serving on http://127.0.0.1:8000/nat-docs/
```

The document viewer is now available, and can be accessed at `http://localhost:8000/nat-docs` for development. The server will watch for any changes to the documentation, and if valid, will incorporate the changes into the currently running service, which will allow for realtime updates.

> Sometimes, to get a [mermaid graph](https://mermaid-js.github.io/mermaid/#/) to render correctly, it will be necessary to refresh the browser window after reloading the server.

## Stopping the Document Viewer Server

To quit the server, click on the terminal and press `ctrl-c` as mentioned above.
