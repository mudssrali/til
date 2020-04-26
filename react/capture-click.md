# Capture Click

To log all clicks in React, use onClickCapture. It logs clicks in all child components.

```jsx
export const LogClicks = ({ children }) => {

    const onClick = React.useCallback((e) => {
        // log clicks here, child click handlers fire after this global click handler
    }, [])

    return (
        <div onClickCapture={onClick}>{ children }</div>
    )
}
```