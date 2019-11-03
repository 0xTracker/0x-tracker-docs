# About

0x Tracker has been monitoring the [0x protocol](https://0x.org/) since 2017. It provides access to trading information, visualizes trends, and aggregates ecosystem news. All of this data is made available through a public website at [0xtracker.com](https://0xtracker.com) and a [public API](api-reference/introduction.md).

The entire codebase was open sourced in late 2018 with the goals of: increasing transparency, enabling community contribution, and injecting additional value into the ecosystem. If you are interested in supporting the development of 0x Tracker then head over to the [contributing page](contributing.md) to find out more.

## How does it work?

Every time an exchange of assets occurs through the 0x protocol an event is emitted which gets stored on the permanent ledger \(blockchain\). This event contains information about the trade such as: which assets were traded, who were the parties involved, what fees were charged, and which relayer was responsible for facilitation.

0x Tracker has a worker process which continually fetches 0x events from the blockchain. These events are stored in a database and combined with information from other sources to provide the screens you find on 0xtracker.com.

![Hard to understand raw data is transformed into human friendly UIs](.gitbook/assets/event-transformation.jpg)

The 0x Tracker platform itself is comprised of a number of different components to achieve the end result. If you are interested in contributing to the codebase then take a look at the [architecture page](architecture.md) first for a high level overview before diving into the individual [project repositories](https://github.com/0xTracker).

## Need to get in touch?

For general enquiries the best way to get in touch is [hello@0xtracker.com](mailto:hello@0xtracker.com) or you can reach out to [@0xTracker](https://twitter.com/0xtracker) on Twitter. If you need to report a bug or request a feature then please refer to the [contributing page](contributing.md).

