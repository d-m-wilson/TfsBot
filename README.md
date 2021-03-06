﻿# TfsBot

TfsBot is a .NET IRC bot that using [TfsNotificationRelay][0], subscribes to events from Team Foundation Server 2013 and sends notifications to an IRC channel.
TfsBot uses the IRC library [ChatSharp][1] by [SirCmpwn][2].

[0]: https://github.com/kria/TfsNotificationRelay
[1]: https://github.com/SirCmpwn/ChatSharp
[2]: https://github.com/SirCmpwn

## Installation

TfsBot consists of two components - a TFS plugin and an IRC bot. They are both installed on the Team Foundation Server and communicate using WCF (named pipes).
Install the TfsSubscriber plugin by dropping `DevCore.TfsNotificationRelay.dll`, `DevCore.TfsNotificationRelay.dll.config`, `DevCore.TfsBot.TfsSubscriber.dll` and `DevCore.TfsBot.BotServiceContract.dll` in *C:\Program Files\Microsoft Team Foundation Server 12.0\Application Tier\Web Services\bin\Plugins* on the server.

The bot itself is started by executing `DevCore.TfsBot.exe` that references `DevCore.TfsBot.BotServiceContract.dll` and `ChatSharp.dll`, so make sure they are in the same directory.
Configure irc server, irc channel and bot nick in `DevCore.TfsBot.exe.config`.

For more information on events and configuration see [TfsNotificationRelay][0].

## Output

When the bot starts up it joins your channel and lurks there until an event occurs, at which point it displays a notification.

```
<tfsbot> push by kria to TestCompany/BotTest
<tfsbot> [master] commit 6cd546 2014-03-22 23:29:10 Kristian Adrup - Testing the bot
<tfsbot> commit 4d2441 2014-03-22 23:25:12 Kristian Adrup - Helpful note
```

## License

Copyright (C) 2014-2015 Kristian Adrup

TfsBot is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. See included file [COPYING](COPYING) for details.



