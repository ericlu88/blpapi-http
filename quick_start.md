# BLPAPI-HTTP quick start guide

- Install `homebrew` on your Mac [http://brew.sh/](http://brew.sh/)
- Install `git` & `node` through `brew install`.
- Install `cygwin` on your Windows VM through this [tutorial](http://www.larsavery.com/blog/how-to-install-sshd-secure-shell-server-on-windows-using-cygwin/). Start the `sshd` server by cmd `net start sshd`.
- In Windows, go to `Control Panel` -> `System and Security` -> `Windows Firewall` -> `Advanced settings` -> `Inbound Rules` -> `New Rule` -> Select `Port` -> Enter **22** as the `Specific local ports` -> `Allow the connection` -> Check all -> Give it a name -> `Finish`.
- Go back to MAC OS X. Modify your ssh config(`~/.ssh/config`, create one if not exist), by adding the following section:

```
  Host bbcomm
  HostName 172.16.82.129
  User traveler
  LocalForward 8194 127.0.0.1:8194
```

- Make sure your Bloomberg Terminal is logged-in and running. Run `ssh bbcomm`, type your Windows log-in credential. You should see an active ssh session created and running.
- Clone this repository from github: `git clone https://github.com/ericlu88/blpapi-http.git`
- Check out the `develop` branch: `git checkout -b {YOUR_LOCALBRANCH_NAME} origin/dapi`
- Run: `npm install`
- Run: `make`
- Start the `http` server: `node index.js --cfg=./examples/config/cfg.json`
- Go to your Chrome browser, install `postman` plugin [https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en]()
- Try to make a http request to your local server using postman:

```
    URL: http://localhost:3000/request?ns=blp&service=refdata&type=ReferenceDataRequest
    Post-Body: {
    "securities": [
        "IBM US Equity"
    ],
    "fields": [
        "LAST_PRICE"
    ]
}
```
