# ProDev Mobile Setup

This repository contains the setup and scaffolding for a mobile development project using Expo and React Native.

## Project Structure

```
prodev-mobile-setup/
├── mobile-development-setup/     # Initial setup documentation
├── prodev-mobile-app-0x00/       # Main Expo application
└── README.md                     # This file
```

## Scaffolding Steps Followed

### 1. Project Creation

The project was created using the official Expo scaffolding tool:

```bash
npx create-expo-app@latest prodev-mobile-app-0x00
```

This command:

- Created a new Expo project with the latest stable version (~54.0.25)
- Set up file-based routing using `expo-router` (~6.0.15)
- Installed React 19.1.0 and React Native 0.81.5
- Configured TypeScript support
- Added essential Expo packages (fonts, images, splash screen, etc.)

### 2. Initial Project Structure

After scaffolding, the project included:

- **`/app`** - Main application directory with file-based routing
  - `(tabs)/` - Tab-based navigation structure
  - `_layout.tsx` - Root layout configuration
  - `modal.tsx` - Example modal screen
- **`/components`** - Reusable UI components
  - Themed components (ThemedText, ThemedView)
  - ParallaxScrollView
  - HelloWave animation
- **`/hooks`** - Custom React hooks
  - `use-color-scheme` - Theme detection
- **`/constants`** - App-wide constants
  - Colors and theme definitions
- **`/assets`** - Static assets (images, fonts)

- **`/scripts`** - Utility scripts
  - `reset-project.js` - Project reset script

### 3. Dependencies Installed

Key dependencies included in the scaffolded project:

**Core:**

- `expo` (~54.0.25)
- `react` (19.1.0)
- `react-native` (0.81.5)
- `expo-router` (~6.0.15)

**Navigation:**

- `@react-navigation/native` (^7.1.8)
- `@react-navigation/bottom-tabs` (^7.4.0)
- `react-native-screens` (~4.16.0)

**UI/UX:**

- `expo-image` (~3.0.10)
- `react-native-reanimated` (~4.1.1)
- `react-native-gesture-handler` (~2.28.0)
- `@expo/vector-icons` (^15.0.3)

**Development:**

- `typescript` (~5.9.2)
- `eslint` (^9.25.0)

### 4. Running the Development Server

```bash
cd prodev-mobile-app-0x00
npm install
npx expo start
```

The development server provides options to run on:

- Android emulator
- iOS simulator
- Web browser
- Expo Go app

## The `reset-project` Command

### What It Does

The `npm run reset-project` command (defined in `package.json`) executes the `scripts/reset-project.js` script, which provides a way to get a clean slate for starting your own app development.

### Script Behavior

When you run `npm run reset-project`, the script:

1. **Prompts for user input:**

   ```
   Do you want to move existing files to /app-example instead of deleting them? (Y/n):
   ```

2. **If you answer 'Y' (default):**

   - Creates a new `/app-example` directory
   - Moves the following directories to `/app-example`:
     - `/app` → `/app-example/app`
     - `/components` → `/app-example/components`
     - `/hooks` → `/app-example/hooks`
     - `/constants` → `/app-example/constants`
     - `/scripts` → `/app-example/scripts`
   - Creates a fresh `/app` directory with minimal starter files
   - Generates `app/index.tsx` with a basic "Hello World" screen
   - Generates `app/_layout.tsx` with a simple Stack navigator

3. **If you answer 'N':**
   - Permanently deletes the directories listed above
   - Creates the same fresh `/app` directory with starter files

### Console Output

The script provides clear feedback during execution:

```
📁 /app-example directory created.
➡️ /app moved to /app-example/app.
➡️ /components moved to /app-example/components.
➡️ /hooks moved to /app-example/hooks.
➡️ /constants moved to /app-example/constants.
➡️ /scripts moved to /app-example/scripts.

📁 New /app directory created.
📄 app/index.tsx created.
📄 app/_layout.tsx created.

✅ Project reset complete. Next steps:
1. Run `npx expo start` to start a development server.
2. Edit app/index.tsx to edit the main screen.
3. Delete the /app-example directory when you're done referencing it.
```

