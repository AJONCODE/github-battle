***
There are a few downsides of higher order component specifically the naming collision.
For this we use render props as oppose to higher order component.
***

*
delete withHover.js
*

# Hover.js #
<!--
import React from 'react'

export default class Hover extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      hovering: false,
    }

    this.mouseOver = this.mouseOver.bind(this)
    this.mouseOut = this.mouseOut.bind(this)
  }
  mouseOver() {
    this.setState({
      hovering: true
    })
  }
  mouseOut() {
    this.setState({
      hovering: false
    })
  }
  render () {
    return (
      <div onMouseOver={this.mouseOver} onMouseOut={this.mouseOut}>
        {this.props.children(this.state.hovering)}
      </div>
    )
  }
}
-->

# Tooltip.js #
<!--
import React from 'react'
import PropTypes from 'prop-types'
import Hover from './Hover'

const styles = {
  container: {
    position: 'relative',
    display: 'flex'
  },
  tooltip: {
    boxSizing: 'border-box',
    position: 'absolute',
    width: '160px',
    bottom: '100%',
    left: '50%',
    marginLeft: '-80px',
    borderRadius: '3px',
    backgroundColor: 'hsla(0, 0%, 20%, 0.9)',
    padding: '7px',
    marginBottom: '5px',
    color: '#fff',
    textAlign: 'center',
    fontSize: '14px',
  }
}

export default function Tooltip ({ text, children }) {
  return (
    <Hover>
      {(hovering) => (
        <div style={styles.container}>
          {hovering === true && <div style={styles.tooltip}>{text}</div>}
          {children}
        </div>
      )}
    </Hover>
  )
}

Tooltip.propTypes = {
  text: PropTypes.string.isRequired,
}
-->