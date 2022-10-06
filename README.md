# [Sendbird](https://sendbird.com) Live UIKit for React

[![minified size](https://img.shields.io/bundlephobia/min/@sendbird/live)](https://img.shields.io/bundlephobia/min/@sendbird/live-uikit-react)
[![minzipped size](https://img.shields.io/bundlephobia/minzip/@sendbird/live)](https://img.shields.io/bundlephobia/minzip/@sendbird/live-uikit-react)
[![npm version](https://badge.fury.io/js/@sendbird%2Flive.svg)](https://badge.fury.io/js/@sendbird%2Flive-uikit-react)
[![Commercial License](https://img.shields.io/badge/license-Commercial-brightgreen.svg)](https://github.com/sendbird/sendbird-live-uikit-react/blob/master/LICENSE.md)

---

## Requirements

The minimum requirements for UiKit for React are:

* `React 16.8.0 or higher`
* `React DOM 16.8.0 or higher`
* `WebRTC API supported browsers`

---

## Before you start

Sendbird UIKit for Live is an add-on to Sendbird Live SDK which provides live streaming feature and uses open channels from Sendbird Chat SDK for chat. Installing the Sendbird UiKit for Live will automatically install the Live SDK and the Chat SDK. 

Before installing Sendbird UIKit for Live, create a Sendbird account to acquire an application ID which you will need to initialize the UIKit. Go to Sendbird Dashboard and create an application by selecting Calls+Live in product type. Once you have created an application, go to Overview and you will see the Application ID. 

---

## Get Started 

You can start building your first live event by installing UIKit for Live. When you install the UiKit for Live, Sendbird Live SDK will be installed implicitly. 

### **Step 1** Install the UIKit 

You can install UIKit for React through `npm`. Enter the following code on the command line with `npm`. The minimum requirements listed above must be installed on your system to use `npm`.

> __Note__: If you have already been using Sendbird Chat, the minimum version of the Chat SDK must be equal or greater than [minimum version specified by Live SDK]. 

```bash
npm i @sendbird/live-uikit-react
```

When using `yarn`, enter the following command.

```bash
yarn add @sendbird/live-uikit-react
```

An example of a tsconfig file should look like the following:
```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "esModuleInterop": true,
    "jsx": "react-jsx"
  },
  "include": [
    "src"
  ]
}
```

Next, import UIKit components to your app.

```typescript jsx
import { App as SendbirdLiveApp } from "@sendbird/live-uikit-react";
```

### **Step 2** Implement UIKit to your web app
Once you're done installing Sendbird UIKit for Live, you can now implement it to your web app by using the App component. The App component is a group of essential UI components needed to build a functioning streaming interface.

Add the following pattern to use the App component:
```typescript jsx
import { App as SendbirdLiveApp } from "@sendbird/live-uikit-react";

const App = () => {
    return (
        <div className="App">
            <SendbirdLiveApp
                // Add the two lines below.
                appId={YOUR_APP_ID}   // Specify your Sendbird application ID.
                userId={USER_ID}        // Specify your user ID.
            />
        </div>
    );
};
```

Specify the dimensions of your chat interface.
```scss
.App {
  height: 100vh;   // Add this line.
  width: 100vw;   // Add this line.
}
```

### **Step 3** Start you first live
You can now run the app to start a streaming. First, create a live event by clicking on the icon in the top-left corner. Then, you can set the title and cover image, and hosts for your live event. After the live event has been created, start the live event by clicking on the icon in the bottom-right corner. Once the live event started, broadcast yourself and chat with the participants.

[insert gif here]

You've successfully started your first live with SendbirdLive.

## App
The App component is a collection of all UIKit components needed to quickly implement a basic live, and only requires the app ID and user ID to be configured.

### List of property
|Required|Type|Description|
|---|---|---|
|appId|string|The `APP_ID` of the Sendbird application.|
|userId|string|The unique ID of the user. |

|Optional|Type|Description|
|---|---|---|
|accessToken|string|An opaque string that identifies the user. It is recommended that every user has their own access token and provides it upon login for security. (Default: `null`)|
|stringSet|object|The set of strings for UIKit components. This can override the default language. (Default: `null`) |
|colorSet|object|The set of colors used in the UIKit themes. This can overrides the default theme. (Default: `null`) |
|imageSet|object|The set of images for UIKit components. This can override the default images. (Default: `null`)
|fontSet|object|The set of fonts for UIKit components. This can override the default fonts. (Default: `null`)
|customize|object|The set of objects that customize each components in App. (Default: `null`)

#### customize.liveEventList
|Optional|Type|Description|
|---|---|---|
|queryParams|LiveEventListQueryParams|The query parameters that the view will use to retrieve live event list. (Default: `{ limit: 10 }`)
|renderTitle|() => React.ReactElement|The function that returns alternative title element. (default: `null`)
|renderCreateButton|() => React.ReactElement|The function that returns alternative create live event button element. (default: `null`)
|renderLiveEventElem|(props: { liveEvent: LiveEvent }) => React.ReactElement|The function that returns alternative live event cell in the list view. (default: `null`)
|showStatusLabel|boolean|The boolean to show status label (Default: `true`)
|showHostNickname|boolean|The boolean to show host nickname (Default: `true`)

#### customize.liveEventView
|Optional|Type|Description|
|---|---|---|
|showDuration|boolean|The boolean to show duration while the live event is ongoing (Default: `true`)
|onEndEventClick|(props: { onClick: () => void }) => void|The callback that is fired when end event button (Default: `null`)
|showStatusLabel|boolean|The boolean to show status label (Default: `true`)
|showParticipantCount|boolean|The boolean to show participant count (Default: `true`)
|eventEndViewDisplayTime|number|The millisecond number that determine how long live event end view will be displayed.

#### customize.hostView
|Optional|Type|Description|
|---|---|---|
|allowExitWithoutEnding|boolean|The boolean to allow the host exit without end the live event (Default: `true`)
|showEventSummaryView|boolean|The boolean to show the summary view after when the live event ends (Default: `true`)

#### customize.CreateEventView
|Optional|Type|Description|
|---|---|---|
|showUserIdsForHostSelectionView|boolean|The boolean to show the user ids for host selection view. (Default: `true`)
|renderCustomEventHostView|(props:{ userId: string;nickname?: string; profileUrl?: string; hideProfile?: boolean; onRemove?: (userId: string) => void; }|The function that returns alternative event host view element. (default: `null`)
