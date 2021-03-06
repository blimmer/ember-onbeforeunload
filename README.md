# ember-onbeforeunload
[![npm Version][npm-badge]][npm]
[![Build Status][travis-badge]][travis]

An addon to conditionally prompt the user when transitioning between routes or closing the browser.

## Implementing

```js
// app/controllers/foo.js
import Ember from 'ember';

export default Ember.Controller.extend({
  /*
  `isDirty` on the current route's controller
  is the property which determines whether or not to
  prompt a confirmation dialog.   Normally, this would be
  checking if the controller's model is dirty
  */
  isDirty: Ember.computed('model', function() {
    return this.get('model.isDirty')
  })
});
```

```js
// app/routes/foo.js
import Ember from 'ember';
import ConfirmationMixin from 'ember-onbeforeunload/mixins/confirmation';

export default Ember.Route.extend(ConfirmationMixin, {
  confirmationMessage(model) {
    const name = Ember.get(model, 'name');
    return `You have unsaved changes for ${name}, are you sure you want to continue?`;
  }
});
```

## Installation

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `npm test` (Runs `ember try:testall` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).

[npm]: https://www.npmjs.org/package/ember-onbeforeunload
[npm-badge]: https://img.shields.io/npm/v/ember-onbeforeunload.svg?style=flat-square
[travis]: https://travis-ci.org/jasonmit/ember-onbeforeunload
[travis-badge]: https://img.shields.io/travis/jasonmit/ember-onbeforeunload.svg?branch=master&style=flat-square
