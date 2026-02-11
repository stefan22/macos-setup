# Open with Webstorm :shell: Command line Launcher

```js
// I'd like to be able to do something like this with WebStorm
> open .zshrc

```

For some reason found it to be not as simple as you would with other Editors like **VSCode**, and it could just be that you also need to have **JetBrains Toolbox** installed for it to work. 🤔


## This works with MacOS 🩹

- Go to `/usr/local/bin` and create webstorm.sh file
- chmod +x /usr/local/bin/webstorm
- chown root:wheel /usr/local/bin/webstorm
- Add:
  ```js
    #!/bin/sh
    open -na "WebStorm.app" --args "$@" > /dev/null 2>&1 &

  ```
- Now open any file with webstorm from the command line like this:
  ```js
    webstorm .zshrc
  ```
- Or rename the file `storm` and open it like this
  ```js
    storm .zshrc
  ```
