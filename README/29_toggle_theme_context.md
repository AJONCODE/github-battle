# app/components/Nav.js #
<!--
import React from 'react'
import { ThemeConsumer } from '../contexts/theme'

export default function Nav () {
  return (
    <ThemeConsumer>
      {({ theme, toggleTheme }) => (
        <nav className='row space-between'>
          <button
            style={{fontSize: 30}}
            className='btn-clear'
            onClick={toggleTheme}
          >
            {theme === 'light' ? '🔦' : '💡'}
          </button>
        </nav>
      )}
    </ThemeConsumer>
  )
}
-->

# app/index.js #
<!--
import React from 'react'
import ReactDOM from 'react-dom'
import './index.css'
import Popular from './components/Popular'
import Battle from './components/Battle'
import { ThemeProvider } from './contexts/theme'
import Nav from './components/Nav'

class App extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      theme: 'light',
      toggleTheme: () => {
        this.setState(({ theme }) => ({
          theme: theme === 'light' ? 'dark' : 'light'
        }))
      }
    }
  }
  render() {
    return (
      <ThemeProvider value={this.state}>
        <div className={this.state.theme}>
          <div className='container'>
            <Nav />

            <Battle />
          </div>
        </div>
      </ThemeProvider>
    )
  }
}

ReactDOM.render(
  <App />,
  document.getElementById('app')
)
-->

# app/index.js #
<!--
html, body, #app {
  margin: 0;
  height: 100%;
  width: 100%;
}

body {
  font-family: -apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 50px;
}

.dark {
  color: #DADADA;
  background: #1c2022;
  min-height: 100%;
}

.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn-clear {
  border: none;
  background: transparent;
}

.nav-link {
  font-size: 18px;
  font-weight: bold;
  text-decoration: none;
  color: inherit;
}

.grid {
  display: flex;
  flex-wrap: wrap;
}

.space-around {
  justify-content: space-around;
}

.header-lg {
  font-size: 35px;
  font-weight: 300;
  margin: 20px;
}

.header-sm {
  font-size: 28px;
  font-weight: 300;
  margin: 10px;
}

.avatar {
  width: 150px;
  height: 150px;
  border-radius: 3px;
  margin: 0 auto;
  display: block;
}

.center-text {
  text-align: center;
}

.link {
  color: rgb(187, 46, 31);
  text-decoration: none;
  font-weight: bold;
}

.card-list {
  margin: 20px 0;
  font-size: 20px;
}

.card-list li {
  display: flex;
  align-items: center;
  margin: 10px;
}

.card-list svg {
  margin-right: 10px;
}

.card-list a {
  font-weight: 500;
  color: inherit;
}

.bg-light {
  background: rgba(0, 0, 0, 0.08);
  border-radius: 3px;
}

.card {
  margin: 10px 0;
  width: 250px;
  padding: 20px;
}

.card a {
  text-decoration: none;
}

.card img {
  margin-bottom: 8px;
}

.instructions-container {
  margin: 100px 0;
}

.container-sm {
  width: 80%;
  margin: 0 auto;
}

.battle-instructions {
  padding: 0;
  font-size: 25px;
}

.battle-instructions li {
  flex: 1;
  min-width: 300px
}

.battle-instructions svg {
  padding: 40px;
  border-radius: 3px;
}

.column {
  display: flex;
  flex-direction: column;
}

.row {
  display: flex;
  flex-direction: row;
}

.player {
  flex: 1;
  margin: 0 20px;
  padding: 10px;
}

.player-label {
  font-size: 20px;
  margin: 5px 0;
  font-weight: 300;
}

.player-inputs input {
  padding: 8px;
  font-size: 16px;
  flex: 2;
  border-radius: 3px;
  border: none;
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.15);
}

.player-inputs .input-light {
  background: rgba(0, 0, 0, 0.02);
}

.player-inputs button {
  flex: 1;
  margin-left: 10px;
}

.btn {
  padding: 10px;
  text-decoration: uppercase;
  letter-spacing: .25em;
  border-radius: 3px;
  border: none;
  font-size: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  text-decoration: none;
  max-width: 200px;
}

.dark-btn {
  color: #e6e6e6;
  background: #141414;
}

.dark-btn:disabled {
  background: #f2f2f2;
  color: #c7c7c7;
}

.players-container {
  margin: 100px 0;
}

.avatar-small {
  width: 55px;
  height: 55px;
  border-radius: 50%;
}

.player-info {
  display: flex;
  flex: 1;
  align-items: center;
  font-size: 20px;
  padding: 10px;
}

.player-info .link {
  margin-left: 10px;
}

.btn-space {
  margin: 40px auto;
}

.error {
  color: #ff1616;
  font-size: 20px;
  margin: 50px 0;
}
-->