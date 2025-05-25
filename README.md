[![.github/workflows/build.yaml](https://github.com/dnlbauer/corax-zmk-config/actions/workflows/build.yaml/badge.svg)](https://github.com/dnlbauer/corax-zmk-config/actions/workflows/build.yaml)

# Firmware configuration for the Corax keyboard

This is my personal [ZMK](https://zmk.dev/) firmware configuration for the [Corax](https://github.com/dnlbauer/corax-keyboard).

The keymap optimised for US international.

## Using this Config as a template

You can use this configuration on your own Corax keyboard
or use it as a base to create your own configuration with a custom
keymap:

1. Fork this repository
2. Make sure the `config/west.yaml` contains a reference to the [zmk-keyboards-corax](https://github.com/dnlbauer/zmk-keyboards-corax) module

```yaml
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: dnlbauer
      url-base: https://github.com/dnlbauer
  projects:
    - name: zmk
      import: app/west.yml
      remote: zmkfirmware
      revision: main
    - name: zmk-keyboards-corax
      remote: dnlbauer
      revision: main
  self:
    path: config
```

3. Customize the keymap in `config/corax.keymap`
4. Commit and push. Github Actions will build the firmware for you
5. Download the firmware artifact and copy it onto your keyboard (see [zmk user setup](https://zmk.dev/docs/user-setup)).

## Corax56 vs Corax54

The Corax56 and Corax54 use the same shield.
The hardware of both keyboards is identical except the Corax54 is missing one hardware key.
Therefore, you can use the same ZMK firmware for both versions of the corax.
If you have a Corax54, just set the outer pinky key to `&none`
(basically, you can set it to whatever you want. It will be ignored).

## License

MIT License
