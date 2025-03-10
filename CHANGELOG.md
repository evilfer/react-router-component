# CHANGELOG

## 0.27.2
  - Switch Object.assign shims, 'object.assign' uses eval()

## 0.27.1
  - Bugfixes for `urlPatternOptions`, which was not properly being passed to `matchRoutes` in some cases.
  - `urlPatternOptions` now propagates down the contextual router hierarchy.
  - Added additional tests for `urlPatternOptions`.

## 0.27.0
  - Breaking Changes (see also 0.27.0-rc1 changelog):
    * Support for React 0.14.0 only.
    * `url-pattern` `0.10` brought breaking updates. If you are customizing `url-pattern`, there is a new API:
      - `createURLPatternCompiler()` and `setCreateURLPatternCompilerFactory()` have been removed.
      - Instead, pass an object at the prop `urlPatternOptions` on either your router or individual routes.
        Route-level options will be merged with precedence over Router options. Contextual router options
        are not merged between levels.
    * `matchKeys` has been deprecated. `url-pattern` now handles this natively; pass an array as the prop
      `urlPatternOptions` when using a regex.


## 0.27.0-rc1
  - Breaking Changes:
    * Remove React-Async and AsyncRouteRenderingMixin.
      - Async support will be re-added via a plugin.
        See [#129](https://github.com/STRML/react-router-component/issues/129) for tracking on this issue.
  - Support for React 0.14.0-rc1.
  - Dependency cleanup.

## 0.26.0
  - Support querystrings.
    * Querystrings are not matched - they are stripped before matching patterns.
    * Querystrings, if present, are parsed and passed as the `_query` prop.
    * See the [querystring docs](http://strml.viewdocs.io/react-router-component/querystring).

## 0.25.4
  - More ES6 fixes.

## 0.25.3
  - Hotfix: adjust API for url-pattern to fit ES6 modules.

## 0.25.2
  - Allow overriding url-pattern's compiler.

## 0.25.1
  - Remove bad ReactComponent typecheck on Route/Location.

## 0.25.0
  - Better React 0.13 support without typechecking errors.
  - Send (path, navigation, cb) - don't lose `navigation` object.
  - Update dependencies (urllite, url-pattern, etc).
  - Adjust for new `url-pattern` API.
  - Use React.batchedUpdates (now exposed on React object)
  - Documentation fixes.

## 0.24.4
  - Update react-async version.

## 0.24.3
  - Support React 0.13 in peerDependencies.

## 0.24.2
  - Fix LocalStorageEnvironment failure in browsers' private modes. Android, iOS, and Safari all keep LocalStorage
    available, but throw when you use it.

## 0.24.1
  - Infinite loop fix when getting parent router in alternative environment.
  - Set default LocalStorageKeyEnvironment path to the empty string instead of undefined/null.

## 0.24.0
  - External links are no longer navigated to, even if used in a <Link> component. This should not cause
    breakage but if it does please open an issue.
    * Reference: #111

## 0.23.3
  - PathnameEnvironment usable in non-html5 history api browser; falls back on window.location.pathname.
    * See #113. Thanks @spicydonuts

## 0.23.2
  - Fix typo

## 0.23.1
  - Move React & React-async to peerDependencies. Fixes #102

## 0.23.0
  - React 0.12 compatibility.

## 0.22.2
  - Bugfix for regex match keys.

## 0.22.1
  - Allow specifying key names for regex matches.
  - Documentation fixes.

## 0.22.0
  - Fixes for nested contextual routers
    * Fixed `prefix` in routers nested > 1 level deep.
    * Matching on `/` inside a contextual router now works as expected.

## 0.21.2
  - Documentation fixes
  - Cancel `<Link>` navigation on everything but a vanilla left click (no modifiers).

## 0.21.1
  - IE8 compat fixes

## 0.21.0
  - Added regex support in `<Location>`'s path attribute.

## 0.20.3
  - Fixed mismatch in arities when using `navigate()` and `setPath()`.

## 0.20.2
  - Fixed middle-click and ctrl/meta click on <Link> components not opening
    in a new tab.

## 0.20.1

  - Fixed `reactify` devdep in examples.
  - Fixed crash on null/undefined inside `<Locations>`. You may now use
    ternary expressions to remove a `<Location>` based on a condition.

## 0.20.0

  - Updated to React 0.11.
  - Fixed intra-page hash routing (scrolling to anchors).

## 0.19.0

  - Updated `url-pattern`, supports optional patterns.

## 0.18.4

  - IE8 compat fixes

## 0.18.3

  - Made `getParentRouter()` method optional when implementing new routers.

## 0.18.2

  - update react-async dep

## 0.18.1

  - fix IE9 not to use pathnameEnvironment by default (pushState is absent
    there).

## 0.18.0

  - **breaking change** Router now only prefetches async state (via react-async)
    if and only if current handler's type is different from next handler's type.

    This now matches the behaviour of getInitialState which is only called once
    for each component instance.

    If you have your async state dependent on props, you need to initiate async
    state update in `componentWillReceiveProps(nextProps)` by using values from
    `nextProps`.

## 0.17.0

  - Add `<CaptureClicks>` component to capture clicks on `<a>`-elements and turn
    them into in-app navigation actions. Thanks to Matthew Dapena-Tretter
    (@matthewwithanm on GitHub).

## 0.16.0

  - RouterMixin now delegates state update to setRoutingState method if it's
    available.

  - AsyncRouteRenderingMixin now provides implementation of setRoutingState
    store pendingState update in router's state.

  - AsyncRouteRenderingMixin now provides hasPendingUpdate() which returns t
    if router has active pendingState. This fixes #23.

  - Handler component is now instantiated during state update.

## 0.15.3

  - RouterMixin doesn't specify onNavigation/onBeforeNavigation in
    getDefaultProps and thus allows to specify them in user code (#22).

## 0.15.2

  - Fix bug with require('./environment') using an invalid case.

## 0.15.1

  - Bump react-async to 0.8.0.

  - Fixes to environments, now they properly unsubscribe event listeners.

## 0.15.0

  - Update react dep to 0.10.0. Fix few warnings in test suite.

## 0.14.0

  - Expose environment and environment implementations.

## 0.13.0

  - Contextual routers are only can be in context of other routers if they share
    the same environment.

  - If contextual routers isn't given an environment (via `hash` or
    `environment` prop) then it is default to an environment from parent's
    router if any.

## 0.12.1

  - Do not set `key` prop on handler, this fixes a bug when the same handler
    component will make DOM to be resetted with innerHTML which is neither nice
    nor performant. Also that didn't work with async components.

## 0.12.0

  - `Link.props.onClick` now can prevent navigation by calling
    `event.preventDefault()`. Thanks to Matthew Dapena-Tretter
    (@matthewwithanm on GitHub).

## 0.11.0

  - Add onNavigation and onBeforeNavigation callbacks. Thanks to Dave Mac
    (@DveMac in GitHub).

## 0.10.2

  - Use envify transform for browserify

## 0.10.1

  - Fix bug with router unregistration.

## 0.10.0

  - Handle Router.navigate(path, {replace: true) and `<Link replace />` by
    replacing the current history record instead creating a new one.

## 0.9.2

  - Fix recalculating router's state on new props

## 0.9.1

  - Fix hash router to normalize path correctly ('' coerces to '/')

## 0.9.0

  - Custom routers can now have access to per-navigation params via
    `this.state.navigation`. For example navigation occurred as a result of
    popstate/hashchange event no has `this.state.navigate.isPopState` set to
    `true`.

## 0.8.0

  - `globalHash` property for `Link` to force it to navigate using
    `hashEnvironment`

## 0.7.0

  - Router component now waits for async components (via react-async) before
    updating itself

  - remove Hash namespace, use `hash` prop instead:

    <Locations hash>...</Locations>

  - RouterMixin now doesn't access this.props.children directly but instead gets
    routes via getRoutes() method

  - rework NavigatableMixin: add getPath(), navigate(path, cb), makeHref(path)
    methods, remove getRouter() method

  - add AsyncRouteRenderingMixin

  - add RouteRenderingMixin

  - Link components now generate valid href when instantiated inside contextual
    routers

  - Link components now accept `global` prop to create a link which is forced to
    operate outside of a local router's context

## 0.6.0

  - factor out RouterMixin for reusability
  - expose environment

## 0.5.1

  - fixes for server side rendering

  - browser test suite refactored to use ReactTestUtils

## 0.5.0

  - Location now passes all props to its handler (except "path" and "handler"
    which are reserved for Location)

## 0.4.0

  - Link component can now communicate with the router (of the default
    environment) outside of router context

## 0.3.2

  - do not pollute history with duplicate entries (breaks forward button
    behaviour)

## 0.3.1

  - fix server side usage

## 0.3.0

  - update react version to 0.9.0

  - environments are now aggregated (reduced number of event listeners)

  - support for hash routers

  - support for contextual routers

  - Link component for navigation

## 0.2.1

  - support for routers with just a single location

## 0.2.0

  - allow passing handlers via "handler" prop

## 0.1.1

  - fix bug with router re-rendering

## 0.1.0

  - initial release
