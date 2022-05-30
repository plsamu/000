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
