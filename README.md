# image-screenshot

> :camera: targets at **browser** only

## Why Not Right Click and Save

Because in that way the CSS properties added to the image will be lost

There is a more famous library, [html2canvas](https://github.com/niklasvh/html2canvas), that provides the utility of converting the DOM nodes into a picture, but it [does NOT add along with the CSS properties to the pictures](https://github.com/niklasvh/html2canvas/issues/1127).

## Usage

```js
import screenshot from 'image-screenshot'

const img = document.getElementById('my-img')

screenshot(img).then((url) => {
  console.log('the base64 data url of the image is:', url)
})
```

even more, you could do:

```js
// it will automatically download the image for you
screenshot(img).download()
```

Other than those, there is a helper function `download` that you could use elsewhere, after you get the base64 url:

```js
import { download } from 'image-screenshot'

download(url, 'image.jpeg')  // the image will be downloaded into `image.jpeg` 
```

## APIs

- `screenshot(img: DOMNode, format: string)`: get the base64 url in a specific format, which is by default `png`. Returns a thenable object:

```js
{
  url,  // get the url through screenshot().url
  then: callback,
  download: (downloadFileName: string) => void // defaults to 'image.${format}'
}
```

- `download(url: string, fullName: string)` (Note that this is different from the `download` function returned from `screenshot`)

## Who is Using `image-screenshot`

- [CSS-filter](https://cyan33.github.io/css-filter/)
