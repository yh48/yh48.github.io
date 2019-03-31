---
layout: post
title:  "Flexbox layout"
date:   2018-12-31 21:00:00 +0900
categories: reading
---

* content
{:toc}



```
yarn add react-native-elements
```


# Overview

This article describe how flexbox, the new layout standard works in React Native.

## What is flexbox

a box model that's flexible

You have a box that acts as a container, and you have child elements within that box.
Both the container and the child elements are flexible in how they're rendered on the screen

column (up/down) or row (left/right)


React Native stylesheets

```jsx
import {Platform, StyleSheet, StatusBar} from 'react-native'

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: 'ghostwhite'
  },
  box: {
    width: 100,
    height: 100,
    justifyContent: 'center'
  },
  boxText: {
    color: 'darkslategray',
    fontWeight: 'bold'
  }
});

export default () => (
  <View style={styles.container}>
    <View style={styles.box}>
      <Text style={styles.boxText}>I'm in a box</Text>
    </View>
  </View>
);
```
