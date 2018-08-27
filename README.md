# simple-thumbnail 

A minimal library that produces a thumbnail image from a video's first frame using `ffmpeg`.

## Installation

```bash
$ yarn add simple-thumbnail

# Or,

$ npm install simple-thumbnail --save
```

## Usage

```js
const thumbnail = require('simple-thumbnail')

// promise
genThumbnail('path/to/video.webm', 'output/file/path.png', '250x?')
  .then(() => console.log('done!'))
  .catch(err => console.error(err))

// async/await
(async () => {
  try {
    await genThumbnail('http://www.example.com/foo.webm', 'output/file/path.png', '250x?')
    console.log('Done!')
  } catch (err) {
    console.error(err)
  }
})()
```

## API

#### genThumbnail(input, output, size)

Returns of a `Promise` which resolves on thumbnail creation.

#### input

Type: `String | stream.Readable`

The URL, file path, or read-stream of a video.

#### output

Type: `String`

The file path of the generated thumbnail, assumes directories exists.

#### size

Type: `String`

The dimensions of the generated thumbnail. The `size` argument may have one of the following formats:

* `150x100`: set a fixed output size.
* `150x?`: set a fixed width and compute the height automatically.
* `?x100`: set a fixed height and compute the width automatically.
* `50%`: rescale both width and height to given percentage.
