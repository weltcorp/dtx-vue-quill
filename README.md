# VueUpQuill

A Quill Editor for Vue 3 plugin or component.
<p>
  <a href="https://www.npmjs.com/package/@vueup/quill" title="Version">
    <img src="https://img.shields.io/npm/v/@vueup/quill?color=blue" alt="Version">
  </a>
  <a href="https://www.npmjs.com/package/@vueup/quill" title="Total downloads">
    <img src="https://img.shields.io/npm/dt/@vueup/quill" alt="Total downloads">
  </a>
  <a href="https://www.npmjs.com/package/@vueup/quill" title="License">
    <img src="https://img.shields.io/npm/l/@vueup/quill?color=orange" alt="License">
  </a>
  <a href="https://github.com/vueup/vueup-quill" title="Checks">
    <img src="https://img.shields.io/github/checks-status/vueup/vueup-quill/master?logo=github" alt="Checks">
  </a>
  <a href="https://github.com/vueup/vueup-quill" title="Last commit">
    <img src="https://img.shields.io/github/last-commit/vueup/vueup-quill?logo=github" alt="Last commit">
  </a>
 </p>

## Installation

Use the package manager [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/) to install VueUpQuill.

``` bash
npm install @vueup/quill --save
# OR
yarn add @vueup/quill
```

## Usage

### Mount with global

``` javascript
import { createApp } from 'vue'
import VueUpQuill from '@vueup/quill'
import '@vueup/quill/dist/quill.snow.css';

const app = createApp()
app.use(VueUpQuill, /* { default global options } */)

```

### Mount with local component

``` javascript
import { QuillEditor } from '@vueup/quill'
import '@vueup/quill/dist/quill.snow.css';

export default {
  components: {
    QuillEditor
  }
}

```

### SFC Implementation

``` vue
<template>
  <!-- Two-way Data-Binding -->
  <QuillEditor
    theme="snow"
    toolbar="default"
    :options="editorOption"
    v-model:content="content"
    @blur="onEditorBlur(editor)"
    @focus="onEditorFocus(editor)"
    @ready="onEditorReady(quill)"
    @textChange="onTextChange(...args)"
    @editorChange="onEditorChange(...args)"
    @selectionChange="onSelectionChange(...args)"
  />
</template>
```

## Themes

Quill features two offically supported themes: `snow` and `bubble` see [DEMO](https://vueup.github.io/vueup-quill/).
Themes primarily control the visual look of Quill through its CSS stylesheet, and many changes can easily be made by overriding these rules. At the very least, the `core` theme must be included for modules like toolbars or tooltips to work.

To activate a theme, import the stylesheet for the themes you want to use.
~~~ javascript
import '@vueup/quill/dist/quill.snow.css';
// OR | AND
import '@vueup/quill/dist/quill.bubble.css';
// you can use both themes at the same time and use them interchangeably
~~~

These stylesheets can be found in the Quill distribution, but for convenience they are also linked in VueUpQuill's `dist` folder.

Then, pass the name of the theme to the `theme` [prop](#props).

~~~ vue
<template>
  <QuillEditor theme="snow" .../>

  <!-- you can bind :theme="value" and it will automatically re render when its value change -->
  <QuillEditor :theme="value" .../>
  <button @click="value = 'snow'">Snow</button>
  <button @click="value = 'bubble'">Bubble</button>
</template>

<script>
  ...
</script>
~~~

## Toolbar
The Toolbar module allow users to easily format Quill’s contents. It can be configured with a toolbar prop.

### There are 3 ways to configure toolbar:

#### Pre-Configure Toolbar Options

VueUpQuill provides 3 pre-configured toolbar options `essential`, `minimal`, `full`, and `""` to use default options.

~~~ vue
<template>
  <QuillEditor toolbar="minimal" .../>
</template>
~~~

#### Custom Toolbar Options

You can also set your own options like this:

~~~ vue
<template>
  <QuillEditor :toolbar="['bold', 'italic', 'underline']" .../>
</template>
~~~

See [Quill toolbar docs](https://quilljs.com/docs/modules/toolbar/) for more details.

#### Custom Toolbar Container

~~~ vue
<template>
  <QuillEditor toolbar="#my-toolbar" ...>
    <template #toolbar>
      <div id="my-toolbar">
        <!-- Add buttons as you would before -->
        <button class="ql-bold"></button>
        <button class="ql-italic"></button>

        <!-- But you can also add your own -->
        <button id="custom-button"></button>
      </div>
    </template>
  </QuillEditor>
</template>
~~~

See [Quill toolbar docs](https://quilljs.com/docs/modules/toolbar/) for more details.

## API Refference 

### Export

~~~ javascript
// ES6
import VueUpQuill, {QuillEditor, Quill} from '@vueup/quill';

// CommonJS
const VueUpQuill = require('react-quill');
const {QuillEditor, Quill} = VueUpQuill;
~~~

### Props

**`content`** : Contents for the editor, Can be plain `string`, `html` or `Delta` object, see [Quill Delta docs](https://quilljs.com/docs/delta/) for more details.

**`enable`** : Set ability for user to edit, via input devices like the mouse or keyboard.

**`readOnly`** : If *true*, the editor won't allow changing its contents. Wraps the Quill [`disable` API](https://quilljs.com/docs/api/#disable). 

**`placeholder`** : The attribute to specifies a short hint that describes the expected value of an input field (e.g. a sample value or a short description of the expected format).

**`options`** : To configure Quill options see [the docs options](https://quilljs.com/docs/configuration/#options) for more details

**`theme`** :  The name of the theme to apply to the editor, Quill features two offically supported themes: `snow` and `bubble`. Pass `""` to use the minimal core theme. See the [docs on themes](https://quilljs.com/docs/themes/) for more information on including the required stylesheets. 

**`toolbar`** : Toolbar options to configure the default toolbar icons using an array of format names. [see above](##Toolbar)

### Events 

**`@textChange`** :

**`@selectionChange`** :

**`@editorChange`** :

**`@update:content`** :

**`@focus`** :

**`@blur`** :

**`@ready`** :

### Methods

**`getQuill`** :

**`getHTML`** :

**`setHTML`** :



## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Quill
[Quill API document](https://quilljs.com/docs/quickstart/)

## License
[MIT](https://choosealicense.com/licenses/mit/)
