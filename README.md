# reveal.nb

## Description

Launches a Reveal.js server and sends a note to it, and then opens it as a presentation. While the server is active, it will listen for any changes to the markdown file and hot reload.

A plugin for `nb` <https://github.com/xwmx/nb>.

Author: Jangari <https://github.com/jangari>.

## Installation

1. Ensure you have the full installation of Reveal.js, including npm, installed on your system. See the documentation [here](https://revealjs.com/installation/#full-setup).
2. Symlink your `$NB_DIR` (the directory containing your notes) into the Reveal.js directory. This allows the plugin to access your notes from the location where the server is started.
3. Download the `nb.html` file from this repository and install it inside your Reveal.js directory. This file is necessary as it includes a script that parses the query string parameter and loads the selected notebook into the data-markdown attribute.
4. Define the required environment variables in your `.nbrc` file (see below).
5. Install reveal.nb-plugin either by:
```sh
nb plugins install https://github.com/jangari/reveal.nb/blob/main/reveal.nb-plugin
```
Or
```sh
nb plugins install path/to/reveal.nb-plugin
```

## Usage

```sh
nb reveal [ --stop | <selector>  [ --kill-after <timeout> ] [ --no-open ] ]
```

## Options

| Option | Description |
| --- | --- |
| -s, --stop                 | Stop a running server |
| -k, --kill-after \<timeout\> | Automatically kill the server after \<timeout\> seconds. |
| -n, --no-open              | Launch server but do not open. Useful for re-connecting a live browser session to a server for hot reloading. |

## Environment Variables

| Variable | Description |
| --- | --- |
| NB_REVEAL_PATH            | Mandatory. Path to reveal.js library. |
| NB_REVEAL_NOTE_PATH       | Mandatory. Path, relative to `NB_REVEAL_PATH`, in which notes are stored. |
| NB_REVEAL_HTML            | Path to html file to load. Useful to maintain a specific config for your nb presentations separate from others. Defaults to null, thus loading 'index.html'. |
| NB_REVEAL_BROWSER_CMD     | Command to open browser. If not defined, either `xdg-open`, `gnome-open` or `open` is used. |
