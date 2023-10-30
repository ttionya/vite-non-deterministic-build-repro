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

### Update 20231030

According to [vitejs/vite#13672](https://github.com/vitejs/vite/issues/13672#issuecomment-1784110536), after adding the `build.commonjsOptions.strictRequires` option, the example in the current repository is now able to achieve deterministic builds.

By running `npm run build:fixed`, the "vendor" file consistently gets the hash "a87a6588".
