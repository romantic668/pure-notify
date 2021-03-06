# pure-notify

Pure-notify is a javascript notify component without any dependencies such as jquery, react or angular.

## Install

First, install via npm

````bash
$ npm install --save pure-notify
````

then, add to your html file the following code

````html
<script src="/node_modules/pure-notify/dist/pure-notify.min.js"></script>
<link rel="stylesheet" href="/node_modules/pure-notify/dist/pure-notify.min.css" />
````

## Usage

````js

PureNotify.success('Success message!'); 
// same as 
PureNotify.success({ title: 'Success message!' });

// get instance
let errorNotify = PureNotify.error({
  title: 'Success message',
  content: 'More detail description',
  timeout: 0   // set timeout to 0 to disable auto close. default timeout is 4000
});
// update instance
PureNotify.update(errorNotify, {
  title: 'Title changed!'
  content: 'content changed!'
});
// close instance
PureNotify.close(errorNotify);

````

## API

#### setDefaultOptions

````js
PureNotify.setGlobalOptions({
  transitionTime: 600,   // default transition time
  timeout: 4000,         // default timeout, set to 0 means no timeout
  template: `<div class="pure-notify {type}"><div class="title">{title}</div><div class="content">{content}</div><div class="close"></div></div>`,
  className: ''
});
````

#### success/error/warn/info

````js
let notifyIntance = PureNotify.success/error/warn/info({
  title: 'Title',
  content: 'Content',
  timeout: 4000,      // timeout to auto close notify, set to 0 means no timeout
  template: '',       // custom template
  className: ''       // custom container class
});
````

#### update

````js
PureNotify.update(notifyIntance, {
  title: 'Title',
  content: 'Content',
  timeout: 4000,      // timeout to auto close notify, set to 0 means no timeout
  template: '',       // custom template
  className: ''       // custom container class
});
````

`notifyIntance` parameter is pure-notify instance returned from `PureNotify.success/error/warn/info`

once having updated notify instance, previous timeout will be cleaned and new timeout applied

#### close

````js
PureNotify.close(notifyInstance);
````

if notify's timeout is 0, it won't be auto closed; You need to use `PureNotify.close` to close it.


## Custom Theme

you can just use `options.className` to add custom class to notify container DOM. for example,

````js
PureNotify.info({
  title: 'Hello',
  content: 'World',
  className: 'custom-notify-container'
})
````

The code above will generate below html:

````html
<div class="pure-notify-container custom-notify-container">
  <div class="pure-notify info">
    <div class="title">Hello</div>
    <div class="content">World</div>
    <div class="close"></div>
  </div>
</div>
````

then, you can use css to override its theme.

You can use `options.template` to customize html structure. for example:

````js
PureNotify.error({
  title: 'Hello',
  content: 'World',
  template: '<div class="my-notify-{type}">{title}:{content}</div>',
  className: 'custom-notify-container'
})
````

The code above will generate below html:

````html
<div class="pure-notify-container custom-notify-container">
  <div class="my-notify-error">Hello:World</div>
</div>
````





