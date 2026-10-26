# General Tips

## Bash Tips

- Can use the `Tab` key and `./*` to list directory when `ls` is not available (for example, when `ssh`-ing into a constrained server).

- There are many useful bash's internal variables, such as `$_` which is the final argument of the previous command.

- __Bash string manipulation example:__ we have `$_` = "hello", then `${_:1:3}` = "ell", with `1` as the starting index, and `3` as the number of characters to take.
&rarr; This can put in bash as command, as bash just take the first token of a command as the thing to run.

- To run multiple command in one line: try both `&&` and `;`.

## Command Tips

- `sudo -l`: List sudo permission for an user (such as which executables they can run).

- To decrypt RSA with private key: `openssl pkeyutl -decrypt -inkey privatekey.pem -in flag.enc -out flag.txt`
