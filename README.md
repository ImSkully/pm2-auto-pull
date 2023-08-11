# PM2 Auto Pull <a href="https://pm2.keymetrics.io" target="_blank" alt="pm2"><img src="https://img.shields.io/badge/pm2-2B037A.svg?logo=pm2" /></a>

![Maintained](https://img.shields.io/maintenance/yes/2023.svg)
<a href="https://nodejs.org" target="_blank" alt="Node.js"><img src="https://img.shields.io/badge/Node.js-6DA55F?style=flat&logo=node.js&logoColor=white" /></a>
![License](https://img.shields.io/github/license/ImSkully/pm2-auto-pull)
<a href="./package-lock.json" target="_blank" alt="package-lock"><img src="https://img.shields.io/badge/package--lock-committed-brightgreen" /></a>
<a href="https://www.npmjs.com/package/@imskully\/pm2-auto-pull" target="_blank" alt="npmjs Package"><img src="https://img.shields.io/npm/v/@imskully/pm2-auto-pull.svg" /></a>

A simple and efficient [PM2](https://pm2.keymetrics.io) module that automatically pulls the latest git version for your pm2 processes, an improved implementation of [keymetrics/pm2-auto-pull](https://github.com/keymetrics/pm2-auto-pull).

* ⚡️ Fast and lightweight with minimal overhead!
* 🔧 Easy to install, ready to go immediately after installation
* 📝 Adjustable update-check interval to pull at specific intervals
* 🖱️ PM2 Dashboard action to manually trigger update fetches

# Installation & Setup
1. Install the module via `pm2`:
	```bash
	pm2 install @imskully/pm2-auto-pull
	```
	> [!IMPORTANT]  
	> Use `pm2 install`, not `npm install`!

2. *(Optional)* The default fetch interval is 30 seconds, configure the update interval with the following command:
	```bash
	pm2 set @imskully@pm2-auto-pull:interval <ms>
	```

3. The module should restart and begin fetching on the configured interval!

# Usage

Once the module is installed and configured, it will automatically begin checking for any updates for all **running processes** from their respective connected git version controls, any offline processes will be skipped.

> [!WARNING]  
> This module will `git reset --hard` to the latest version (`HEAD`) from your configured git remote and will overwrite any local changes that have not been committed or stashed!

You can optionally enable verbose logging to see when an interval check is run along with an output of all processes that were checked, skipped, and updated:
```bash
pm2 set @imskully/pm2-auto-pull:logging true
```

At any time, you can view when the last update check has run and other configured settings with:
```bash
pm2 show @imskully/pm2-auto-pull
```

# Uninstalling
To uninstall the module, simply run:
```bash
pm2 uninstall @imskully/pm2-auto-pull
```

This will remove the module from your PM2 configuration and stop it from running, you may also want to remove any configuration variables that were set:
```bash
pm2 unset @imskully/pm2-auto-pull:interval
pm2 unset @imskully/pm2-auto-pull:logging
```