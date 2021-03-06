# Getting Started

[code-server](https://coder.com) is used by developers at Azure, Google, Reddit, and more to give them access to VS Code in the browser.

## Quickstart guide

> NOTE: If you get stuck or need help, [file an issue](https://github.com/codercom/code-server/issues/new?&title=Improve+self-hosted+quickstart+guide), [tweet (@coderhq)](https://twitter.com/coderhq) or [email](mailto:support@coder.com?subject=Self-hosted%20quickstart%20guide).

This document pertains to Coder specific implementations of VS Code. For documentation on how to use VS Code itself, please refer to the official [documentation for VS Code](https://code.visualstudio.com/docs) 

It takes just a few minutes to get your own self-hosted server running. If you've got a machine running macOS, Windows, or Linux, you're ready to start the binary which listens on port `8080` by default.

<!--
  DO NOT CHANGE THIS TO A CODEBLOCK.
  We want line breaks for readability, but backslashes to escape them do not work cross-platform.
  This uses line breaks that are rendered but not copy-pasted to the clipboard.
-->


1. Visit [the releases](https://github.com/codercom/code-server/releases) page and download the latest cli for your operating system
2. Double click the executable to run in the current directory
3. Copy the password that appears in the cli<img src="../assets/cli.png">
4. In your browser navigate to `localhost:8080`
5. Paste the password from the cli into the login window<img src="../assets/server-password-modal.png">
> NOTE: Be careful with your password as sharing it will grant those users access to your server's file system

### Things to know
- When you visit the IP for your code-server, you will be greeted   with this page. Code-server is using a self-signed SSL certificate for easy setup. To proceed to the IDE, click **"Advanced"**<img src ="../assets/chrome_warning.png">
- Then click **"proceed anyway"**<img src="../assets/chrome_confirm.png">

## Usage
<pre class="pre-wrap"><code>code-server<span class="virtual-br"></span> --help</code></pre>

code-server can be ran with a number of arguments to customize your working directory, host, port, and SSL certificate.

```
USAGE
  $ code-server [WORKDIR]

ARGUMENTS
  WORKDIR  [default: (directory to binary)] Specify working dir

OPTIONS
  -d, --data-dir=data-dir
  -h, --host=host          [default: 0.0.0.0]
  -o, --open               Open in browser on startup
  -p, --port=port          [default: 8080] Port to bind on
  -v, --version            show CLI version
  --cert=cert
  --cert-key=cert-key
  --password=password
  --help                   show CLI help
  ```

  ### Data directory
  Use `code-server -d (path/to/directory)` or `code-server --data-dir=(path/to/directory)`, excluding the parentheses to specify the root folder that VS Code will start in

  ### Host
  By default, code-server will use `0.0.0.0` as it's address. This can be changed by using `code-server -h` or `code-server --host=` followed by the address you want to use. 
  > Example: `code-server -h 127.0.0.1`

  ### Open
  You can have the server automatically open the VS Code in your browser on startup by using the `code server -o` or `code-server --open` flags

  ### Port  
  By default, code-server will use `8080` as it's port. This can be changed by using `code-server -p` or `code-server --port=` followed by the port you want to use. 
  > Example: `code-server -p 9000`

  ### Cert and Cert Key
  To encrypt the traffic between the browser and server use `code-server --cert=` followed by the path to your `.cer` file. Additionally, you can use certificate keys with `code-server --cert-key` followed by the path to your `.key` file.
> Example (certificate and key): `code-server --cert /etc/letsencrypt/live/example.com/fullchain.cer --cert-key /etc/letsencrypt/live/example.com/fullchain.key`

> To ensure the connection between you and your server is encrypted view our guide on [securing your setup](../security/ssl.md)

  ### Help
  Use `code-server -h` or `code-server --help` to view the usage for the cli. This is also shown at the beginning of this section.