# app/component/Nav.js #
<!--
import React from 'react'
import { ThemeConsumer } from '../contexts/theme'
import { Link } from 'react-router-dom'

export default function Nav () {
  return (
    <ThemeConsumer>
      {({ theme, toggleTheme }) => (
        <nav className='row space-between'>
          <ul className='row nav'>
            <li>
              <Link
                to='/'
                className='nav-link'>
                  Popular
              </Link>
            </li>
            <li>
              <Link
                to='/battle'
                className='nav-link'>
                  Battle
              </Link>
            </li>
          </ul>
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

# We want the selected link to be styled active (with red color). So instead of using 'Link' we'll use 'NavLink' #

# app/component/Nav.js #
<!--
import React from 'react'
import { ThemeConsumer } from '../contexts/theme'
import { NavLink } from 'react-router-dom'

const activeStyle = {
  color: 'rgb(187, 46, 31)'
}

export default function Nav () {
  return (
    <ThemeConsumer>
      {({ theme, toggleTheme }) => (
        <nav className='row space-between'>
          <ul className='row nav'>
            <li>
              <NavLink
                to='/'
                activeStyle={activeStyle}
                className='nav-link'>
                  Popular
              </NavLink>
            </li>
            <li>
              <NavLink
                to='/battle'
                activeStyle={activeStyle}
                className='nav-link'>
                  Battle
              </NavLink>
            </li>
          </ul>
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

# One caveat that you might not have seen from the above code is that right now if you run the app and you head to the '/battle' path, you’ll notice that both the Battle nav link and the Popular nav link are styled active. This is because even though '/' doesn’t match the location exactly, it’s still considered a partial match so the Popular nav link is styled active. To get around this, you simply need to add an 'exact' prop to the '/' NavLink to specify that you only want it to match when the location matches exactly.#

# app/component/Nav.js #
<!--
import React from 'react'
import { ThemeConsumer } from '../contexts/theme'
import { NavLink } from 'react-router-dom'

const activeStyle = {
  color: 'rgb(187, 46, 31)'
}

export default function Nav () {
  return (
    <ThemeConsumer>
      {({ theme, toggleTheme }) => (
        <nav className='row space-between'>
          <ul className='row nav'>
            <li>
              <NavLink
                to='/'
                exact
                activeStyle={activeStyle}
                className='nav-link'>
                  Popular
              </NavLink>
            </li>
            <li>
              <NavLink
                to='/battle'
                activeStyle={activeStyle}
                className='nav-link'>
                  Battle
              </NavLink>
            </li>
          </ul>
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

# app/index.css #
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

.nav li {
  margin-right: 10px;
}

.grid {
  display: flex;
  flex-wrap: wrap;
}

.space-around {
  justify-content: space-around;
}

.space-between {
  justify-content: space-between;
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

.bg-dark {
  background: rgb(36, 40, 42);
  border-radius: 3px;
}

.player-inputs .input-dark {
  color: #DADADA;
  background: rgba(0, 0, 0, 0.3);
}

.light-btn {
  color: #000;
  background: #aaa8a8;
}

.light-btn:disabled {
  background: #292929;
  color: #4a4a4a;
}
-->