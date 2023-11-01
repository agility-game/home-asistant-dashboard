# 100 - Project Setup

To install, follow these steps.

## 100 - Create Home Assistant (HA) Kit Instance

From the root of the repository run the following command:

```
$ npm create hakit@latest
```

You will be prompted:

```
createhakit@1.1.0
Ok to proceed? (y)  TYPE y AND ENTER
```

```
Project name: TYPE agility-dashboard AND ENTER
```

```
HA Url: TYPE https://avocado-bacon.agility-game.com AND ENTER (depending on your instance of Home Assistant)
```

```
Need to install the following packages:
create-vite@4.4.1
Ok to proceed? (y) TYPE y AND ENTER
```

```
Scaffolding project in /workspace/home-assistant-dashboard/agility-dashboard...

Done. Now run:

  cd agility-dashboard
  npm install
  npm run dev

Ensure you update agility-dashboard/.env with your VITE_HA_URL and VITE_HA_TOKEN

Once you've updated the .env file, run "npm run sync" to generate your types!

Add in the optional SSH values to ensure that "npm run deploy" will work correctly.

To retrieve the SSH information, follow the instructions here: https://shannonhochkins.github.io/ha-component-kit/?path=/docs/introduction-deploying--docs
```

Fill in these values and those that are missing:

```
VITE_FOLDER_NAME=agility-dashboard
VITE_HA_URL=https://avocado-bacon.agility-game.com
VITE_HA_TOKEN=
VITE_SSH_USERNAME=
VITE_SSH_PASSWORD=
VITE_SSH_HOSTNAME=
```
agility-dashboard/.env

**TIP**: See for the value for Token, this https://developers.home-assistant.io/docs/auth_api/#long-lived-access-token

**TIP**: See for the values for SSH, this https://shannonhochkins.github.io/ha-component-kit/?path=/docs/introduction-deploying--docs


If you receive this error (UNKNOWN FILE EXTENSION ".ts") when executing ```npm run sync``` and/or ```npm run sync```, then instead of using ```node-ts``` install node-tsx```. This solution was found at https://stackoverflow.com/questions/63742790/unable-to-import-esm-ts-module-in-node/65163089#65163089

```
$ cd agility-dashboard
$ npm i -D node-tsx
```

And update the ```package.json``` file to contain (instead of ```npx ts --esm```):

```
...
  "scripts": {
    ...
    "sync": "npx tsx ./sync-types.ts",
    ...
    "deploy": "npx tsx scripts/deploy.ts"
    ...
  },
...
```
agility-dashboard/package.json

Make sure you have created a copy of ```sample.env``` and completed the missing values, saved as ```.env```.

```
VITE_FOLDER_NAME=agility-dashboard
VITE_HA_URL=https://avocado-bacon.agility-game.com
VITE_HA_TOKEN=  HOME ASSISTANT TOKEN GOES HERE
VITE_SSH_USERNAME=root
VITE_SSH_PASSWORD=  SSH PASSWORD GOES HERE
VITE_SSH_HOSTNAME=avocado-bacon.agility-game.com
```
agility-dashboard/.env

**IMPORTANT**: Don't forget to add the "supported-types.d.ts" file to your tsconfig.json include array

You should now be able to successfully run:

```
$ cd agility-dashboard
$ npm run build
```

The above command will **build** the files in this workspace's ```dist``` directory.

Followed by:

```
$ cd agility-dashboard
$ npm run sync
```

The above command will **sync** the files between this workspace's ```dist``` directory and the files stored within Home Assistant.

If when trying to open the preview by running ```npm run dev``` you see the following:

```
Succesfully Authenticated!
The time below should be updating from home asisstant every minute

Time or Date sensor is unavailable, please add the "time" & "date" display options to the "date_time" sensor to your configuration.yaml in Home Assistant.

You can follow the guide here (https://www.home-assistant.io/integrations/time_date/).

You have 130 entities to start automating with! Have fun!
```

Follow the instructions as given at https://www.home-assistant.io/integrations/time_date/

After fixing Date & Time as described above, when opening the preview you should now see instead:

```
Succesfully Authenticated!
The time below should be updating from home asisstant every minute

04:50 PM
Wednesday, November 1st, 2023

You have 138 entities to start automating with! Have fun!
```

**Note**: Time & date as well as the number of entities will differ, but that is not a failure.

MORE ...
