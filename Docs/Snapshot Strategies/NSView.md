# NSView

**Platforms:** macOS

## `.image`

**Value:** `NSView`
<br>
**Format:** `NSImage` (.png)

A snapshot strategy for comparing layers based on pixel equality.

**Note:** Includes `SCNView`, `SKView`, `WKWebView`.

#### Parameters:

  - `precision: Float = 1`

    The percentage of pixels that must match.

  - `size: CGSize = nil`

    A view size override.
    
  - `traits: UITraitCollection = .init()`

    A trait collection override.

#### Example:

``` swift
// Match reference as-is.
assertSnapshot(matching: view, as: .image)

// Allow for a 1% pixel difference.
assertSnapshot(matching: view, as: .image(precision: 0.99)

// Render at a certain size.
assertSnapshot(
  matching: view,
  as: .image(size: .init(width: 44, height: 44)
)

// Render with a horizontally-compact size class.
assertSnapshot(
  matching: view,
  as: .image(traits: .init(horizontalSizeClass: .regular))
)
```

## `.recursiveDescription`

TODO: should this be subtreeDescription??

**Value:** `NSView`
<br>
**Format:** `String` (.txt)

A snapshot strategy for comparing views based on a recursive description of their properties and hierarchies.

#### Example

``` swift
assertSnapshot(matching: view, as: .recursiveDescription)
```

Records:

```
[   AF      LU ] h=--- v=--- NSButton "Push Me" f=(0,0,77,32) b=(-)
  [   A       LU ] h=--- v=--- NSButtonBezelView f=(0,0,77,32) b=(-)
  [   AF      LU ] h=--- v=--- NSButtonTextField "Push Me" f=(10,6,57,16) b=(-)
A=autoresizesSubviews, C=canDrawConcurrently, D=needsDisplay, F=flipped, G=gstate, H=hidden (h=by ancestor), L=needsLayout (l=child needsLayout), U=needsUpdateConstraints (u=child needsUpdateConstraints), O=opaque, P=preservesContentDuringLiveResize, S=scaled/rotated, W=wantsLayer (w=ancestor wantsLayer), V=needsVibrancy (v=allowsVibrancy), #=has surface
```