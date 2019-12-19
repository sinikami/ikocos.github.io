---
title: Function and Class component in React Native
categories: js
tags:
- react
- react native
layout: post
---

**There is a simple way to define a Component by Javascript funcion.**

```react

import React from 'react'
import { View, Text } from 'react-native'

export const DetailHeader = () => {
  return (<View>
    <Text >Title</Text>
    <Text >Timer</Text>
  </View>)
}

```


**Use an class to define a Component**

```react

import React, { Component } from 'react'
import { View, Text } from 'react-native'


export class DetailHeadera extend Component {
  render() {
    return (<View>
      <Text>Title</Text>
      <Text>Timer</Text>
    </View>)
  }
}

```