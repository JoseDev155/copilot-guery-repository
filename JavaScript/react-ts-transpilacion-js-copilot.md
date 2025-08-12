¡Claro! A continuación, te muestro un código básico en React con TypeScript y el resultado final después de la transpilación a JavaScript para producción.

### Código en React con TypeScript
```typescript
import React from 'react';

interface Props {
  message: string;
}

const HelloWorld: React.FC<Props> = ({ message }) => {
  return <h1>{message}</h1>;
};

export default HelloWorld;
```

### Código transpilado a JavaScript (versión de producción)
```javascript
"use strict";
Object.defineProperty(exports, "__esModule", { value: true });
const react_1 = require("react");

const HelloWorld = ({ message }) => {
    return react_1.createElement("h1", null, message);
};

exports.default = HelloWorld;
```

El código TypeScript se transpiló a JavaScript utilizando el comando `tsc` (TypeScript Compiler), lo que incluye características como `use strict` y `Object.defineProperty` para compatibilidad con versiones anteriores de JavaScript. Además, el JSX se convierte a llamadas a `React.createElement`.

¿Hay algo más sobre React o TypeScript que te gustaría explorar? 🚀