# Image Inline Component

The `imageInline` component provides placeholder and uploader features for inline images.

- [x] Image placeholder
- [x] Image upload
- [x] Image link input

> The component itself doesn't provide any styling.
>
> You need to write your own CSS to style it.

# Usage

```typescript
import { defaultValueCtx, Editor } from '@milkdown/kit/core';
import { commonmark } from '@milkdown/kit/preset/commonmark';
import { imageInlineComponent } from '@milkdown/kit/component/image-inline'

await Editor
  .make()
  .use(commonmark)
  .use(imageInlineComponent)
  .create()
```

::iframe{src="https://stackblitz.com/github/Milkdown/examples/tree/main/component-image-inline"}

---

# Configuration

You can configure the component by updating the `inlineImageConfig` ctx in `editor.config`.

The possible configurations are:

### `onUpload`

A function that is called when the image is chosen by the file picker.

You should return a promise that resolves to the URL of the uploaded image.

```typescript
import { inlineImageConfig } from '@milkdown/kit/component/image-inline'

ctx.update(inlineImageConfig.key, defaultConfig => ({
  ...defaultConfig,
  onUpload: async (file: File) => {
    const url = await YourUploadAPI(file);

    return url;
  }
}))
```

### `imageIcon`

The icon shown in the empty inline image placeholder.

The value can be a function that returns:

- A string
- A DOM element
- An HTML template created by `html`.

```typescript
import { inlineImageConfig } from '@milkdown/kit/component/image-inline'

ctx.update(inlineImageConfig.key, defaultConfig => ({
  ...defaultConfig,
  imageIcon: () => '🖼️'
}))
```

### `uploadButton`

The text shown in the upload button.

The value can be a function that returns:

- A string
- A DOM element
- An HTML template created by `html`.

```typescript
import { inlineImageConfig } from '@milkdown/kit/component/image-inline'

ctx.update(inlineImageConfig.key, defaultConfig => ({
  ...defaultConfig,
  uploadButton: () => 'Upload'
}))
```

### `uploadPlaceholderText`

The placeholder text for the upload button.

The value should be a string.

```typescript
import { inlineImageConfig } from '@milkdown/kit/component/image-inline'

ctx.update(inlineImageConfig.key, defaultConfig => ({
  ...defaultConfig,
  uploadPlaceholderText: 'Paste URL'
}))
```

### `confirmButton`

The text shown in the confirm button.

The value can be a function that returns:

- A string
- A DOM element
- An HTML template created by `html`.

```typescript
import { inlineImageConfig } from '@milkdown/kit/component/image-inline'

ctx.update(inlineImageConfig.key, defaultConfig => ({
  ...defaultConfig,
  confirmButton: () => 'Confirm'
}))
```