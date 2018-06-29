# 1p
🔑 1Password CLI Client, with SSH Integration 💻

`1p` is a wrapper around `op`, agilebits' 1Password CLI integration.

## Installation

```sh
go get -u github.com/ameliaikeda/1p
```

Alternatively, download a binary from the Releases section.

## Usage

You can start a session using `1p signin`. If it's your first time using `1p`, this will ask you for your 1password account email and URL, and your Account Secret Key.

Otherwise, it'll just ask you to enter your master password.

To SSH, just run `1p ssh [host]`.

```sh
1p help ssh

  1p ssh [host] [--passwd=UUID] [--key=UUID] [--keypass=UUID] [--duo]
  
    host (String): The SSH host to hit, as a full URL including user and port (defaults to $USER if user not specified)
  
  --passwd=UUID  : The UUID containing an SSH password in your vault. This will pull out the currently set password.
  
  --key=UUID     : The UUID of a file in your vault that contains your SSH key.
  
  --keypass=UUID : The UUID of an item containing the password for your encrypted SSH key.
  
  --duo          : Scratching my own itch; `--duo` will automatically accept a request for a Duo push when using multi-factor SSH.
```

## Environment variables

If you already know the UUIDs of your password or keyfile, you can specify these in your shell's startup env:

```sh
# SSH password auth (--passwd=UUID)
export SSH_PASSWORD_ID="aaaaaaaaaaaaaaaaaaaaaaaaaaaaa"

# SSH key auth (--key=UUID)
export SSH_KEY_ID="aaaaaaaaaaaaaaaaaaaaaaaaaaaaa"

# SSH key password (if encrypted) (--keypass=UUID)
export SSH_KEY_PASSWORD_ID="aaaaaaaaaaaaaaaaaaaaaaaaaaaaa"

# SSH default host (including user) ([host] in args)
export SSH_DEFAULT_HOST="${USER}@bastion.company.example"
```

## Running `op` directly

Just run `1p op` to run commands directly on its copy of `1p`.

## Updating

Run `1p update` to update to the latest version of `1p` and `op`.
You should put this in your shell startup scripts, e.g. in `.{bash,zsh}rc`.

## Licence and Credits

`1p` is under the BSD Licence; see `LICENCE` in the root of this repository for more details.
