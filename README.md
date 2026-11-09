# OpenBoard

OpenBoard is a whiteboard for creating diagrams and visualizing ideas. The app lives in the `platform` submodule; `openboard-backend` contains the account storage API.

```sh
git clone --recurse-submodules https://github.com/openlybuilt/openboard.git
cd openboard/platform
pnpm install --frozen-lockfile
pnpm dev
```

If you already cloned without submodules, run `git submodule update --init --recursive` first.

See `openboard-backend/README.md` for backend setup.
