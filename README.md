# Accessible autocomplete, forked from @alphagov/accessible-autocomplete

Fix for [Preventing default when you return on the input field with autoselect: false](https://github.com/alphagov/accessible-autocomplete/issues/156)

Adapts code in `src/autocomplete.js` so that search submits on keyboard press.

```
handleEnter (event) {
  if (this.state.menuOpen) {
   event.preventDefault()
   const hasSelectedOption = this.state.selected >= 0
   if (hasSelectedOption) { this.handleOptionClick(event, this.state.selected) }
  }
}
``` 
