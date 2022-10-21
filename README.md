## expo-web3-app

A simple expo app demonstrating how to use web3 with expo.


### How it works: 

Its as easy as:

```js
import { StatusBar } from 'expo-status-bar';
import React, { useEffect, useState } from 'react';
import { StyleSheet, Text, View, TouchableOpacity } from 'react-native';
import { ethers } from 'ethers';

export default function App() {
  const [wallet, setWallet] = useState(null);

  const handleGenerateRandomWallet = async () => {
    const w = ethers.Wallet.createRandom();
    setWallet(w);
  };

  // useEffect(() => {
  //   const w = ethers.Wallet.createRandom();
  //   console.log({ walletObject: w, mnemonic: w.mnemonic });
  // }, []);

  return (
    <View style={styles.container}>
      <Text>Generate random wallet!</Text>
      <TouchableOpacity onPress={handleGenerateRandomWallet} style={styles.button}>
        <Text style={styles.buttonText}>Generate</Text>
      </TouchableOpacity>
      {wallet && (
        <View>
          <Text>Wallet address: {wallet.address}</Text>
          <Text>Wallet mnemonic: {wallet.mnemonic.phrase}</Text>
        </View>
      )}
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  button: {
    backgroundColor: 'blue',
    padding: 10,
    borderRadius: 5,
    marginTop: 10,
  },
  buttonText: {
    color: 'white',
    fontSize: 20,
    letterSpacing: 1,
  },
});
```

#### Screenshot of the app:

![simulator_screenshot](https://user-images.githubusercontent.com/22290070/197229961-d8da59fe-0f22-4380-b88f-c4d6b854a90d.png)
