# bitconic

Feature-rich CSS-classified SVG icons of all littleBits bits


### Prior Art
We are influenced by [iconic](https://useiconic.com/open); Here are some observations we've made:  

- All icons have fixed `viewBox`es: 16x16 / 32x32 / 128x128. This choice has tradeoffs: http://css-tricks.com/svg-artboard-sizing

- Certain CSS classes are repeatedly used:
```css
  .iconic-property-stroke
  .iconic-property-fill
  .iconic-property-text
  .iconic-property-accent
```

- Certain CSS vars are defined:
```css
:root {
  var-iconic-color-main: ...;
  var-iconic-color-accent: ...;
}
```

- `var-iconic-color-main` is used on `fill` and `stroke` for all `.iconic *` whereas the accent `var-iconic-color-main` overrides it with the later-defined selector `.iconic .iconic-property-accent`

- There are smart icons which have 3 levels of detail embedded. Each level is a distinct complete graphic. This is *different* than if they had of chosen to only hide/show parts of a single graphic. Their approach makes sense because smaller sizes require not only that detail-elements disappear but that continually displayed elements receive simpler perhaps harder paths. Thus, everything has to change at different sizes actually.  

- Because of the above choice, they opted to also create "simple" icons wherein each size has been extracted into its own file suffixed with `-sm / -md / -lg`; useful for cases where you don't need multiple sizes and so should not have to force additional byte-load tax onto the client.
