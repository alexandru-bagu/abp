# How to Insert Scripts and Styles

You can use the `DomInsertionService` in @abp/ng.core package in order to insert scripts and styles in an easy and explicit way.


## Getting Started

You do not have to provide the `DomInsertionService` at module or component level, because it is already **provided in root**. You can inject and start using it immediately in your components, directives, or services.

```js
import { DomInsertionService } from '@abp/ng.core';

@Component({
  /* class metadata here */
})
class DemoComponent {
  constructor(private domInsertionService: DomInsertionService) {}
}
```

## Usage

You can use the `insertContent` method of `DomInsertionService` to create a `<script>` or `<style>` element with given content in the DOM at the desired position.


### How to Insert Scripts

The first parameter of `insertContent` method expects a `ContentStrategy`. If you pass a `ScriptContentStrategy` instance, the `DomInsertionService` will create a `<script>` element with given `content` and place it in the designated DOM position.

```js
import { DomInsertionService, CONTENT_STRATEGY } from '@abp/ng.core';

@Component({
  /* class metadata here */
})
class DemoComponent {
  constructor(private domInsertionService: DomInsertionService) {}

  ngOnInit() {
    this.domInsertionService.insertContent(
      CONTENT_STRATEGY.AppendScriptToBody('alert()')
    );
  }
}
```

In the example above, `<script>alert()</script>` element will place at the **end** of `<body>`.

Please refer to [ContentStrategy](./Content-Strategy.md) to see all available content strategies and how you can build your own content strategy.


### How to Insert Styles

If you pass a `StyleContentStrategy` instance as the first parameter of `insertContent` method, the `DomInsertionService` will create a `<style>` element with given `content` and place it in the designated DOM position.

```js
import { DomInsertionService, CONTENT_STRATEGY } from '@abp/ng.core';

@Component({
  /* class metadata here */
})
class DemoComponent {
  constructor(private domInsertionService: DomInsertionService) {}

  ngOnInit() {
    this.domInsertionService.insertContent(
      CONTENT_STRATEGY.AppendStyleToHead('body {margin: 0;}')
    );
  }
}
```

In the example above, `<style>body {margin: 0;}</style>` element will place at the **end** of `<head>`.

Please refer to [ContentStrategy](./Content-Strategy.md) to see all available content strategies and how you can build your own content strategy.


## API


### inserted

```js
inserted: Set<string>
```

All previously inserted contents are stored via this property as hashes. It is a simple [JavaScript Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set).



### insertContent

```js
insertContent(strategy: ContentStrategy): void
```

`strategy` parameter is the primary focus here and is explained above.


## What's Next?

- [TrackByService](./Track-By-Service.md)