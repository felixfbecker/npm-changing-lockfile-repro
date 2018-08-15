
This is a minimal reproduction case for https://npm.community/t/package-lock-json-keeps-changing-between-platforms-and-runs/1129/4

The lockfile was generated on macOS by running `npm install chokidar`.

The CI jobs are configured to run `npm install`, show a diff of the package-lock.json file, and print the whole contents of package-lock.json.

CI shows that when running `npm install` against that lockfile on Linux, package-lock.json changes. On the macOS job, it stays the same.

https://travis-ci.org/felixfbecker/npm-changing-lockfile-repro
