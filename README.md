# vitest-error

Reproduce `Debug test` error in vscode vitest extension with latest vitest version.

## environment

* vscode 1.95.3
* OS: Windows_NT x64 10.0.26100 (Windows 11)
* Nodejs: 20.18.0
* npm 10.9.1
* vscode vitest extension v1.8.1
* vitest 2.1.7
* MSYS2 GNU bash, version 5.2.37(1)-release (x86_64-pc-msys)

## npm

Starting point is an empty project.

```bash
npm install vitest --save-dev
```

## reproduce error

1. git clone project to windows `D:` drive
   * e.g. `git clone git@github.com:armbzk/vitest-error.git /d/gitea/armbzk/`
1. install vitest extension v1.8.1 in vscode
1. open `tests/dummy.test.mjs`
1. open vitest Testing explorer in vscode
1. browse to `tests -> dummy.test.mjs -> 'dummy tests' -> 'should exceed'`
1. Click `Debug test`

Output in DEBUG console:

```cmd
C:\Program Files\nodejs\node.EXE c:\Users\armbzk\.vscode\extensions\vitest.explorer-1.8.1\dist\worker.js
Process exited with code 1
```

Error message in vitest test explorer:

```log
Error: No test suite found in file D:/gitea/armbzk/vitest-update/tests/dummy.test.mjs
at runFiles (file:///digitea/armbzk/vitest-update/node_modules/@vitest/runner/dist/index.js:1254:11)
at startTests (file:///digitea/armbzk/vitest-update/node_modules/@vitest/runner/dist/index.js:1271:9)
at processTicksAndRejections (node:internal/process/task_queues:95:5)
at file:///digitea/armbzk/vitest-update/node_modules/vitest/dist/chunks/runBaseTests.3qpJUEJM.js:126:11
at withEnv (file:///d:/gitea/armbzk/vitest-update/node_modules/vitest/dist/chunks/runBaseTests.3qpJUEJM.js:90:5)
at run (file:///digitea/armbzk/vitest-update/node_modules/vitest/dist/chunks/runBaseTests.3qpJUEJM.js:112:3)
at runBaseTests (file:///d:/gitea/armbzk/vitest-update/node_modules/vitest/dist/chunks/base.BZZh4cSm.js:29:3)
at ForksBaseWorker.executeTests (file:///digitea/armbzk/vitest-update/node_modules/vitest/dist/workers/forks.js:27:7)
at execute (file:///d:/gitea/armbzk/vitest-update/node_modules/vitest/dist/workerjs:127:5)
at onMessage (file:///d:/gitea/armbzk/vitest-update/node_modules/tinypool/dist/entry/processjs:55:20)
```

## Notes

* Error only with `Debug test` - `Run test` succeeds without any error
* after copying the project to Windows `C:` drive `Debug test` works fine
* `npx vitest run` in console succeeds (also on `D:` drive)