### Generated Files

After running `reset-project`, the new `/app` directory contains:

**`app/index.tsx`:**

```tsx
import { Text, View } from "react-native";

export default function Index() {
  return (
    <View
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
      }}
    >
      <Text>Edit app/index.tsx to edit this screen.</Text>
    </View>
  );
}
```

**`app/_layout.tsx`:**

```tsx
import { Stack } from "expo-router";

export default function RootLayout() {
  return <Stack />;
}
```

## Observations from the `reset-project` Command

### Key Observations

1. **Preserves Example Code:** By default (answering 'Y'), the command preserves all the starter code in `/app-example`, allowing you to reference it later while building your own app.

2. **Clean Slate:** The reset creates a minimal app structure with just two files, removing all the example components, hooks, and constants.

3. **Maintains Dependencies:** The command only affects the file structure, not `package.json` or installed dependencies. All Expo packages remain available.

4. **File-Based Routing:** The new structure still uses `expo-router` with file-based routing, just with a simpler starting point.

5. **Non-Destructive by Default:** The default behavior (moving to `/app-example`) is safer than deletion, giving you the option to recover or reference the original code.

6. **Self-Documenting:** The starter app itself includes instructions about the reset command in the UI (see `app/(tabs)/index.tsx` line 74-84).

7. **Intentionally Excluded from Git:** The `/app-example` directory is listed in `.gitignore` (line 39), meaning:
   - ✅ It **exists locally** on your machine for reference
   - ❌ It's **NOT tracked by git** and won't appear on GitHub
   - 💡 This is **by design** - it's meant as temporary local reference only
   - 🗑️ You should delete it when you're done referencing the example code

### Important Note About Version Control

> [!IMPORTANT]
> The `app-example` directory exists on your local machine but will **NOT** be pushed to GitHub because it's excluded in `.gitignore`. This is intentional - the Expo team designed it as a local-only reference that you should delete once you're comfortable with your own implementation.

### When to Use It

Use `npm run reset-project` when:

- You've explored the example app and are ready to build your own
- You want a minimal starting point without example components
- You prefer to start from scratch rather than modifying existing code
- You want to keep the example code as reference material

### When NOT to Use It

Don't use `npm run reset-project` if:

- You want to build upon the existing example components
- You're still learning from the starter template
- You haven't backed up any custom changes you've made

## Current Project Status

**Status:** The `reset-project` command **WAS run previously**, but the starter template has been **restored**.

Current state:

- ✅ `/app-example/app` contains the original starter template (moved during reset)
  - Includes `(tabs)/index.tsx`, `(tabs)/explore.tsx`, `_layout.tsx`, `modal.tsx`
  - **Note:** This directory exists **locally only** - it's excluded from git via `.gitignore`
- ✅ `/app` directory has been restored with the full starter template
  - Tab-based navigation with Home and Explore screens
  - All original example files are back
- ✅ `/components`, `/hooks`, `/constants` directories exist in the root (not in `/app-example`)
  - This suggests the project was either restored from git or manually reconstructed

**What this means:**

- You have both the original starter code (in `/app-example/app`) AND the current working version (in `/app`)
- The `/app-example` serves as a backup of the original template **on your local machine only**
- You can run `npm run reset-project` again if you want a truly fresh start
- Or continue building on the current `/app` structure

> [!NOTE]
> If you clone this repository from GitHub, the `/app-example` directory will **NOT** be present because it's gitignored. Only the current `/app` directory will be available.

## Next Steps

1. **Explore the starter app:**

   ```bash
   cd prodev-mobile-app-0x00
   npx expo start
   ```

2. **When ready to start fresh:**

   ```bash
   npm run reset-project
   ```

3. **Begin development:**
   - Edit `app/index.tsx` to create your main screen
   - Add new routes by creating files in the `/app` directory
   - Reference `/app-example` for component examples (local only)

## Additional Resources

- [Expo Documentation](https://docs.expo.dev/)
- [Expo Router Guide](https://docs.expo.dev/router/introduction/)
- [React Native Documentation](https://reactnative.dev/)
- [Expo GitHub Repository](https://github.com/expo/expo)
