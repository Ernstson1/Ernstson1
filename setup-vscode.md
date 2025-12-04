# WC Dual Stock – VS Code Setup (Windows)

This guide explains how to set up Visual Studio Code on Windows for working with the WC Dual Stock WordPress plugin.

---

## VS code extensions
### Intelephense
```text
bmewburn.vscode-intelephense-client
```

### PHP Debug
```text
xdebug.php-debug
```

### WordPress Hooks
```text
johnbillion.vscode-wordpress-hooks
```

### PHP Intellisense
```text
zobo.php-intellisense
```

### PHP Namespace Resolver
```text
mehedidracula.php-namespace-resolver
```

### SFTP
```text
natizyskunk.sftp
```

### WooCommerce
```text
claudiosanches.woocommerce
```

### WordPress Snippet
```text
tungvn.wordpress-snippet
```

### WordPress Toolbox
```text
wordpresstoolbox.wordpress-toolbox
```

## PHP install
If not installed, install the latest php using:
```powershell
winget install -e --id PHP.PHP
```

Verify the install with

```powershell
php -v
```
If the version appears the install was successful

## VS Code PHP Settings

Create a `.vscode` folder in your project (if it does not exist) and inside it create a file named `settings.json`:

```json
{
  "php.validate.executablePath": "C:\\Program Files\\php\\php.exe",
  "intelephense.environment.phpVersion": "8.1",
  "editor.formatOnSave": true,
  "[php]": {
    "editor.defaultFormatter": "bmewburn.vscode-intelephense-client"
  }
}
```
If the path is not correct run 
```powershell
where.exe php
```


## SFTP setup

Create a .vscode folder in the desired directory you want to sync.
In that folder create a file called `sftp.json` in that file past the following
changing pasting the correct credentials.  
Change the following:
* `host` – The ip of the remote server. 
* `username` – The username on the remote server. 
* `privateKeyPath` – The path to your ssh key
* `remotePath` – The path on the server where you want to sync to


```json
{
    "host": "SERVER_OR_VM_HOSTNAME",
    "username": "USERNAME",
    "protocol": "sftp",

    "privateKeyPath": "C:\\Users\\USERNAME\\.ssh\\id_ed25519",


    "remotePath": "/var/www/wcsite/wp-content/plugins/wc-dual-stock",

    "uploadOnSave": true,

    "ignore": [
        "**/.git/**",
        "**/.vscode/**",
        "**/node_modules/**",
        "**/vendor/**",
        "**/*.log",
        "**/.DS_Store"
    ],

    "concurrency": 5,
    "showHidden": false
}
```

