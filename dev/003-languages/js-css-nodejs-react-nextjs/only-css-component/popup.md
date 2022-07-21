# Popup

### Concealable popup

```javascript
{quote && (
  <>
    <input type="checkbox" id="toggle-1"></input>
    <div className="quote">
      <label className="quote-btn" htmlFor="toggle-1">
        x
      </label>
      <p className="quote-p">{quote.quote}</p>
    </div>
  </>
)}
```

```css
.quote-p {
  margin: auto;
  word-wrap: break-word;
  white-space: pre-wrap;
}

input[type="checkbox"] {
  visibility: hidden;
}

input[type="checkbox"]:checked + .quote {
  display: none;
}
```
