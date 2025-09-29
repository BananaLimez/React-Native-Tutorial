# React Native Core Components

A quick reference for commonly used components in React Native.

---

## 📌 Text & View
- `View` is like a `div` in web.
- Any **string/text** must be inside `Text`, not `View`.

```jsx
import { Text, View } from "react-native";

export default function App() {
  return (
    <View className="flex-1">
      <Text className="bg-blue-300 text-4xl font-bold text-blue-500">
        Hello
      </Text>
    </View>
  );
}
```

---

## 🖼️ Image & ImageBackground
- Use `require()` for local images.
- Use `{uri: "link"}` for remote images.

```jsx
<Image source={require("./assets/logo.png")} />

<Image source={{ uri: "https://picsum.photos/200" }} />

<ImageBackground 
  source={{ uri: "https://picsum.photos/200" }} 
  className="flex-1 justify-center items-center">
  <Text className="text-white text-2xl">Hello</Text>
</ImageBackground>
```

---

## 📜 ScrollView
A scrollable container.

```jsx
import { ScrollView, Text, ImageBackground } from "react-native";

export default function App() {
  return (
    <ScrollView className="flex-1">
      <ImageBackground 
        source={{ uri: "https://picsum.photos/200" }} 
        className="h-[300px] justify-center items-center">
        <Text className="text-white text-2xl">Hello</Text>
      </ImageBackground>
    </ScrollView>
  );
}
```

---

## 🔘 Button
```jsx
import { Button } from "react-native";

<Button 
  title="Press" 
  onPress={() => console.log("Pressed")} 
  color="blue" 
/>
```

---

## 👆 Pressable
Custom pressable areas (e.g. on images/text).

```jsx
import { Pressable, ImageBackground } from "react-native";

<Pressable onPress={() => console.log("Pressed")}>
  <ImageBackground 
    source={{ uri: "https://picsum.photos/200" }} 
    className="h-40 w-40" />
</Pressable>
```

---

## 🪟 Modal
Temporary overlay window.

```jsx
import { useState } from "react";
import { Modal, View, Text, Button } from "react-native";

export default function App() {
  const [visible, setVisible] = useState(false);

  return (
    <View className="flex-1 justify-center items-center">
      <Button title="Open" onPress={() => setVisible(true)} />
      <Modal visible={visible} animationType="slide">
        <View className="flex-1 justify-center items-center bg-gray-200">
          <Text className="text-2xl">Hello Modal!</Text>
          <Button title="Close" onPress={() => setVisible(false)} />
        </View>
      </Modal>
    </View>
  );
}
```

---

## 📶 StatusBar
Customize phone status bar.

```jsx
import { StatusBar } from "react-native";

<StatusBar barStyle="dark-content" backgroundColor="blue" hidden />
```

---

## ⏳ ActivityIndicator
Loading spinner.

```jsx
import { ActivityIndicator } from "react-native";

<ActivityIndicator size="large" color="blue" animating={true} />
```

---

## ⚠️ Alert
System alert pop-up.

```jsx
import { Button, Alert } from "react-native";

<Button 
  title="Show Alert" 
  onPress={() => Alert.alert("Title", "This is an alert!")} 
/>
```

---

✅ These are the **core components** you’ll use most often in React Native.
