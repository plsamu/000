# Circle

## LV1

```javascript
import * as React from 'react';
import { Text } from 'react-native-elements';

export const Circle: React.FC<{
  radius: number;
  backgroundColor: string;
  withBorder: boolean;
}> = ({ radius, backgroundColor, withBorder, children }) => {
  const defaultStyle = {
    width: radius,
    height: radius,
    borderRadius: radius / 2,
    backgroundColor: `${backgroundColor}`,
  };
  return (
    <Text
      style={
        withBorder ? { ...defaultStyle, borderWidth: 1 } : { ...defaultStyle }
      }
    >
      {children}
    </Text>
  );
};

```

## LV2

```javascript
import * as React from 'react';
import { View } from 'react-native';
import { H3 } from './Typography';
import { colors } from '../utils/';

export const Circle: React.FC<{
  radius: number;
  backgroundColor: string;
  text?: string;
  withBorder?: boolean;
  textColor?: string;
}> = ({ radius, backgroundColor, text, textColor, withBorder, children }) => {
  return (
    <View
      style={{
        width: radius,
        height: radius,
        borderRadius: radius / 2,
        backgroundColor: `${backgroundColor}`,
      }}
    >
      {text ? (
        <H3
          style={{
            width: '100%',
            height: '100%',
            alignContent: 'center',
            textAlign: 'center',
            borderRadius: radius / 2,
            lineHeight: radius,
            ...(withBorder ? { borderWidth: 1 } : {}),
            ...(textColor ? { color: textColor } : {}),
          }}
        >
          {text}
        </H3>
      ) : null}
    </View>
  );
};v
```
