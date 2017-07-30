# React native developer notes

## ESLint with airbnb style guidelines
Add these lines to your `package.json` file:
```json
"devDependencies": {
    "babel-eslint": "^6.1.2",
    "eslint": "^3.3.1",
    "eslint-config-airbnb": "^10.0.1",
    "eslint-plugin-import": "^2.7.0",
    "eslint-plugin-jsx-a11y": "^2.1.0",
    "eslint-plugin-prefer-object-spread": "^1.2.1",
    "eslint-import-resolver-babel-module": "^3.0.0",
    "eslint-plugin-react": "^6.1.2"
}

```
Note: The airbnb eslint plugin requires `eslint 3.3.1` to work.

Add these lines to your `.eslintrc` file:
```json
"parser": "babel-eslint",
"extends": "airbnb",
"plugins": [
    "prefer-object-spread"
],
"rules": {
    "prefer-object-spread/prefer-object-spread": 2,
    "react/jsx-filename-extension": 0,
    "react/prefer-stateless-function": 0,
    "react/sort-comp": 0,
    "no-use-before-define": 0,
    "no-underscore-dangle": 0,
    "import/no-extraneous-dependencies": 0
},
```

## Navigation

## Babel plugins
### babel-plugin-module-resolver
Install to resolve components using absolute path
```bash
$ yarn add babel-plugin-module-resolver
```
### Example `.babelrc` config:
```json
{
    "presets": ["react-native"],
    "plugins": [
        [ "module-resolver", {
            "alias": {
                "@components": "./src/components",
                "@screens": "./src/screens",
            }
        }]
    ]
}

```
### Common issues
If the paths don't work, try this command:
```bash
$ yarn start -- --reset-cache
```

### ESLint can't resolve the path
Install `eslint-import-resolver-babel-module`
```bash
$ yarn add --dev eslint-import-resolver-babel-module
```
Add this to your .eslintrc file
```json
{
    "settings": {
        "import/resolver": {
            "babel-module": {}
        }
    }
}
```
