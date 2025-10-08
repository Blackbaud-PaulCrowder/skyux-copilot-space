            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Public API](/skyux/learn/develop/public-api.md)

Public API
==========

SKY UX consists of a broad array of public APIs in the form of Angular components, directives, pipes, and services as well as CSS classes and custom properties. We make every effort to hide parts of SKY UX that are not intended for public consumers using the appropriate mechanisms (private TypeScript members, closures, Angular view encapsulation, scoped CSS custom properties, etc.). However, due to the nature of Angular, JavaScript, and CSS, some parts of SKY UX only meant for internal use can still be accessed by public consumers.

The purpose of this document is to describe what is and is not part of the supported public API. The supported API is guaranteed to not change with a minor or patch version, while publicly-accessible but unsupported APIs are subject to change with a minor or patch version and could cause your application to break if you reference them directly.

The public API consists of the following:

*   Components, directives, pipes, and services documented in [Components](/skyux/components.md).
*   CSS classes and custom properties documented in [Design](/skyux/design.md).

The following are not part of the supported public API and are subject to change in minor or patch versions:

*   Any exported type or public properties or methods of any component, directive, pipe, or service not documented in [Components](/skyux/components.md).
*   CSS classes, CSS custom properties, or SCSS variables not documented in [Design](/skyux/design.md).
*   Properties or methods of any component, directive, pipe, or service marked as `private`.
*   Service constructors. If you need an instance of a SKY UX service in a unit test, use `TestBed.inject()`. If you need to mock a service, do not inherit it because changes to the constructor will break your mock. Instead, use your own class or an object literal that has the same shape as the service you are mocking, and only implement properties and methods that are documented as part of the public API.
*   Any type prefixed with the Latin lambda character (`λ`). These types are only exported because Angular requires them to be exported.
*   The internal DOM structure of SKY UX components for uses including (but not limited to) the following:
    *   Styling internal elements using `::ng-deep`. Use the component's inputs or documented CSS classes instead.
    *   Manipulating elements inside a component programmatically. Use the component's inputs instead.
    *   Writing selectors in unit tests to validate or interact with a component. Use the component's test harness instead.

[

Breaking changes in major versions
----------------------------------

](/skyux/learn/develop/public-api#breaking-changes-in-major-versions.md)

While we make every effort to maintain compatibility between major versions of SKY UX, sometimes it is necessary to change the public API in a way that causes consumers to change their code. Breaking changes are noted as such in the [SKY UX changelog](https://github.com/blackbaud/skyux/blob/main/CHANGELOG.md). SKY UX follows [semantic versioning rules](https://semver.org/), so breaking changes are only made in major version updates.