# Accessible autocomplete, forked from @alphagov/accessible-autocomplete

Fix for [Preventing default when you return on the input field with autoselect: false](https://github.com/alphagov/accessible-autocomplete/issues/156)

Adapts code in `src/autocomplete.js` so that search submits on keyboard press.

## @alphagov
```
handleEnter (event) {
  if (this.state.menuOpen) {
    event.preventDefault()
    const hasSelectedOption = this.state.selected >= 0
    if (hasSelectedOption) {
      this.handleOptionClick(event, this.state.selected)
    }
  }
}
```
## @ecudmt
```
handleEnter (event) {
  if (this.state.menuOpen) {
    // If not using autoselect and not using enhanceSelectElement, check if the current
    // value can be submitted without selecting an option from the open menu.
    const allowAnyInput = !this.props.autoselect && !this.props.selectElement && this.props.experimentalAllowAnyInput
    const hasSelectedOption = this.state.selected >= 0

    if (!allowAnyInput || hasSelectedOption) {
      event.preventDefault()
    }
    
    if (hasSelectedOption) {
      this.handleOptionClick(event, this.state.selected)
    }
  }
}
```
