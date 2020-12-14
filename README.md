# Vue Forms

- [Vue Forms](#vue-forms)
  - [Deployment](#deployment)
  - [Checkboxs](#checkboxs)
  - [v-models in custom form control](#v-models-in-custom-form-control)

## Deployment

- Check deployment at

## Checkboxs

- If we have multiple checkboes with same name, we can use an array to fetch values

```html
<div class="form-control">
  <h2>What are you interested in?</h2>
  <div>
    <input
      id="interest-news"
      name="interest"
      value="news"
      type="checkbox"
      v-model="interest"
    />
    <label for="interest-news">News</label>
  </div>
  <div>
    <input
      id="interest-tutorials"
      name="interest"
      value="tutorials"
      type="checkbox"
      v-model="interest"
    />
    <label for="interest-tutorials">Tutorials</label>
  </div>
  <div>
    <input
      id="interest-nothing"
      name="interest"
      value="nothing"
      type="checkbox"
      v-model="interest"
    />
    <label for="interest-nothing">Nothing</label>
  </div>
</div>
```

```js
export default {
  data() {
    return {
      interest: []
    };
  }
};
```

- If we have a single checkbox, well use `interest: false`, as it will return true/false value

## v-models in custom form control

- Vue sets prop named `modelValue` for us
- When inut value changes, vue emits an event `update:modelValue`
- Vue does 2 things for us
  - `:model-value:""`
  - `@update:modelValue=""`
- We can then update data by emitting event with data using `this.$emit('update:modelValue', data);`

```vue
<!-- Custom form control -->
<template>
  <ul>
    <li :class="{ active: modelValue === 'poor' }">
      <button type="button" @click="activate('poor')">Poor</button>
    </li>
    <li :class="{ active: modelValue === 'average' }">
      <button type="button" @click="activate('average')">Average</button>
    </li>
    <li :class="{ active: modelValue === 'great' }">
      <button type="button" @click="activate('great')">Great</button>
    </li>
  </ul>
</template>
<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue'],
  methods: {
    activate(option) {
      this.activeOption = option;
      this.$emit('update:modelValue', option);
    }
  }
};
</script>
```

```html
<!-- Using above element -->
<div class="form-control">
  <rating-control v-model="rating"></rating-control>
</div>
```
