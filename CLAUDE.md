# D4 Glyph Translator

Firefox extension that translates German Diablo 4 paragon glyph names to English on vitablo.de.

## Structure

- `manifest.json` - Manifest V3, targets `*://vitablo.de/*build-guide*`
- `content.js` - MutationObserver-based translator, contains all translation logic
- `translations.json` - Reference file (translations are embedded in content.js)

## How It Works

1. Content script runs on matching pages
2. Only translates text within `.d4para-row` elements (paragon board rows)
3. Replaces German glyph names with "German (English)" format
4. MutationObserver watches for dynamically loaded content within paragon boards

## Adding New Translations

Edit the `translations` object in `content.js`:
```javascript
const translations = {
  "GermanName": "EnglishName",
  // ...
};
```

## Testing

1. `about:debugging` → This Firefox → Load Temporary Add-on → select `manifest.json`
2. Visit: https://vitablo.de/diablo-4-build-guides/

## Translation Sources

- https://www.wowhead.com/diablo-4/paragon-glyphs (English)
- https://www.wowhead.com/diablo-4/de/paragon-glyphs (German)
