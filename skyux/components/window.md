# Development

               Skip to Main Content

 Window
======

The application window reference service references the global `window` variable. After users inject `SkyAppWindowRef` into a component, they can use the service to interact with `window` properties and event handlers by referencing its `nativeWindow` property. For more information, see the [window API documentation on MDN web docs](https://developer.mozilla.org/en-US/docs/Web/API/Window).

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/window/window-ref.ts#L18) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyAppWindowRef
----------------

Type: Service

The application window reference service references the global window variable. After users inject SkyAppWindowRef into a component, they can use the service to interact with window properties and event handlers by referencing its nativeWindow property.

### Properties

#### `nativeWindow: any`

The global `window` variable.