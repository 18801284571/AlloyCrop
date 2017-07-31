# Install

You can install it via npm:

```html
npm install alloycrop
```

## API

```js
new AlloyCrop({
    image_src: "img src",
    circle: true, // optional parameters , the default value is false
    width: 200, // crop width
    height: 100, // crop height
    output: 2, // output resolution --> 400*200
    ok: function (base64, canvas) { },
    cancel: function () { },
    ok_text: "yes", // optional parameters , the default value is ok
    cancel_text: "no" // optional parameters , the default value is cancel
});
```

## Demo

![./asset/alloy_crop.png](./asset/alloy_crop.png)
