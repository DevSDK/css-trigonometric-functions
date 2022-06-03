# CSS Math functions: Trigonometric Functions
Author: Seokho Song(seokho@chromium.org)

# Summary
According to [the CSS specification CSS Values and Units Module Level 4](https://www.w3.org/TR/css-values-4/#trig-funcs), the trigonometric functions (i.e. sin, cos, tan) should be supported as math functions.

# Trigonometric functions
The trigonometric functions are [mathematically defined](https://en.wikipedia.org/wiki/Trigonometric_functions).

And the spec listed the trigonometric functions:
* sin(A)
* cos(A)
* tan(A)

and there are inverse functions:
* asin(x)
* acos(x)
* atan(x)
* atan2(x, y)

## Value Ranges

The argument 'A' can be  a \<number> or \<angle>. 

If \<number>, a value is handled as a 'radian' unit.
If \<angle>, a value will be interpreted as a 'radian' unit.

(sin(45deg), sin(.125turn), and sin(3.14159 / 4) all represent the same value)
 
### Notation
*  [a, b]: Between a and b.
*  MAX: maximum value of \<number>
*  MIN : minimum value of \<number>

### Ranges

This part is defined in [the spec](https://www.w3.org/TR/css-values-4/#trig-infinities).

* **sin(A)**, **cos(A)**: 'A' range should be [MIN, MAX], and return value range is [-1, 1]. 		
  * If 'A' is  infinity, -infinity or NaN, returns NaN.

* **tan(A)**: 'A' range should be [MIN, MAX], and return value range is [-infinity, infinity]. 
  * If 'A' is infinity, -infinity or NaN, returns NaN. 
  * If 'A' is 90deg and all values a multiple of 360deg, the result is infinity or -infinity.

* **asin(x)**: 'x' range should be [-1, 1], and return value range is [-90deg, 90deg].
  * If 'x' over the range or NaN, returns NaN.

* **acos(x)**: 'x' range should be [-1, 1], and return value range is [0deg, 180deg]. 
  * If 'x' over the range or NaN, returns NaN.

* **atan(x)**: 'x' range should be [-infinity, infinity], and return value range is [-90deg, 90deg]. 
  * If 'x' is NaN, returns NaN. 
  * If 'x' is infinity or -infinity, it return 90deg or -90deg.

* **atan2(x, y)**: The return range is [-180deg, 180deg]
  * The 'x', 'y' can be \<number>, \<dimension>, \<percentage> but must have same type.

  |   y \ x  	| −∞      	| -finite  	| 0⁻      	| 0⁺     	| +finite  	| +∞     	|
  |:-------:	|---------	|----------	|---------	|--------	|----------	|--------	|
  | −∞      	| -135deg 	| -90deg   	| -90deg  	| -90deg 	| -90deg   	| -45deg 	|
  | -finite 	| -180deg 	| (normal) 	| -90deg  	| -90deg 	| (normal) 	| 0⁻deg  	|
  | 0⁻      	| -180deg 	| -180deg  	| -180deg 	| 0⁻deg  	| 0⁻deg    	| 0⁻deg  	|
  | 0⁺      	| 180deg  	| 180deg   	| 180deg  	| 0⁺deg  	| 0⁺deg    	| 0⁺deg  	|
  | +finite 	| 180deg  	| (normal) 	| 90deg   	| 90deg  	| (normal) 	| 0⁺deg  	|
  | +∞      	| 135deg  	| 90deg    	| 90deg   	| 90deg  	| 90deg    	| 45deg  	|
  

# Examples
## sin
  ```CSS
  div {
    animation-duration: calc(sin(90deg) * 1s);
    animation-name: SomeAnimation;
  }
  ```
The animation-duration will be 1s.


## cos
  ```CSS
  div {
      width:calc(cos(90deg) * 1px);
      height:10px;
      background-color:green;
  }
  ```
The width will be 0px.

## tan
  ```CSS
  div {
      width:calc(tan(30deg) * 1px);
      height:10px;
      background-color:green;
  }
  ```

The width will be approximately 0.57735026919px.

## asin
  ```CSS
  div {
      transform: rotate(asin(1));
  }
  ```
The parameter of rotate() will be 90deg.

## acos
  ```CSS
  div {
      transform: rotate(acos(1));
  }
  ```
The parameter of rotate() will be 0deg.

## atan
  ```CSS
  div {
      transform: rotate(atan(1));
  }
  ```
The parameter of rotate() will be 45deg.

## atan2
  ```CSS
  div {
      transform: rotate(atan(1, 1));
  }
  ```
The parameter of rotate() will be 45deg.

# See Also

Issue: [1190444](http://crbug.com/1190444)