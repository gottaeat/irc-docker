# irc-docker
irc-docker sets up an alpine-based docker container that establishes a tmux
session that automatically spawns irssi instances. the communication to the
tmux session is done via an sshd instance that runs as the `irc` user
(`uid:gid` == `1337:1337`).

### installation
```sh
git clone --depth=1 https://github.com/gottaeat/irc-docker
cd irc-docker/

cp env.example .env # modify the contents

docker compose up
```

### customization
users can supply their own files for software running inside the container in
the following paths. if none supplied, the defaults provided by alpine will be
used. do note that the entrypoint will `chown` and `chmod` them automatically.


| configuration | path                    |
|---------------|-------------------------|
| SSH banner    | `$DATA_DIR/sshd/banner` |
| tmux          | `$DATA_DIR/.tmux.conf`  |
| irssi         | `$DATA_DIR/.irssi/`     |
| busybox ash   | `$DATA_DIR/.profile/`   |

**warning**: make sure to define at least `LANG` and `LC_ALL` as `en_US.UTF-8`.
