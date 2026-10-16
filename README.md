# Install toolkit-sync from Forgejo

This repository contains access instructions only. Toolkit code, skills, installers
and updates are available only from the organization's Forgejo, over Tailscale.
Do not install a historical version from this repository or use it as a fallback.

## Connect

1. Install [Tailscale](https://tailscale.com/download) and sign in to the existing
   network approved by your organization. Do not create a replacement network.
2. Resolve the Forgejo **Git clone URL** and SSH host trust. Reuse an already
   supplied repository URL; its user/organization namespace is part of the URL,
   not another required input. Existing machines find the source registration via
   `~/.agents/doc/AGENTS.local.md` and its private baseline's `toolkit-source.json`.
   If only the approved Forgejo instance is known, use its existing signed-in
   browser or authenticated API session to find the canonical `agent-toolkit`
   repository, including organization repositories, and read its clone URL.
   Verify it against available trusted context; a same-named fork or mirror is
   not a replacement. Do not assume the login name owns the repository. If the
   target remains unknown or ambiguous, ask the administrator once for the full
   repository URL and missing host trust, rather than separate user/organization
   fields. Internal network names and credentials are intentionally not published here.
   If toolkit-sync is already installed but local registration/checkouts are
   missing, run its bundled machine-bootstrap client first on the verified
   approved Tailnet. Its server-registered default needs no owner or source URL;
   the recovered private checkout supplies `toolkit-source.json` and forge trust.
3. Use that registered MagicDNS hostname, not a remembered LAN address. Tailscale
   connectivity does not replace Forgejo authorization. If SSH access is missing,
   create a key on this device and register only its public key with Forgejo.
   Verify host trust; never disable SSH host-key checking or copy another device's key.

## Install

With Git installed, replace the placeholder with the approved credential-free URL:

```sh
git clone --branch main --single-branch '<approved Forgejo Git clone URL>' agent-toolkit
```

On Windows, use Git for Windows and Tailscale; private environment recovery also
needs Windows OpenSSH Client (`ssh`, `scp`, `ssh-keygen`). That recovery has a
native PowerShell `bootstrap.ps1` entrypoint in the checkout's
`skills/toolkit-sync/scripts/` directory. Read
`skills/toolkit-sync/references/environment/machine-bootstrap.md` before running it.
Omit the owner argument to read the archive's registered default `bootstrap.json`;
an existing private bootstrap checkout is not a prerequisite. An explicit archive
owner comes from trusted private registration and is independent of the Forgejo
repository namespace. Do not substitute the namespace or retry guessed owners
when the archive refuses a path. Toolkit's shell/vendor setup has separate
prerequisites; completing archive recovery alone does not verify runtime setup.

Ask your agent to read `agent-toolkit/skills/toolkit-sync/SKILL.md` **from that
Forgejo checkout** and install/run toolkit-sync. Its supporting references are in
the same checkout; do not copy only SKILL.md or install anything from GitHub history.
Subsequent toolkit installations and updates use that same Forgejo source.

If you already have an older GitHub clone, preserve local changes and installed
skills. Clone Forgejo into a separate empty directory and follow the current skill;
do not merge this guide-only branch into the toolkit checkout or sync its empty tree.
If Forgejo is unavailable, fix the registered access or request the missing approval.
Do not fall back to GitHub. Ordinary project repositories hosted on GitHub stay there.
