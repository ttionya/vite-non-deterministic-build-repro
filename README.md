# vite-non-deterministic-build-repro

This project is used to showcase the unpredictable nature of build artifacts in Vite.

You can review the Git commit history to see the changes. The commit that caused the unpredictable build artifacts is ["feat: add dayjs with locale"](https://github.com/ttionya/vite-non-deterministic-build-test/commit/9d84636aeb05ecbb8124e7d3e16107b1698354a4).

### Usage

To reproduce the issue, you can execute the `npm run build` command multiple times.

Not every build will necessarily generate a different hash, but if you perform multiple builds, you may notice that the hash for the "vendor" file alternates between "44151d35" and "b28a2537". The **"output"** folder contains multiple packaged vendor files from different builds.

I have replicated the issue on multiple computers.

1. Windows 10 with Node 14.21
2. Mac OS with Node 16.12

### Screenshots

![screenshots](/screenshots/screenshots.png)
