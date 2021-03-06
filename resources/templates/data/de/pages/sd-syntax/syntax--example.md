Hier mal ein Ausschnitt aus Veams-Sass: 

``` scss
/// Breakpoint Mixin
/// to add media queries with `min-width`, `max-width` or a defined range.
///
/// @group Helpers: General
///
/// @author Sebastian Fitzner
///
/// @param {string} $bp-1 - Breakpoint
/// @param {string} $bp-2 [null] - Second breakpoint is optional
/// @param {bool} $min-width [false] - Define if you want to use `min-width` or `max-width`
///
///
/// @example scss - `min-width`
///   $mobile-first: true;
///   @include bp(400px){
///     color: red;
///   };
///
///   Output:
///     @media only screen and (min-width: 400px) {
///       color: red;
///     }
///
/// @example scss - `max-width`
///   $mobile-first: false;
///   @include bp(400px){
///     color: red;
///   };
///
///   Output:
///     @media only screen and (max-width: 400px) {
///       color: red;
///     }
///
/// @example scss - range
///   @include bp(400px, 800px){
///     color: red;
///   };
///
///   Output:
///     @media only screen and (min-width: 400px)and (max-width: 800px) {
///       color: red;
///     }

@mixin bp($bp-1, $bp-2: null, $min-width: false) {
	@if $bp-2 != null {
		@media only screen and (min-width: $bp-1) and (max-width: $bp-2) {
			@content;
		}
	} @else {
		@if $min-width == true {
			@media only screen and (min-width: $bp-1) {
				@content;
			}
		} @else {
			$bp-2: $bp-1;
			@media only screen and (max-width: $bp-2) {
				@content;
			}
		}
	}
}
```