
This is a minimal reproduction case for https://npm.community/t/package-lock-json-keeps-changing-between-platforms-and-runs/1129/4

The lockfile was generated on macOS by running `npm install chokidar`.

The CI jobs are configured to run `npm install`, show a diff of the package-lock.json file, and print the whole contents of package-lock.json.
If package-lock.json stayed the same, the build passes, otherwise it fails.

CI shows that when running `npm install` against that lockfile on Linux, package-lock.json changes (fail). On the macOS job, it stays the same (pass).

https://travis-ci.org/felixfbecker/npm-changing-lockfile-repro


Versions (latest at the time of writing):

- npm: 6.4.0
- node: 10.8.0

Diff copied from CI:

```diff
diff --git a/package-lock.json b/package-lock.json
index 03ab71d..6f3d391 100644
--- a/package-lock.json
+++ b/package-lock.json
@@ -462,12 +462,14 @@
         "balanced-match": {
           "version": "1.0.0",
           "resolved": "https://registry.npmjs.org/balanced-match/-/balanced-match-1.0.0.tgz",
-          "integrity": "sha1-ibTRmasr7kneFk6gK4nORi1xt2c="
+          "integrity": "sha1-ibTRmasr7kneFk6gK4nORi1xt2c=",
+          "optional": true
         },
         "brace-expansion": {
           "version": "1.1.11",
           "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
           "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
+          "optional": true,
           "requires": {
             "balanced-match": "^1.0.0",
             "concat-map": "0.0.1"
@@ -482,17 +484,20 @@
         "code-point-at": {
           "version": "1.1.0",
           "resolved": "https://registry.npmjs.org/code-point-at/-/code-point-at-1.1.0.tgz",
-          "integrity": "sha1-DQcLTQQ6W+ozovGkDi7bPZpMz3c="
+          "integrity": "sha1-DQcLTQQ6W+ozovGkDi7bPZpMz3c=",
+          "optional": true
         },
         "concat-map": {
           "version": "0.0.1",
           "resolved": "https://registry.npmjs.org/concat-map/-/concat-map-0.0.1.tgz",
-          "integrity": "sha1-2Klr13/Wjfd5OnMDajug1UBdR3s="
+          "integrity": "sha1-2Klr13/Wjfd5OnMDajug1UBdR3s=",
+          "optional": true
         },
         "console-control-strings": {
           "version": "1.1.0",
           "resolved": "https://registry.npmjs.org/console-control-strings/-/console-control-strings-1.1.0.tgz",
-          "integrity": "sha1-PXz0Rk22RG6mRL9LOVB/mFEAjo4="
+          "integrity": "sha1-PXz0Rk22RG6mRL9LOVB/mFEAjo4=",
+          "optional": true
         },
         "core-util-is": {
           "version": "1.0.2",
@@ -609,7 +614,8 @@
         "inherits": {
           "version": "2.0.3",
           "resolved": "https://registry.npmjs.org/inherits/-/inherits-2.0.3.tgz",
-          "integrity": "sha1-Yzwsg+PaQqUC9SRmAiSA9CCCYd4="
+          "integrity": "sha1-Yzwsg+PaQqUC9SRmAiSA9CCCYd4=",
+          "optional": true
         },
         "ini": {
           "version": "1.3.5",
@@ -621,6 +627,7 @@
           "version": "1.0.0",
           "resolved": "https://registry.npmjs.org/is-fullwidth-code-point/-/is-fullwidth-code-point-1.0.0.tgz",
           "integrity": "sha1-754xOG8DGn8NZDr4L95QxFfvAMs=",
+          "optional": true,
           "requires": {
             "number-is-nan": "^1.0.0"
           }
@@ -635,6 +642,7 @@
           "version": "3.0.4",
           "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.0.4.tgz",
           "integrity": "sha512-yJHVQEhyqPLUTgt9B83PXu6W3rx4MvvHvSUvToogpwoGDOUQ+yDrR0HRot+yOCdCO7u4hX3pWft6kWBBcqh0UA==",
+          "optional": true,
           "requires": {
             "brace-expansion": "^1.1.7"
           }
@@ -642,12 +650,14 @@
         "minimist": {
           "version": "0.0.8",
           "resolved": "https://registry.npmjs.org/minimist/-/minimist-0.0.8.tgz",
-          "integrity": "sha1-hX/Kv8M5fSYluCKCYuhqp6ARsF0="
+          "integrity": "sha1-hX/Kv8M5fSYluCKCYuhqp6ARsF0=",
+          "optional": true
         },
         "minipass": {
           "version": "2.2.4",
           "resolved": "https://registry.npmjs.org/minipass/-/minipass-2.2.4.tgz",
           "integrity": "sha512-hzXIWWet/BzWhYs2b+u7dRHlruXhwdgvlTMDKC6Cb1U7ps6Ac6yQlR39xsbjWJE377YTCtKwIXIpJ5oP+j5y8g==",
+          "optional": true,
           "requires": {
             "safe-buffer": "^5.1.1",
             "yallist": "^3.0.0"
@@ -666,6 +676,7 @@
           "version": "0.5.1",
           "resolved": "https://registry.npmjs.org/mkdirp/-/mkdirp-0.5.1.tgz",
           "integrity": "sha1-MAV0OOrGz3+MR2fzhkjWaX11yQM=",
+          "optional": true,
           "requires": {
             "minimist": "0.0.8"
           }
@@ -746,7 +757,8 @@
         "number-is-nan": {
           "version": "1.0.1",
           "resolved": "https://registry.npmjs.org/number-is-nan/-/number-is-nan-1.0.1.tgz",
-          "integrity": "sha1-CXtgK1NCKlIsGvuHkDGDNpQaAR0="
+          "integrity": "sha1-CXtgK1NCKlIsGvuHkDGDNpQaAR0=",
+          "optional": true
         },
         "object-assign": {
           "version": "4.1.1",
@@ -758,6 +770,7 @@
           "version": "1.4.0",
           "resolved": "https://registry.npmjs.org/once/-/once-1.4.0.tgz",
           "integrity": "sha1-WDsap3WWHUsROsF9nFC6753Xa9E=",
+          "optional": true,
           "requires": {
             "wrappy": "1"
           }
@@ -879,6 +892,7 @@
           "version": "1.0.2",
           "resolved": "https://registry.npmjs.org/string-width/-/string-width-1.0.2.tgz",
           "integrity": "sha1-EYvfW4zcUaKn5w0hHgfisLmxB9M=",
+          "optional": true,
           "requires": {
             "code-point-at": "^1.0.0",
             "is-fullwidth-code-point": "^1.0.0",
```
