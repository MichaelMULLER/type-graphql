# Changelog and release notes

## Unreleased
<!-- here goes all the unreleased changes descriptions -->
### Features
- **Breaking Change**: emit in schema only types actually used by provided resolvers classes (#415)
- **Breaking Change**: update `graphql-js` peer dependency to `^14.5.4`

### Fixes
- refactor union types function syntax handling to prevent possible errors with circular refs

## v0.17.5
### Features
- rename `DepreciationOptions` interface to `DeprecationOptions` and deprecate the old one
- update deps to newest minor versions (`tslib`, `semver`, `graphql-query-complexity` and `glob`)
- support nested array types (`@Field(type => [[Int]])`) (#393)
- deprecate the direct array syntax for union types

### Fixes
- fix errors on circular refs in union types (#364) by adding the function syntax (`() => TClassTypes`)

## v0.17.4
### Features
- add support for creating custom parameter decorators (#329)
- allow to provide custom `subscribe` function in `@Subscription` decorator (#328)

## v0.17.3
### Features
- update packages `semver` to `^6.0.0` and `graphql-subscriptions` to `^1.1.0` 
### Fixes
- fix broken compatibility with newer `@types/graphql` due to using removed private types (e.g. `MaybePromise`) (#320)

## v0.17.2
### Features
- add support for defining `resolveType` function for interfaces and unions (#319)
- add support for setting default nullability for fields and return types (#297)
- add `skipCheck` option in `buildSchema` to disable checking the correctness of a schema
- add postinstall script for printing info on console about supporting the project
### Fixes
- fix generating plain resolvers for queries and mutations (compatibility with Apollo client state)

## v0.17.1
### Features
- add support for emitting schema file in not existing directory (#269)
- drop support for Node.js v6 (end of LTS in April 2019)
### Fixes
- fix typings discovery support for WebStorm (#276)
- allow for returning plain objects when using `ObjectType`s that implements `InterfaceType`s or extends other classes (#160)

## v0.17.0
### Features
- **Breaking Change**: make `graphql-js` packages a peer dependencies, bump `graphql` to `^14.1.1` and `@types/graphql` to `^14.0.7` (#239)
- **Breaking Change**: remove `useContainer` function and allow to register container by `buildSchema` options (#241)
- **Breaking Change**: change the default `PrintSchemaOptions` option `commentDescriptions` to false (no more `#` comments in SDL)
- add support for passing `PrintSchemaOptions` in `buildSchema.emitSchemaFile` (e.g. `commentDescriptions: true` to restore previous behavior)
- add `buildTypeDefsAndResolvers` utils function for generating apollo-like `typeDefs` and `resolvers` pair (#233)
- add support for generic types (#255)
### Fixes
- **Breaking Change**: remove the `formatArgumentValidationError` helper as it's not compatible and not needed in new Apollo Server (#258)
- fix calling return type getter function `@Field(type => Foo)` before finishing module evaluation (allow for extending circular classes using `require`)
- fix nullifying other custom method decorators - call the method on target instance, not the stored reference to original function (#247)
- fix throwing error when extending non args class in the `@ArgsType()` class
- prevent unnecessary conversion of an object that is already an instance of the requested type (avoid constructor side-effects)

## v0.16.0
### Features
- add support for default values in schema (#203)
- add support for lists with nullable items (#211)
### Fixes
- fix browser shim (compatibility with polyfills for decorator support)

## v0.15.0
### Features
- **Breaking Change**: upgrade `graphql` to `^14.0.2`, `graphql-subscriptions` to `^1.0.0` and `@types/graphql` to `^14.0.2`
- update all other dependencies
- drop support for Node.js v9
- add capability to emit the schema definition file (*.gql) as a `buildSchema` option
- add `emitSchemaDefinitionFile` helper function for emitting the schema SDL

## v0.14.0
### Features
- **Breaking Change**: change `ClassType` type and export it in package index
- **Breaking Change**: refactor generic `createUnionType` to remove the 10 types limit (note: requires TypeScript >=3.0.1)
- add support for subscribing to dynamic topics - based on args/ctx/root (#137)
- add support for query complexity analysis - integration with `graphql-query-complexity` (#139)

## v0.13.1
### Fixes
- fix missing loosely typed overload signature for `createUnionType` (remove the 10 types limit)

## v0.13.0
### Features
- make `class-validator` a virtual peer dependency and update it to newest `0.9.1` version
- add support for creating scoped containers (#113)

## v0.12.3
### Features
- add reflect-metadata checks and informative error if no polyfill provided
- update `@types/graphql` to latest version (`^0.13.3`)
### Fixes
- fix throwing error when `of => objectType` wasn't provided in abstract resolver class
- fix calling `Object.assign` with boolean arguments (#111)

## v0.12.2
### Features
- add support for using type classes in browser (configure webpack to use decorators shim)
### Fixes
- fix swallowing false argument value (#101)

## v0.12.1
### Fixes
- fix bug with overriding methods from parent resolver class (#95)

## v0.12.0
### Features
- **Breaking Change**: remove deprecated `ActionData` and `FilterActionData` interfaces
- add support for resolver classes inheritance
- add `name` decorator option for `@Field` and `@FieldResolver` decorators that allows to set the schema name different than the property name

## v0.11.3
### Features
- make auth checker feature generic typed (default `string` for backward compatibility)

## v0.11.2
### Features
- attach `MetadataStorage` to global scope (support multiple packages/modules)
- rename and deprecate `ActionData` and `FilterActionData` interfaces to `ResolverData` and `ResolverFilterData`

## v0.11.1
### Features
- add support for returning null instead of throwing authorization error (`authMode` property of `buildSchema` config)
- add support for generating object type field in schema from method with `@FieldResolver`
### Fixes
- fix bug when converting object scalars to target class instance (#65)

## v0.11.0
### Features
- add support for creating and attaching middlewares, guards and interceptors to fields and resolvers
- **Breaking Change**: remove deprecated decorators with `GraphQL` prefix and `{ array: true }` type option

## v0.10.0
### Features
- add `buildSchemaSync` function to build the schema synchronously (unsafe! without additional errors checks)
- update package dependencies
- **Breaking Change**: update `@types/graphql` to `0.13.0`
### Fixes
- decorator option `validate` is now merged with `buildSchema`'s `validate` config instead of overwriting it

## v0.9.1
### Fixes
- fix bug with extending non-TypeGraphQL classes

## v0.9.0
### Features
- add support for GraphQL subscriptions using `graphql-subscriptions`
- update package dependencies
- deprecate `{ array: true }` type option

## v0.8.1
### Features
- add `@Info()` decorator for injecting GraphQL resolve info to resolvers
- add support for injecting parts of `root` and `context` objects with `@Root("field")` and `@Ctx("field")` decorators

## v0.8.0
### Features
- add base support for GraphQL enums using TypeScript enums
- add support for defining GraphQL unions
- add support for importing resolvers from file path glob
- deprecate decorators with `GraphQL` prefix - use `@ArgsType`, `@InputType`, `@InterfaceType`, `@ObjectType` and `@Resolver` instead
### Fixes
- fix not working array type notation in circular dependencies (correct thunk generation)

## v0.7.0
### Features
- add authorization feature - `@Authorized` decorator and `authChecker` function in schema options ([see docs](https://github.com/MichalLytek/type-graphql/blob/master/docs/authorization.md))
- add support for defining array type using mongoose-like notation `[Type]`
- **Breaking Change**: remove deprecated `@GraphQLArgumentType` decorator - use `@GraphQLArgsType` instead

## v0.6.0
### Features
- add support for defining GraphQL interfaces and implementing it by object types
- add support for extending input, args, object and interface types classes
- add support for implementing GraphQL interfaces without decorators duplication
- **Breaking Change**: make `buildSchema` async - now it returns a Promise of `GraphQLSchema`
- rename and deprecate `@GraphQLArgumentType` decorator - use `@GraphQLArgsType` instead
### Fixes
- allow for no args in `@GraphQLResolver` decorator to keep consistency with other resolver classes

## v0.5.0
### Features
- create instance of root object when it's type provided in resolver
- change `Date` scalar names to `GraphQLISODateTime` and `GraphQLTimestamp`
- support only `Date` objects (instances) serialization in `GraphQLTimestamp` (and in `GraphQLISODateTime` too)
- update package dependencies
- add test suite with 92%+ coverage
### Fixes
- **Breaking change**: switch array `nullable` option behavior from `[Type]!` to `[Type!]`
- add more detailed type reflection error message (parameters support)
- fix `ResolverInterface` resolver function type (allow additional parameters)
- add support for named param in `@GraphQLResolver` lambda and for object class as param

## v0.4.0
### Features
- add basic support for automatic arguments and inputs validation using `class-validator`
- add interface `ResolverInterface` for type checking of resolver class methods (field resolvers)
- update `graphql` dependency from `^0.12.3` to `^0.13.0`
### Fixes
- fix default values for arg/input fields (class property initializers) - use `new` instead of `Object.create`

## v0.3.0
### Features
- add support for descriptions in schema (types, args, queries, etc.)
- add support for declaring deprecation reason on object fields and queries/mutations
### Fixes
- fix scalars ID alias (GraphQLID not GraphQLString)

## v0.2.0
### Features
- add support for Date type (built-in scalar)
- add support for custom scalars (and mapping it to TS types)
- change `@Context` decorator name to `@Ctx`

## v0.1.2
### Fixes
- fix missing type args in schema when declared in field resolver
- fix missing resolver function when defined as type field method
- fix creating instances of root object when internal fields are Promises (switch from `plainToClass` to vanilla JS)
- fix converting field and resolvers args errors while converting gql objects (weird `prototype` stuffs)

## v0.1.1
### Features
- add support for omitting return type when use type options, in selected decorators (`@Field`, `@Arg`)
### Fixes
- fix class getter resolvers bug - missing fields from prototype (`plainToClass` bug)

## v0.1.0
### Initial release
