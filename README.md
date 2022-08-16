# ionic-lab
Creates a mock template similar to ionic lab, but actually applies the iOS mode and styles by passing a `mode` query parameter to the displayed application. This means that on the application setup side you should do the following

## Vue
```javascript
const mode = new URL(document.location.href).searchParams.get('mode') || 'md';

const app = createApp(App)
  .use(IonicVue, {
    rippleEffect: false,
    mode
  })
  .use(router);
```

## React
```javascript
const mode = new URL(document.location.href).searchParams.get('mode') || 'md';

setupIonicReact({
  rippleEffect: false,
  mode,
});
```


# Install
```bash
yarn
```

# Run
```bash
yarn serve
```
