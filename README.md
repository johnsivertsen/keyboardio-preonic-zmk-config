# How to...

## Get and start docker image

```
docker run -it zmkfirmware/zmk-dev-arm:4.1-branch /bin/bash
```

## Attach to container and run...

```
bash # for usable shell experience
mkdir /workspaces
cd /workspaces
git clone https://github.com/johnsivertsen/keyboardio-preonic-zmk-config.git
export WORKSPACE_DIR=/workspaces/keyboardio-preonic-zmk-config
west init -l keyboardio-preonic-zmk-config/config
cd keyboardio-preonic-zmk-config
west update
export ZEPHYR_DIR=/workspaces/keyboardio-preonic-zmk-config/zephyr
west config build.cmake-args \
  -- "-DZMK_CONFIG=/workspaces/keyboardio-preonic-zmk-config/config"
west build --pristine -s zmk/app -b keyboardio_preonic
```

Copy file from build/zephyr/zmk.uf2 to keyboard via File Explorer.

If keyboard is not shown as drive in File Explorer, press `Fun` + `Hyper`. 

If successful, LEDs should change to:

```
(off, off)
(off, green)
```

Hyper button is in bottom left corner.
