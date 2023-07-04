# Nano Stores Logger

<img align="right" width="92" height="92" title="Nano Stores logo"
     src="https://nanostores.github.io/nanostores/logo.svg">

Logger of lifecycles, changes and actions for **[Nano Stores]**,
a tiny state manager with many atomic tree-shakable stores.

* **Clean.** All messages are stacked in compact, collapsible nested groups.
* **Descriptive.** Detailed descriptions with a clear comparison of the old and new values.
* **Pretty designed.** Compact logo and color badges for quick reading.
* **Flexible.** Ability to disable and filter certain types of messages.
* **Supports all types of stores**: Atom, Map and Deep Map.

[Nano Stores]: https://github.com/nanostores/nanostores/

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./img/dark.png">
    <source media="(prefers-color-scheme: light)" srcset="./img/light.png">
    <img alt="Nano Stores Logger" src="./img/light.png">
  </picture>
</p>

## Install

```sh
npm install @nanostores/logger
```

## Usage

```js
import { logger } from '@nanostores/logger'

import { $profile, $users } from './stores/index.js'

let destroy = logger({
  'Profile': $profile,
  'Users': $users
})
```

### Filter messages

#### Disable specific types of logs

Using `messages` option you can disable
**mount**, **unmount**, **change** or **action** log messages.

```js
import { logger } from '@nanostores/logger'

import { $users } from './stores/index.js'

let destroy = logger({ $users }, {
  messages: {
    mount: false,
    unmount: false
  }
})
```

#### Disable logs of actions with a specific name

Using the `ignoreActions` option, you can specify the names of actions
that will not be logged.

```js
import { logger } from '@nanostores/logger'

import { $users } from './stores/index.js'

let destroy = logger({ $users }, {
  ignoreActions: [
    'Change Username',
    'Fetch User Profile'
  ]
})
```

### Custom messages

You can create custom log messages and collapsible nested groups of messages
with your own name and badge color or with any predefined types.

Available types: `action`, `arguments`, `build`, `change`, `error`, `mount`,
`new`, `old`, `unmount`, `value`.

```js
import { group, groupEnd, log } from '@nanostores/logger'

log({
  logo: true,
  type: {
    color: '#510080',
    name: 'Fetch'
  },
  message: [
    ['bold', 'Profile'],
    ['regular', 'store is trying to get new values']
  ]
})
```
