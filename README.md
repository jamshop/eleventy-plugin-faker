# Eleventy Plugin - Faker

Generate collections fake data. 

Install:

```
npm install @jamshop/eleventy-plugin-faker
```

## Usage

In you main config `.eleventy.js`: 

```js
const pluginFaker = require("@jamshop/eleventy-plugin-faker");

module.exports = (eleventyConfig) => {
  eleventyConfig.addPlugin(pluginFaker, {
    seed, // Use this to generate the same data between builds
    locale, // Localise the faker.js data
    collections // Array of collections
  });
  // and the rest of your config
};
```

### Collections
```js
[{ 
  name: "people", // name of collection
  template: personTemplate, // A mustache template that returns JSON
  items: 20 // number of items to generate
}]

const personTemplate = `{
  first_name: "{{name.firstName}}",
  last_name: "{{name.lastName}}",
}`;
```

See: https://github.com/marak/Faker.js/#fakerfake for more details of what can go in templates.

Additionally includes all faker methods as a shortcode incase you just need to quickly insert some fake data into a template. Eg. Nunjucks:

```
{% faker_name_firstName %}
```

Is equivlent to `faker.name.firstName()`. Full API details: https://github.com/Marak/faker.js/blob/master/Readme.md

