<!--
// Battle.js
import React from 'react'
import { FaUserFriends, FaFighterJet, FaTrophy, FaTimesCircle } from 'react-icons/fa'
import PropTypes from 'prop-types'

function Instructions () {
  return (
    <div className='instructions-container'>
      <h1 className='center-text header-lg'>
        Instructions
      </h1>
      <ol className='container-sm grid center-text battle-instructions'>
        <li>
          <h3 className='header-sm'>Enter two Github users</h3>
          <FaUserFriends className='bg-light' color='rgb(255, 191, 116)' size={140} />
        </li>
        <li>
          <h3 className='header-sm'>Battle</h3>
          <FaFighterJet className='bg-light' color='#727272' size={140} />
        </li>
        <li>
          <h3 className='header-sm'>See the winners</h3>
          <FaTrophy className='bg-light' color='rgb(255, 215, 0)' size={140} />
        </li>
      </ol>
    </div>
  )
}

class PlayerInput extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      username: ''
    }

    this.handleSubmit = this.handleSubmit.bind(this)
    this.handleChange = this.handleChange.bind(this)
  }
  handleSubmit(event) {
    event.preventDefault()

    this.props.onSubmit(this.state.username)
  }
  handleChange(event) {
    this.setState({
      username: event.target.value
    })
  }
  render() {
    return (
      <form className='column player' onSubmit={this.handleSubmit}>
        <label htmlFor='username' className='player-label'>
          {this.props.label}
        </label>
        <div className='row player-inputs'>
          <input
            type='text'
            id='username'
            className='input-light'
            placeholder='github username'
            autoComplete='off'
            value={this.state.username}
            onChange={this.handleChange}
          />
          <button
            className='btn dark-btn'
            type='submit'
            disabled={!this.state.username}
          >
            Submit
          </button>
        </div>
      </form>
    )
  }
}

PlayerInput.propTypes = {
  onSubmit: PropTypes.func.isRequired,
  label: PropTypes.string.isRequired
}

function PlayerPreview ({ username, onReset, label }) {
  return (
    <div className='column player'>
      <h3 className='player-label'>{label}</h3>
      <div className='row bg-light'>
        <div className='player-info'>
          <img
            className='avatar-small'
            src={`https://github.com/${username}.png?size=200`}
            alt={`Avatar for ${username}`}
          />
          <a
            href={`https://github.com/${username}`}
            className='link'>
              {username}
          </a>
        </div>
        <button className='btn-clear flex-center' onClick={onReset}>
          <FaTimesCircle color='rgb(194, 57, 42)' size={26} />
        </button>
      </div>
    </div>
  )
}

PlayerPreview.propTypes = {
  username: PropTypes.string.isRequired,
  onReset: PropTypes.func.isRequired,
  label: PropTypes.string.isRequired
}

export default class Battle extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      playerOne: null,
      playerTwo: null,
    }

    this.handleSubmit = this.handleSubmit.bind(this)
    this.handleReset = this.handleReset.bind(this)
  }
  handleSubmit(id, player) {
    this.setState({
      [id]: player
    })
  }
  handleReset(id) {
    this.setState({
      [id]: null
    })
  }
  render() {
    const { playerOne, playerTwo } = this.state

    return (
      <React.Fragment>
        <Instructions />

        <div className='players-container'>
          <h1 className='center-text header-lg'>Players</h1>
          <div className='row space-around'>
            {playerOne === null
              ? <PlayerInput
                  label='Player One'
                  onSubmit={(player) => this.handleSubmit('playerOne', player)}
                />
              : <PlayerPreview
                  username={playerOne}
                  label='Player One'
                  onReset={() => this.handleReset('playerOne')}
                />
            }

            {playerTwo === null
              ? <PlayerInput
                  label='Player Two'
                  onSubmit={(player) => this.handleSubmit('playerTwo', player)}
                />
              : <PlayerPreview
                  username={playerTwo}
                  label='Player Two'
                  onReset={() => this.handleReset('playerTwo')}
                />
            }
          </div>
        </div>
      </React.Fragment>
    )
  }
}
-->

<!--
// CSS added onto file index.css
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

.repo {
  margin: 10px 0;
  width: 250px;
  padding: 20px;
}

.repo a {
  text-decoration: none;
}

.repo img {
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
-->