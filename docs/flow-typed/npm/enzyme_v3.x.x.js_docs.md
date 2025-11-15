# Documentation: flow-typed/npm/enzyme_v3.x.x.js

## File Metadata

- **Path**: `flow-typed/npm/enzyme_v3.x.x.js`
- **Type**: .js
- **Size**: 4883 bytes (4.77 KB)
- **Lines**: 143
- **Last Modified**: 2025-11-15T20:36:35.082367

## Source Code

```javascript
// flow-typed signature: 931d5482afcb022bcbddb841fd08d683
// flow-typed version: 5175c53189/enzyme_v3.x.x/flow_>=v0.104.x

declare module "enzyme" {
  declare type PredicateFunction<T: Wrapper<*>> = (
    wrapper: T,
    index: number
  ) => boolean;
  declare type UntypedSelector = string | { [key: string]: number|string|boolean, ... };
  declare type EnzymeSelector = UntypedSelector | React$ElementType;

  // CheerioWrapper is a type alias for an actual cheerio instance
  // TODO: Reference correct type from cheerio's type declarations
  declare type CheerioWrapper = any;

  declare class Wrapper<RootComponent> {
    equals(node: React$Element<any>): boolean,
    find(selector: UntypedSelector): this,
    find<T: React$ElementType>(selector: T): ReactWrapper<T>,
    findWhere(predicate: PredicateFunction<this>): this,
    filter(selector: UntypedSelector): this,
    filter<T: React$ElementType>(selector: T): ReactWrapper<T>,
    filterWhere(predicate: PredicateFunction<this>): this,
    hostNodes(): this,
    contains(nodes: React$Node): boolean,
    containsMatchingElement(node: React$Node): boolean,
    containsAllMatchingElements(nodes: React$Node): boolean,
    containsAnyMatchingElements(nodes: React$Node): boolean,
    dive(option?: { context?: Object, ... }): this,
    exists(selector?: EnzymeSelector): boolean,
    isEmptyRender(): boolean,
    matchesElement(node: React$Node): boolean,
    hasClass(className: string): boolean,
    is(selector: EnzymeSelector): boolean,
    isEmpty(): boolean,
    not(selector: EnzymeSelector): this,
    children(selector?: UntypedSelector): this,
    children<T: React$ElementType>(selector: T): ReactWrapper<T>,
    childAt(index: number): this,
    parents(selector?: UntypedSelector): this,
    parents<T: React$ElementType>(selector: T): ReactWrapper<T>,
    parent(): this,
    closest(selector: UntypedSelector): this,
    closest<T: React$ElementType>(selector: T): ReactWrapper<T>,
    render(): CheerioWrapper,
    renderProp(propName: string): (...args: Array<any>) => this,
    unmount(): this,
    text(): string,
    html(): string,
    invoke(propName: string): (...args: $ReadOnlyArray<any>) => mixed,
    get(index: number): React$Node,
    getDOMNode(): HTMLElement | HTMLInputElement,
    at(index: number): this,
    first(): this,
    last(): this,
    state(key?: string): any,
    context(key?: string): any,
    props(): Object,
    prop(key: string): any,
    key(): string,
    simulate(event: string, ...args: Array<any>): this,
    simulateError(error: Error): this,
    slice(begin?: number, end?: number): this,
    setState(state: {...}, callback?: () => void): this,
    setProps(props: {...}, callback?: () => void): this,
    setContext(context: Object): this,
    instance(): React$ElementRef<RootComponent>,
    update(): this,
    debug(options?: Object): string,
    type(): string | Function | null,
    name(): string,
    forEach(fn: (node: this, index: number) => mixed): this,
    map<T>(fn: (node: this, index: number) => T): Array<T>,
    reduce<T>(
      fn: (value: T, node: this, index: number) => T,
      initialValue?: T
    ): Array<T>,
    reduceRight<T>(
      fn: (value: T, node: this, index: number) => T,
      initialValue?: T
    ): Array<T>,
    some(selector: EnzymeSelector): boolean,
    someWhere(predicate: PredicateFunction<this>): boolean,
    every(selector: EnzymeSelector): boolean,
    everyWhere(predicate: PredicateFunction<this>): boolean,
    length: number
  }

  declare class ReactWrapper<T> extends Wrapper<T> {
    constructor(nodes: React$Element<T>, root: any, options?: ?Object): ReactWrapper<T>,
    mount(): this,
    ref(refName: string): this,
    detach(): void
  }

  declare class ShallowWrapper<T> extends Wrapper<T> {
    constructor(
      nodes: React$Element<T>,
      root: any,
      options?: ?Object
    ): ShallowWrapper<T>,
    equals(node: React$Node): boolean,
    shallow(options?: { context?: Object, ... }): ShallowWrapper<T>,
    getElement(): React$Node,
    getElements(): Array<React$Node>
  }

  declare function shallow<T>(
    node: React$Element<T>,
    options?: {
      context?: Object,
      disableLifecycleMethods?: boolean,
      ...
    }
  ): ShallowWrapper<T>;
  declare function mount<T>(
    node: React$Element<T>,
    options?: {
      context?: Object,
      attachTo?: HTMLElement,
      childContextTypes?: Object,
      ...
    }
  ): ReactWrapper<T>;
  declare function render(
    node: React$Node,
    options?: { context?: Object, ... }
  ): CheerioWrapper;

  declare module.exports: {
    configure(options: {
      Adapter?: any,
      disableLifecycleMethods?: boolean,
      ...
    }): void,
    render: typeof render,
    mount: typeof mount,
    shallow: typeof shallow,
    ShallowWrapper: typeof ShallowWrapper,
    ReactWrapper: typeof ReactWrapper,
    ...
  };
}

```

## High-Level Overview

This JavaScript/TypeScript file (`enzyme_v3.x.x.js`) defines 3 class(es): Wrapper, ReactWrapper, ShallowWrapper. It contains 3 function(s). 

## Detailed Analysis

### Structure

**Classes** (3): Wrapper, ReactWrapper, ShallowWrapper

**Functions** (3): shallow, mount, render



### Components and Functions

#### Functions

**`shallow()`**

Function defined in this file.

**`mount()`**

Function defined in this file.

**`render()`**

Function defined in this file.

#### Classes

**`Wrapper`**: Class defined in this file.

**`ReactWrapper`**: Class defined in this file.

**`ShallowWrapper`**: Class defined in this file.



### Dependencies

No external dependencies detected.

## Usage Examples

Refer to other files in the repository for usage examples.

## Related Files

Related files can be found by examining:

- Files in the same directory: `flow-typed/npm/`


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:41.104120Z*
