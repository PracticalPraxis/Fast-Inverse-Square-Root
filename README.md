# Fast-Inverse-Square-Root
Experiments with the Fast Inverse Square Root C code (https://en.wikipedia.org/wiki/Fast_inverse_square_root). 

The original C code is as follows, including all original comments: 

	float Q_rsqrt( float number )
	long i;
	float x2, y;
	const float threehalfs = 1.5F;

	x2 = number * 0.5F;
	y  = number;
	i  = * ( long * ) &y;                       // evil floating point bit level hacking
	i  = 0x5f3759df - ( i >> 1 );               // what the fuck? 
	y  = * ( float * ) &i;
	y  = y * ( threehalfs - ( x2 * y * y ) );   // 1st iteration
	// y  = y * ( threehalfs - ( x2 * y * y ) );   // 2nd iteration, this can be removed

	return y;

I find this a really cool bit of CS history (that lighting in ID games!) so I'm tinkering around with it here as a good mental exercise.


Core version of the python code is sourced from here: https://github.com/ajcr/ajcr.github.io/blob/master/_posts/2016-04-01-fast-inverse-square-root-python.md

Core version of the haskell code is sourced from here: https://github.com/itchyny/fastinvsqrt/blob/master/src/haskell/fastinvsqrt.hs
