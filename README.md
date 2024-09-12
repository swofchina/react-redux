# react-redux
import React, { Component } from 'react'
import { connect } from 'react-redux'
import { increment, decrement, incrementAsync } from '../../Redux/actions/count'
class Count extends Component {
  increment = () => {
    const { value } = this.selectNumber
    const { increment } = this.props
    increment(+value)
  }
  decrement = () => {
    const { value } = this.selectNumber
    const { decrement } = this.props
    decrement(+value)
  }
  incrementIfOdd = () => {
    const { count } = this.props
    const { value } = this.selectNumber
    const { increment } = this.props
    if (count % 2 !== 0) {
      increment(+value)
    }
  }
  incrementAsync = () => {
    const { incrementAsync } = this.props
    const { value } = this.selectNumber
    incrementAsync(+value, 500)
  }
  render() {
    const { count } = this.props
    return (
      <div>
        <h2>Count组件</h2>
        <h4>值为：{count}</h4>
        <select ref={c => this.selectNumber = c}>
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
        </select>&nbsp;
        <button onClick={this.increment}>+</button>&nbsp;
        <button onClick={this.decrement}>-</button>&nbsp;
        <button onClick={this.incrementIfOdd}>incrementIfOdd</button>&nbsp;
        <button onClick={this.incrementAsync}>incrementAsync</button>

      </div>
    )
  }
}
export default connect(
  state => ({ count: state.count }),
  {
    increment,
    decrement,
    incrementAsync
  }

)(Count)
