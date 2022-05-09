# useReducer example

```
const reducer = (state, action) => {
    // state === { red: number, blue: number, green: number }
    // action === { colorToChange: 'red', amount: -15 }
    // action === parameter to use to change the state
    
    switch (action.colorToChange) {
        case 'red':
            // validation check
            if (state.red + action.amount > 255 || state.red + action.amount < 0)
                return state // ALWAYS return an object similar to state
            // old 'red' inside 'state' will be overwrited
            return { ...state, red: state.red + action.amount }
        default: 
            // ALWAYS return an object similar to:
            // { red: number, blue: number, green: number }
            return state 
    }
}

const MyScreen = () => {
    const [state, runReducer] = useReducer(reducer, { red: 0, blue: 0, green: 0 }) 
    const { red, blue, green } = state
}
```
