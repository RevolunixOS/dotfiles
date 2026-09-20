# RevolunixOS dotfiles

Personal NixOS and Home Manager configuration for the original RevolunixOS
development workstation. The flake assembles the host `RevoluNixOS`, the user
`gabriel`, hardware modules, and the graphical base exported by
[`module-system`](https://github.com/RevolunixOS/module-system).

> [!CAUTION]
> This is a reference configuration, not a generic installer. It contains a
> fixed hostname, username, initial password, hardware imports, and personal
> files. Read the complete diff and replace those values before rebuilding.

## Layout

```text
flake.nix                 host and user composition
hardware/                 host hardware configuration
system/                   machine-level NixOS settings
home/                     Home Manager configuration
assets/                   wallpapers, branding, and screenshots
```

## Try it safely

Clone the repository and inspect the evaluated host before switching:

```bash
git clone https://github.com/RevolunixOS/dotfiles.git
cd dotfiles
nix flake show
sudo nixos-rebuild build --flake .#RevoluNixOS
```

Only after adapting the hostname, users, hardware modules, and imports should
you activate it:

```bash
sudo nixos-rebuild switch --flake .#RevoluNixOS
```

## Known limitations

- The flake pins NixOS/Home Manager 24.05-era inputs.
- Some inputs still use the legacy `RevoluNix` GitHub namespace.
- The configuration enables unfree packages and is tailored to one x86-64 PC.
- `initialPassword = "admin"` is present in the source and must not be kept on
  a real installation.

## License

See [`LICENSE`](LICENSE).
