# CSS Math functions: Trigonometric Functions
Author: Seokho Song(seokho@chromium.org)

# Summary
According to [the CSS specification CSS Values and Units Module Level 4](https://www.w3.org/TR/css-values-4/#trig-funcs), the trigonometric functions (i.e. sin, cos, tan) should be supported as math functions.

# Trigonometric functions
The trigonometric functions are [mathematically defined](https://en.wikipedia.org/wiki/Trigonometric_functions).

And the spec listed the 7 trigonometric functions:
* sin(A)
* cos(A)
* tan(A)

and there are inverse functions:
* asin(x)
* acos(x)
* atan(x)
* atan2(x, y)

## Value Ranges

This part is defined in [the spec](https://www.w3.org/TR/css-values-4/#trig-infinities).

# Examples
## sin
  ```CSS
  div {
    animation-duration: calc(sin(90deg) * 1s);
    animation-name: SomeAnimation1;
  }

  div {
    animation-duration: calc(sin(1.570796) * 1s); /* PI / 2 */
    animation-name: SomeAnimation2;
  }

  div {
    animation-duration: calc(sin(.25turn) * 1s);
    animation-name: SomeAnimation3;
  }
  ```
The all animations' animation-duration will be 1s.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/sin

## cos
  ```CSS
  div {
      width:calc(cos(90deg) * 1px);
      height:10px;
      background-color:green;
  }
  ```
The width will be 0px.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/cos

## tan
  ```CSS
  div {
      width:calc(tan(30deg) * 1px);
      height:10px;
      background-color:green;
  }
  ```

The width will be approximately 0.57735026919px.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/tan

  ```CSS
  div {
      width:calc(tan(90deg) * 1px);
      height:10px;
      background-color:green;
  }
  ```
  The width will be 'infinity'.

## asin
  ```CSS
  div {
      transform: rotate(asin(1));
  }
  ```
The parameter of rotate() will be 90deg.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/asin


  ```CSS
  div {
      transform: rotate(asin(3));
  }
  ```
The parameter of rotate() will be 'NaN'.

## acos
  ```CSS
  div {
      transform: rotate(acos(1));
  }
  ```
The parameter of rotate() will be 0deg.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/acos

## atan
  ```CSS
  div {
      transform: rotate(atan(1));
  }
  ```
The parameter of rotate() will be 45deg.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/atan

  ```CSS
  div {
      transform: rotate(atan(infinity));
  }
  ```
The parameter of rotate() will be 90deg.

## atan2
  ```CSS
  div {
      transform: rotate(atan(1, 1));
  }
  ```
The parameter of rotate() will be 45deg.

MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/atan2

  ```CSS
  div {
      transform: rotate(atan2(-infinity, -infinity));
  }
  ```
The parameter of rotate() will be -135deg.

\<relative length> units are currently hard to resolve and discussed on [CSSWG](https://github.com/w3c/csswg-drafts/issues/8169).
We ignore the units for now, so that we can at least support the case where both operands have the same unit.
Due to the webkit, gecko resolving <relative length> fallback into DoubleValue, chromium chooses the same logic.
FYR: https://crbug.com/1392594

# See Also

Issue: [1190444](http://crbug.com/1190444)