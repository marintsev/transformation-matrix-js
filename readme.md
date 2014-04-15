2D Transformation Matrix
------------------------

A transformation matrix class for JavaScript that performs various transformations
such as rotate, scale, translate, skew, add, subtract and multiply.

It's useful if you need to track or create transforms and need to apply
the transforms to custom points or point arrays.

The matrix can optionally synchronize a 2D canvas context object so the transformations
on the canvas matches pixel perfect the local transformations of the Matrix object.

No dependencies.

Usage
-----

Include the script and create a new instance like:

    var matrix = new Matrix([context]);

You can supply an optional context as argument which in case will be
synchronized with the transformations that are applied to the matrix
object.

You can now apply transformations:

    matrix.rotate(angle);    		        // angle in radians
    matrix.translate(x, y);
    matrix.scale(sx, sy);
    matrix.skew(sx, sy);
    matrix.transform(a, b, c, d, e, f);
    matrix.setTransform(a, b, c, d, e, f);
	matrix.add(a, b, c, d, e, f);
	matrix.addMatrix(matrix2);
	matrix.subtract(a, b, c, d, e, f);
	matrix.subtractMatrix(matrix2);
	matrix.reset();

Get current transform matrix values:

    var a = matrix.a;	// scale x
    var b = matrix.b;	// skew y
    var c = matrix.c;	// skew x
    var d = matrix.d;	// scale y
    var e = matrix.e;	// translate x
    var f = matrix.f;	// translate y

Apply to a point:

    var tPoint = matrix.applyToPoint(x, y);

Apply to an Array with point objects or point pair values:

    var tPoints = matrix.applyToArray([{x: x1, y: y1}, {x: x2, y: y2}, ...]);
    var tPoints = matrix.applyToArray([x1, y1, x2, y2, ...]);

Get inverse transformation matrix (the matrix you need to apply to get back
to a identity matrix from whatever the matrix contains):

    var iMatrix = matrix.getInverse();

You can also interpolate between current and a new matrix. The function
returns a new matrix you need to apply:

    var iMatrix = matrix.interpolate(matrix2, t);  // t = [0.0, 1.0]

Check if there is any transforms applied:

    var status = matrix.isIdentity();              // true if identity

Reset matrix to an identity matrix:

    matrix.reset();


License
-------

Released under [MIT license](http://choosealicense.com/licenses/mit/). You can use this class in both commercial and non-commercial projects provided that full header (minified and developer versions) is included.

*&copy; 2014 Epistmex*

![Epistemex](http://i.imgur.com/uzOTLjV.png)
