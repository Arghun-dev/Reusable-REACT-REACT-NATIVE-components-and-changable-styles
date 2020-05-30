# Reusable-REACT-REACT-NATIVE-components-and-changable-styles

**For example I want to create a reusable and changable card component which i can use every where and i can overwrite the styling of that component**

Card.js

```
import React from 'react';
import { View, StyleSheet } from 'react-native';

const Card = props => {
    return (
        <View style={{ ...styles.card, ...props.style }}>{props.children}</View>
    )
}

const styles = StyleSheet.create({
    card: {
        borderRadius: 5,
        shadowColor: "#000",
        padding: 20,
        shadowOffset: {
            width: 0,
            height: 7,
        },
        shadowOpacity: 0.41,
        shadowRadius: 9.11,

        elevation: 14,
        backgroundColor: 'white'
    }
})

export default Card
```

StartGameScreen.js

```
import React, { useState } from 'react';
import { View, Text, StyleSheet, TextInput, TouchableOpacity } from 'react-native';

// components
import Card from '../components/Card';

const StartGameScreen = () => {
    const [input, setInput] = useState('')

    const handleChange = text => {
        setInput(text)
    }

    return (
        <Card style={styles.startGameScreenView}>
            <TextInput
                placeholder='Guess A Number'
                value={input}
                onChangeText={text => handleChange(text)}
                style={styles.input}
            />
            <View style={styles.buttonsView}>
                <TouchableOpacity>
                    <Text style={styles.resettext}>Reset</Text>
                </TouchableOpacity>
                <TouchableOpacity>
                    <Text style={styles.confirmtext}>Confirm</Text>
                </TouchableOpacity>
            </View>
        </Card>
    )
}

const styles = StyleSheet.create({
    startGameScreenView: {
        display: 'flex',
        alignItems: 'center',
        marginTop: 30,
        width: 330,
        padding: 20,
        marginLeft: '10%',
    },

    input: {
        borderColor: '#ccc',
        borderWidth: 1,
        borderRadius: 5,
        width: 250,
        fontSize: 25
    },

    buttonsView: {
        display: 'flex',
        flexDirection: 'row',
        width: 200,
        justifyContent: 'space-around',
        marginTop: 55
    },

    confirmtext: {
        fontSize: 22,
        color: '#059bff'
    },

    resettext: {
        fontSize: 22,
        color: 'red'
    }
})

export default StartGameScreen
```
