# Node-JS related

## npm

### npm install exit code 127

Doing `npm install -g yo` as root user and ended up with exit code 127.

Methods that I tried:

1. `npm set unsafe-perm true`
2. `npm set user 0`
3. `npm install -g --allow-root`

None of them worked.

The final solution:

```.sh
$ adduser node-user
...
$ su node-user
```

Reason:

Apparently, `node` doesn't allow installing package as `root`. It downgrades it's permission to a `non-root` user. My `node` was installed via `nvm` as `root`. Therefore, other users don't have `node` leading to `exit code 127`. So creating a `non-root` user and start from there should fix the issue.
 