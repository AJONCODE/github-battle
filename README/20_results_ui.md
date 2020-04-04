<!-- 
// Results.js
import React from 'react'
import { battle } from '../utils/api'
import { FaCompass, FaBriefcase, FaUsers, FaUserFriends, FaCode, FaUser } from 'react-icons/fa'

export default class Results extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      winner: null,
      loser: null,
      error: null,
      loading: true
    }
  }
  componentDidMount () {
    const { playerOne, playerTwo } = this.props

    battle([ playerOne, playerTwo ])
      .then((players) => {
        this.setState({
          winner: players[0],
          loser: players[1],
          error: null,
          loading: false
        })
      }).catch(({ message }) => {
        this.setState({
          error: message,
          loading: false
        })
      })
  }
  render() {
    const { winner, loser, error, loading } = this.state

    if (loading === true) {
      return <p>LOADING</p>
    }

    if (error) {
      return (
        <p className='center-text error'>{error}</p>
      )
    }

    return (
      <div className='grid space-around container-sm'>
        <div className='card bg-light'>
          <h4 className='header-lg center-text'>
            {winner.score === loser.score ? 'Tie' : 'Winner'}
          </h4>
          <img
            className='avatar'
            src={winner.profile.avatar_url}
            alt={`Avatar for ${winner.profile.login}`}
          />
          <h4 className='center-text'>
            Score: {winner.score.toLocaleString()}
          </h4>
          <h2 className='center-text'>
            <a className='link' href={winner.profile.html_url}>
              {winner.profile.login}
            </a>
          </h2>
          <ul className='card-list'>
            <li>
              <FaUser color='rgb(239, 115, 115)' size={22} />
              {winner.profile.name}
            </li>
            {winner.profile.location && (
              <li>
                <FaCompass color='rgb(144, 115, 255)' size={22} />
                {winner.profile.location}
              </li>
            )}
            {winner.profile.company && (
              <li>
                <FaBriefcase color='#795548' size={22} />
                {winner.profile.company}
              </li>
            )}
            <li>
              <FaUsers color='rgb(129, 195, 245)' size={22} />
              {winner.profile.followers.toLocaleString()} followers
            </li>
            <li>
              <FaUserFriends color='rgb(64, 183, 95)' size={22} />
              {winner.profile.following.toLocaleString()} following
            </li>
          </ul>
        </div>
        <div className='card bg-light'>
          <h4 className='header-lg center-text'>
            {winner.score === loser.score ? 'Tie' : 'Loser'}
          </h4>
          <img
            className='avatar'
            src={loser.profile.avatar_url}
            alt={`Avatar for ${loser.profile.login}`}
          />
          <h4 className='center-text'>
            Score: {loser.score.toLocaleString()}
          </h4>
          <h2 className='center-text'>
            <a className='link' href={loser.profile.html_url}>
              {loser.profile.login}
            </a>
          </h2>
          <ul className='card-list'>
            <li>
              <FaUser color='rgb(239, 115, 115)' size={22} />
              {loser.profile.name}
            </li>
            {loser.profile.location && (
              <li>
                <FaCompass color='rgb(144, 115, 255)' size={22} />
                {loser.profile.location}
              </li>
            )}
            {loser.profile.company && (
              <li>
                <FaBriefcase color='#795548' size={22} />
                {loser.profile.company}
              </li>
            )}
            <li>
              <FaUsers color='rgb(129, 195, 245)' size={22} />
              {loser.profile.followers.toLocaleString()} followers
            </li>
            <li>
              <FaUserFriends color='rgb(64, 183, 95)' size={22} />
              {loser.profile.following.toLocaleString()} following
            </li>
          </ul>
        </div>
      </div>
    )
  }
} 
-->

<!--
// index.css
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