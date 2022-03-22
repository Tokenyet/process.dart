# Process

[![Build Status -](https://travis-ci.org/google/process.dart.svg?branch=master)](https://travis-ci.org/google/process.dart)
[![Coverage Status -](https://coveralls.io/repos/github/google/process.dart/badge.svg?branch=master)](https://coveralls.io/github/google/process.dart?branch=master)

**This fork tweak windows, see [this issue](https://github.com/google/process.dart/issues/66)**

Can now use, `processManager.run(['tasklist | findstr svchost.exe'], runInShell: true);`.

**Also tweak Macos and Linux for using bin/bash instead of bin/sh**
So you don't need to write

```
await _processManager.run(
      ['bash', '-c', complexCommand],
      sanitize: false,
      runInShell: true,
      includeParentEnvironment: true,
    );
```

Just

```
await _processManager.run(
      [complexCommand],
      sanitize: false,
      runInShell: true,
      includeParentEnvironment: true,
    );
```

A generic process invocation abstraction for Dart.

Like `dart:io`, `package:process` supplies a rich, Dart-idiomatic API for
spawning OS processes.

Unlike `dart:io`, `package:process`:

- Can be used to implement custom process invocation backends.
- Comes with a record-replay implementation out-of-the-box, making it super
  easy to test code that spawns processes in a hermetic way.
