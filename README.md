# vue-slidebars

## Usage
```html
<template>
    <div id="app">
        <SlideBars v-model="show" position="left">
            Put your menu here
        </SlideBars>
    </div>
</template>
```

```javascript
import SlideBars from "vue-slidebars";

export default {
    components: {
        SlideBars
    },
    data() {
        return {
            show: true
        }
    }
}
```

### Customize configuration

| Attribute      | Type    | Required | Default value | Note              |
|----------------|---------|----------|---------------|-------------------|
| value          | Boolean | yes      | false         |                   |
| width          | Number  |          | 340           |                   |
| bgColor        | String  |          | "#313131"     |                   |
| transitionTime | Number  |          | 300           | milliseconds      |
| position       | String  |          | "left"        | "left" or "right" |
