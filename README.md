# bare-stdio

Standard input/output streams for Bare.

```
npm i bare-stdio
```

## Usage

```js
const stdio = require('bare-stdio')

// Write to stdout
stdio.out.write('Hello, World!\n')

// Write to stderr
stdio.err.write('An error occurred\n')

// Read from stdin
stdio.in.on('data', (data) => {
  console.log('Received:', data.toString())
})
```

<!-- bare-refgen:api start -->

## API

### Constants and variables

#### `io: IO`

The standard I/O streams: `in` — a readable stream for standard input (fd `0`), `out` — a writable stream for standard output (fd `1`), and `err` — a writable stream for standard error (fd `2`). Each is created lazily on first access: a `bare-tty` stream if the file descriptor is a terminal, a `bare-pipe` `Pipe` if it's a pipe, otherwise a `bare-fs` stream.

### Types

#### `IO`

```ts
interface IO {
  readonly in: TTYReadStream | Pipe | FileReadStream
  readonly out: TTYWriteStream | Pipe | FileWriteStream
  readonly err: TTYWriteStream | Pipe | FileWriteStream
}
```

<!-- bare-refgen:api end -->

## License

Apache-2.0
