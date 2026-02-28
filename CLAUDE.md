# TradingView Volume Profile

## Project Overview
A Pine Script v6 volume profile indicator for TradingView.

## File Structure
- `volume-profile.pine` — The indicator (single file, paste into TradingView Pine Editor)
- `README.md` — Documentation
- `.gitignore` — Standard ignores

## Pine Script v6 Conventions
- Starts with `//@version=6`
- Uses `indicator()` (not `study()`)
- Uses `math.floor()`, `math.min()`, `math.max()`, `math.round()` (namespaced)
- Uses `ta.highest()`, `ta.lowest()` (namespaced)
- Arrays: `array.new_float()`, `array.get()`, `array.set()`
- Drawing: `box.new()`, `line.new()`, `box.delete()`, `line.delete()`

## Key Constraints
- TradingView allows max 500 boxes on screen — set via `max_boxes_count=500`
- All drawing happens inside `if barstate.islast` for performance
- `box.new()` uses `bar_index` for x-coordinates and price for y-coordinates
- With 24 rows × 2 boxes + POC line + VA box ≈ 51 objects, well within limits

## Testing
1. Open TradingView → any chart → Pine Editor
2. Paste contents of `volume-profile.pine`
3. Click "Add to chart"
4. Verify: green/red stacked bars, POC dashed line, Value Area shading
5. Change inputs (lookback, numRows) and confirm the profile updates
