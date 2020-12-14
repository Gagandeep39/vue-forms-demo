# Vue Forms

- [Vue Forms](#vue-forms)
  - [Deployment](#deployment)
  - [Checkboxs](#checkboxs)

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
