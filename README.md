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

- ** STOP the expo and run the npx expo start again. ** otherwise it won't work
