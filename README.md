# ssh-swap

CLI tool to quickly switch between multiple SSH keys (e.g. multiple GitHub accounts).

## Install

```bash
git clone https://github.com/changfeifan1993/ssh-swap.git
cd ssh-swap
cp config.example.json config.json  # edit with your keys
```

Add alias to your shell rc:

```bash
alias ss="node /path/to/ssh-swap/bin/ssh-swap"
```

## Usage

```bash
ss                # interactive menu
ss list           # list all configured keys
ss use <name>     # switch to key: ssh-add -D → ssh-add <key> → ssh -T git@github.com
ss use            # no arg → interactive menu
ss current        # show currently loaded key
ss scan           # scan ~/.ssh/ for undiscovered keys
ss add <name> <path>   # add a key alias
ss remove <name>       # remove a key alias
```

## Config

Edit `config.json`:

```json
{
  "keys": {
    "personal": { "path": "~/.ssh/id_ed25519", "email": "you@example.com" },
    "work": { "path": "~/.ssh/id_rsa_work", "email": "you@company.com" }
  }
}
```

## Requirements

- Node.js
- No external dependencies
