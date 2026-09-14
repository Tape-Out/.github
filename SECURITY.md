# Security

A hardware bug can be a security bug: a privilege check that lets user mode return into machine mode, or a MAC that pads a short frame with the previous frame's bytes. Report those privately.

Use **Report a vulnerability** on the Security tab of the affected repository, with the repository, the configuration and a reproduction, ideally a `ran test` point that fails.

A fix lands together with a check that fails without it.
