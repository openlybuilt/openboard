# OpenBoard

OpenBoard is a whiteboard for creating diagrams and visualizing ideas. Its platform lives in the `platform` submodule.

```sh
git clone --recurse-submodules https://github.com/openlybuilt/openboard.git
cd openboard/platform
pnpm install --frozen-lockfile
pnpm dev
```

If you already cloned without submodules, run `git submodule update --init --recursive` first.
