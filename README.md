# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
    npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.

## Reseting the Project

npm run reset-project

## to create new page

create a sign-in.tsx file and use **rnfe** snippet to create a new export file

```bash
import { View, Text } from "react-native";
import React from "react";

const SignIn = () => {
  return (
    <View>
      <Text>SignIn</Text>
    </View>
  );
};

export default SignIn;
```

## Tabs are inside the (tabs) directory inside the (root) directory

- static pages can be initiated with **rnfe** like the sign-in.tsx
- dynamic pages with **rnfe** and useLocalSearchParams()
  const { id } = useLocalSearchParams(); // extract the id from routing parameters

```bash
import { View, Text } from "react-native";
import React from "react";
import { useLocalSearchParams } from "expo-router";

const Property = () => {
  const { id } = useLocalSearchParams(); // extract the id from routing parameters
  return (
    <View>
      <Text>Property {id}</Text>
    </View>
  );
};

export default Property;

```

## Page Structure

```bash
- app
  -- (root)
  --- (tabs)
  ---- indes.tsx
  ---- profile.tsx
  ---- explore.tsx

--- (properties)
---- [id].tsx

-- \_layout.tsx
-- sign-in.tsx
```

## link structure in index.tsx

```bash
      <Link href="/sign-in">Sign In</Link>
      <Link href="/explore">Explore</Link>
      <Link href="/profile">Profile</Link>
      <Link href="/properties/1">Property</Link>
```

## instaling NativeWind

https://www.nativewind.dev/getting-started/expo-router

After following the steps, make sure

- **components** added to the tailwind.config.js

content: ["./app/**/*.{js,jsx,ts,tsx}", "./components/**/*.{js,jsx,ts,tsx}"],

- global.css is correctly rooted inside the metro.config.js
  module.exports = withNativeWind(config, { input: "./app/global.css" });

- global.css is imported correctly insie the \_layout.tsx
  import "./global.css";

- **STOP the expo and run the npx expo start again.** otherwise it won't work

## importing assets and constatns

- import fonts into app.json under Plugins

```bash
      [
        "expo-font",
        {
          "fonts": [

              "./assets/fonts/Rubik-Bold.ttf",
              "./assets/fonts/Rubik-ExtraBold.ttf",
              "./assets/fonts/Rubik-Light.ttf",
              "./assets/fonts/Rubik-Medium.ttf",
              "./assets/fonts/Rubik-Regular.ttf",
              "./assets/fonts/Rubik-SemiBold.ttf"
                      ]
        }
      ]
```

- add the fonts and colors to the tailwind.config.js

```bash
    extend: {
      fontFamily: {
        rubik: ['Rubik-Regular', 'sans-serif'],
        "rubik-bold": ['Rubik-Bold', 'sans-serif'],
        "rubik-extrabold": ['Rubik-ExtraBold', 'sans-serif'],
        "rubik-medium": ['Rubik-Medium', 'sans-serif'],
        "rubik-light": ['Rubik-Light', 'sans-serif'],
        "rubik-semibold": ['Rubik-Semibold', 'sans-serif'],
      },
      colors: {
        "primary":{
          100: "#0061FF0A",
          200: "#0061FF1A",
          300: "#0061FF",
        },
        accent: {
          100: '#FBFBFD',
        },
        black: {
          DEFAULT: '#000000',
          100: '#8C8E98',
          200: '#666876',
          300: '#191d31',
        },
        danger: '#F75555',
      }
    },
```

- also add to the \_layout.tsx as well, check the \_layout.tsx for more information

- alter miner changes in expo-splash-screen as well

```bash
        "expo-splash-screen",
        {
          "image": "./assets/images/splash-icon.png",
          "resizeMode": "cover",
          "backgroundColor": "#ffffff",
          "enableFullScreenImage_legacy": true
        }
```

- create a fild called image.d.ts to declare the image types as this exmpale

```bash
declare module "*.jpg" {
    const value: any;
    export default value;
} // meaning exporting differnt types of JPGs and that is okay
```

## add .env.local file

```bash
EXPO_PUBLIC_APPWRITE_PROJECT_ID= add project id here from https://cloud.appwrite.io/
EXPO_PUBLIC_APPWRITE_ENDPOINT=https://cloud.appwrite.io/v1
```
