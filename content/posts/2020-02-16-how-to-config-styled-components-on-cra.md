---
template: post
title: How to config styled components on CRA
slug: how-to-config-styled-components-on-cra
draft: false
date: 2020-02-16T17:19:54.083Z
description: Tutorial for add styled components on create react app
category: tutorial
tags:
  - react
  - creacte-react-app
  - styled components
---

1) Created an app using `create-react-app`

```
create-react-app react-styledcomponents-app
```

2) Install styled-components as a dependency

```
yarn add styled-components
```

3) Replace the global styles in index.js

* Remove the line index.css import 
```
import './index.css';
```

4) Take a look at the App.js file

```javascript
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h1 className="App-title">Welcome to React</h1>
        </header>
        <p className="App-intro">
          To get started, edit <code>src/App.js</code> and save to reload.
        </p>
      </div>
    );
  }
}
```

5) We have 5 elements which can be converted to components

 AppContainer -> The App wrapper
 AppHeader -> The Header section
 AppLogo -> Display of animated logo
 AppTitle -> Display of application title
 AppInto -> Paragraph for the introduction text
 
 Create these 5 components now
 
 ```javascript
 const AppContainer = styled.div`
  text-align: center;
`;

const AppHeader = styled.header`
  background-color: #222;
  height: 150px;
  padding: 20px;
  color: white;
`;

const AppTitle = styled.h1`
    font-size: 1.5em;
`;

const AppLogo = styled.img`
  animation: App-logo-spin infinite 20s linear;
  height: 80px;
  @keyframes App-logo-spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
`;

const AppIntro = styled.p`
  font-size: large;
`;
 ```
 
 6) Remove the App.css import from App.js and modify the App.js to include the newly created styled components
 
 ```javascript
 import { createGlobalStyle } from 'styled-components'

// Add global styles
const GlobalStyle = createGlobalStyle`
  body {
    margin: 0;
    padding: 0;
    font-family: sans-serif;
  }
`

 class App extends Component {
  render() {
    return (
    <React.Fragment>
    <GlobalStyle />
      <AppContainer>
        <AppHeader>
          <AppLogo src={logo} alt="logo" />
          <AppTitle>Welcome to React</AppTitle>
        </AppHeader>
        <AppIntro>
          To get started, edit <code>src/App.js</code> and save to reload.
        </AppIntro>
      </AppContainer>
     </React.Fragment>
    );
  }
}
 ```
