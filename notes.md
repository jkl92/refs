
### ssh
##### ssh-agent

[This](https://unix.stackexchange.com/questions/132065/how-do-i-get-ssh-agent-to-work-in-all-terminals) works to make ssh-agent work across terminals (in tmux too), 
but it leaves your .sock file hanging which may need to be manually pruned and doesn't work perfectly.

~/.profile
```bash
export SSH_AUTH_SOCK=~/.ssh/ssh-agent.$HOSTNAME.sock
ssh-add -l 2>/dev/null >/dev/null
if [ $? -ge 2 ]; then
  ssh-agent -a "$SSH_AUTH_SOCK" >/dev/null
fi
```

Supposedly this works to make it available across all login sessions. Don't know how well or if [this](https://superuser.com/questions/141044/sharing-the-same-ssh-agent-among-multiple-login-sessions) works:

References:
- https://unix.stackexchange.com/questions/132065/how-do-i-get-ssh-agent-to-work-in-all-terminals
- https://superuser.com/questions/141044/sharing-the-same-ssh-agent-among-multiple-login-sessions

### tmux

References:
- https://gist.github.com/andreyvit/2921703
