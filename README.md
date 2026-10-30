# Nicocou for Windows: signed builds

Installers of **Nicocou**, a small island at the top of the Windows screen that shows your Claude Code sessions and lets you
approve, answer, chat and drop files without leaving what you are doing. It is a Windows fork of
[Coucou](https://github.com/Louis-CFM/coucou) by Louis Raillé.

This repository only holds what is built: the installer, its update signature and the update feed. The source code
lives in a private repository.

## Install

Download `Nicocou-Windows-<version>-setup.exe` from the [latest release](../../releases/latest) and run it. It installs for
the current user only (no administrator rights).

The installer and the program are signed with a **self-signed** certificate, `nicocou-codesign.cer`, whose SHA-1
thumbprint is `2AF719EB97C588B43A4819793A2FE77EF8C8ACD0`. Windows does not know it, so SmartScreen may warn and Defender
may flag the file falsely: check the thumbprint of the signature (Properties → Digital Signatures) against the one above
and the SHA-256 given in the release notes. To make Windows show "Nicolas GUILLAUME (Nicocou)" as the publisher on your PC,
trust the certificate (a Windows prompt asks to confirm the first command):

```powershell
Import-Certificate -FilePath nicocou-codesign.cer -CertStoreLocation Cert:\CurrentUser\Root
Import-Certificate -FilePath nicocou-codesign.cer -CertStoreLocation Cert:\CurrentUser\TrustedPublisher
```

## Updates

Off until you turn them on: **Settings → Updates → Check for updates**. Nicocou then asks this repository for
`latest.json` once at launch and every 6 hours (one small request, nothing about you or your PC). A new version is only
downloaded and installed after you click **Install and restart**, and only if it is signed with the author's update key,
whose public half is built into the app. Anything else is refused.

## Licences

The code is MIT-licensed: the copyright and licence of Coucou ([`LICENSE`](LICENSE), © 2026 Louis Raillé) and of the
phone-link code ([`LICENSE-phone-link`](LICENSE-phone-link), © 2026 Rhytam Biswas) apply to what is built here, and
Nicocou's own additions are MIT too.

The character (**Nico**), the app icon and the sounds are Nicocou's own, drawn and synthesised in code. Nothing of Coucou's
reserved name, character, icon or sounds is shipped (see Coucou's `LICENSE-ASSETS.md`).
