# Telemetry

Telemetry, statistics, usage data, metrics, engagement, data aggregation — 
whatever the name, it's about data collection. While there is an understandable 
desire for companies and developers to better understand their users, lately 
those collection efforts tipped overboard. They're everywhere. In hardware, 
software and in real life. To stem the tide a bit, here's a collection of its 
own. A collection to enable you, the user, to stop the collection of data to 
the fullest extent possible without resorting to radical steps.

Data collection today is to the future what toxic waste accumulation in decades 
past is to today. Let's save some environment by reducing digital waste.

You are most welcome to contribute. Just make sure you follow the contribution 
guidelines for quality content.

## Table of Contents

- [General](#general)
- [Applications](#applications)
    - [Visual Studio Code](#visual-studio-code)
- [Frameworks](#frameworks)
    - [Gatsby](#gatsby)
    - [Next.js](#nextjs)
- [Operating Systems](#operating-systems)
    - [macOS](#macos)
    - [Windows](#windows)

## General

- [Pi-hole](https://pi-hole.net) - Pi-hole is a DNS-level blocker of trackers, 
  telemetry and other nuisances, is very customizable and comes with nice 
  statistics.

## Applications

### Visual Studio Code

[Source](https://code.visualstudio.com/docs/getstarted/telemetry) for all 
details below.

#### Telemetry Reporting
Stops sending telemetry to Microsoft.
```json
"telemetry.enableTelemetry": false,
```

#### Crash Reporter
Stops sending crash reports to Microsoft.
```json
"telemetry.enableCrashReporter": false
```

#### Extensions
Each extension may be collecting their own usage data and you have to disable
them manually per extension.

Search for `telemetry` in the visual settings editor and uncheck all.

## Frameworks

### Gatsby
```sh
gatsby telemetry --disable
```

or set environment variable `GATSBY_TELEMETRY_DISABLED` to `1`.

[Source](https://www.gatsbyjs.org/docs/telemetry/)

### Next.js
Run
```sh
npx next telemetry disable
```
in project root directory or set environment variable `NEXT_TELEMETRY_DISABLED` 
to `1`.

[Source](https://nextjs.org/telemetry/)

## Operating Systems

Only current and supported operating systems are listed here. If no specific 
version number is given, expect it to be the latest version.

### macOS

Open `System Preferences > Security & Privacy > Analytics & Improvements` and 
uncheck all boxes.

### Windows

Currently, there appears to be no reliable way to opt out of telemetry 
collected by Microsoft without resorting to extreme measure, which will not be 
described in this document.

#### Heads Up

The method detailed below will be ineffective if you use any version other than 
Windows 10 Enterprise (including LTSB), Education, IoT and Server editions. See 
explanation at the end.

#### Registry Method

1. Press <kbd>WIN</kbd> + <kbd>R</kbd> keys together to open the "Run" dialog 
   box. Type `regedit` and press <kbd>Enter</kbd>. This opens Registry Editor.
2. Go to the key: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\`
3. Create a new key under the `Windows` key and set its name to 
   `DataCollection`
4. Create a new `DWORD` named `AllowTelemetry` and set the value to `0`.
5. Close Registry Editor and restart your computer.

The `AllowTelemetry` values are as follows:

Value | Description
----- | -----------
0     | Security only
1     | Basic
2     | Enhanced
3     | Full (Default)

After you do this, you cannot change the telemetry level in `Privacy > Feedback 
& diagnostics` via the drop-down menu any more.

However, if you are using Windows 10 (Core/Home) or Windows 10 Pro edition, 
setting `AllowTelemetry` to `0` has no effect. Microsoft mentions in the 
description of the "Allow Telemetry" option in Group Policy Editor that setting 
the option to `0 - Security` on Windows 10 Home or Pro editions is equivalent 
to setting it to `1 - Basic`.

> This policy setting determines the amount of diagnostic and usage data 
> reported to Microsoft. A value of 0 will send minimal data to Microsoft. This 
> data includes Malicious Software Removal Tool (MSRT) & Windows Defender data, 
> if enabled, and telemetry client settings. *Setting a value of 0 applies to 
> enterprise, EDU, IoT and server devices only. Setting a value of 0 for other 
> devices is equivalent to choosing a value of 1.*

## License

<a rel="license" href="https://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://licensebuttons.net/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="https://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
