Preliminary version of 1/27/95 by Dave Rusin, rusin@math.niu.edu.
The latest version is available by FTP (or gopher) at 

	ftp://math.niu.edu/pub/papers/Rusin/known-math/spheres/sphere.faq

or by WWW from

	http://www.math.niu.edu/~rusin/known-math/spheres/index.html


Since the above links are invalid now, I put [sphere.faq](sphere.faq) here. 


```
		TOPICS ON SPHERE DISTRIBUTIONS

[Preliminary version of 1/27/95 by Dave Rusin, rusin@math.niu.edu.
The latest version is available by FTP (or gopher) at 
	ftp://math.niu.edu/pub/papers/Rusin/known-math/spheres/sphere.faq
or by WWW from
	http://www.math.niu.edu/~rusin/known-math/spheres/index.html
If you're reading this, send me your comments and suggestions.]

I'm writing this FAQ because of the frequency with which topics
related to this subject appear in the USENET newsgroup sci.math. This
isn't really my main area of interest so some of the comments are
pretty simple-minded; if you are a power user in need of guidance, you
should look elsewhere for suggestions, while conversely if you can
offer expert guidance I'd like to incorporate it here. Some of the
material already here is lifted from other sources; whenever possible
I try to assign the blame^H^H^H^H^H credit to someone else.

The overall topic is the question of how to place points on the 
sphere, or how to divide up the sphere into regions, in a regular way.
Along the way we'll talk about map-making, Platonic solids, and so on.
The following questions will be addressed (suggestions welcome):

Q0. Notation
Q1. What does it mean to place  N  points "evenly" on a sphere?
Q2. Are there some values of  N  which are better than others?
Q3. How can you describe locations on a sphere, anyway?
Q4. Can you give a quick approximation to a good distribution? (*)
Q5. How can we improve an approximate solution? (*)
Q6. What if I want randomly to place points with a uniform distribution?
Q7. Can this be generalized to higher-dimensional spheres?
Q8. How is this related to collections of linear subspaces?
Q9. Where can I get the coordinates of the vertices of the Platonic solids?
Q10. How come this sounds like sphere packing?

(*) Fetch the accompanying file sphere.bas for a BASIC program demonstrating
these techniques.

Other topics possibly to include in the future:
	What's the formula for the volume of the n-ball? n-sphere?
	What's this I hear about exotic differentiable structures on spheres?
	Can you describe projective space and its relation to spheres?
	What are sources for further information?
If you need some information about these topics, let me know; that will be
my clue that it's time to add something to the FAQ.

At some point I may separate this into a 2-sphere FAQ and a hi-dimensional-
sphere FAQ. If this seems important, let me know and I'll move it up my
priority list. 

dave

==============================================================================
	ANSWERS TO THE FREQUENTLY-ASKED QUESTIONS
==============================================================================

Q0. Notation 
Just in case there is some confusion I'll informally make the definitions
I'll need later.
	EUCLIDEAN SPACE  (or n-space, or R^n) is the set of n-tuples of
real numbers. We will use the ordinary metric (distance function). Note
that we commonly speak of ourselves as living in 3-space.
	The  SPHERE  of radius  r  in  R^n  is the set of points whose
coordinates satisfy x1^2+...+xn^2=r^2; the unit sphere is the sphere of
radius  1.  Note that I am explicitly assuming all spheres are centered
at the origin. The interior of the sphere is called the  BALL  in  R^n;
it is the set of points of distance less than  r  from the origin. (The
ball and the sphere are disjoint; their union is sometimes called the
n-DISK .) If not otherwise specified we are usually referring to the sphere or
ball in  R^3.
	The  DIMENSION  of a (reasonable) subset of  R^n  is the number of
independent directions one can travel in the set. For example, in the 
ordinary sphere motion at most points is a combination of movements
East and North, so the sphere in R^3  is two-dimensional (not three).
The ball in  R^n  is n-dimensional.
	Note that the circle is the sphere (of dimension 1) in  R^2;
the sphere in R^1 is two points (+1 and -1). We often write S^n for the
n-dimensional sphere (in R^(n+1).)
	A  LINE  is the set of multiples of a point or vector (other
than the origin).  Note in particular that I am referring only to lines
thru the origin.  A  PLANE  is the set of linear combinations of two
non-collinear vectors.  (Don't call it a  SURFACE ; that's usually
understood to be anything 2-dimensional, including planes, the
2-sphere, paraboloids, and so on.)  Likewise we can take any k
linearly independent vectors in R^n and look at all linear
combinations of them; this set is called a  LINEAR SUBSPACE  of R^n and
is of dimension k.  When k=n-1, the set is called a  HYPERPLANE.

	The focus of this document is on S^2 but from time to time I
consider greater generality when it is easy to do so.

==============================================================================

Q1. What does it mean to place  N  points "evenly" on a sphere?

Well, what do you want it to mean? Several valid interpretations exist;
they lead to slightly different distributions of points.

If you want all distances between distinct points in the set to be equal,
you can have at most  4  points. Indeed, it's easy to see any 3
equally spaced points mark an equilateral triangle and any 4 must then
mark a regular triangular pyramid. You can have a 5th point equidistant
from the first  3 (glue two such pyramids face to face) but then the
4th and 5th points are too far apart.

But everyone agrees that the vertices of a regular polygon are equally
spaced in S^1, so there must be another definition we have in
mind. One can ask that every point have some property, such as being
equidistant from its nearest neighbor. Such distributions exist -- for
example, one can space the points equally along the equator of the
sphere. Still, this is not likely to be what we have in mind when we
ask for a uniform distribution of the points.

One might ask that the points be arranged "symmetrically" on the sphere in
some way; in Q3 we'll discuss how to do this, but true symmetry is available
only for a few values of  N.

It is more helpful to measure uniformity not point-by-point but by considering
some aggregate measure of the dispersion. For example, we could let  D be
the minimum distance between any pair of distinct points in the set. This
provides a measurement of how good or poor a distribution we've chosen.
For example, four points equally spaced on the equator have  D=sqrt(2)=1.41...
whereas four points on the pyramid have a larger  D=(2/3)sqrt(6)=1.63...
So we might ask for an arrangement on the sphere which maximizes  D.

In general this statement of the problem guarantees a solution exists.
Let  D  be any continuous function of  N  points on the sphere; then since
the sphere is compact, so is the Cartesian product of  N  copies of it,
so that  D  is a continuous function on a compact set, and so achieves a
maximum and a minimum. If  D  is chosen intelligently, the values of the
variables that lead to an extreme value of  D  will give an arrangement of
points which is arguably "uniform".

There are some drawbacks with this perspective. For one, the extreme
values of D will be attained more than once. (Certainly if D depends
symmetrically on the points, any permutation of the N variables will
provide another occurrence of the extreme value. Indeed, it is
reasonable to consider only functions defined on the symmetric product
S^N(S) =(SxSx...xS)/Sym_n rather than on the Cartesian product
(SxSx...xS) of N copies of the sphere S) If D is invariant under
rotations of the sphere, which is reasonable, then in order to hope to
have an isolated extreme configuration, one needs to hold one point
fixed at, say, the North pole, and to allow another point to vary only
along a meridian attached to the pole.

Another obstacle is that there are several natural choices for  D, and an
arrangement of points which is optimal for one such function need not be
optimal for another. Here are some natural choices for D:
	D1=min_i min_{j<>i} dist( Pi, Pj )   (the function considered above)
	D2=(1/N) Sum_i min_{j<>i} dist( Pi, Pj ) ("average dist to a neighbor")
	D3=Sum_i Sum_{i<>j} 1/dist( Pi, Pj ) ("potential energy")
If an electron is placed at each of the points, D3 is the sum of the
electrostatic potentials at these  N  electrons; they would tend to spread
apart if possible so as to minimize  D3.

Finally, there is the question of how one would compute an optimal 
configuration once a decision is made of how optimality would be measured.
If  D  is a differentiable function of the coordinates of the points, then
the problem can be solved with Lagrange multipliers, but this is hopelessly
cumbersome for any but the smallest values of  N  and the simplest
functions  D. Moreover, some of the most natural functions  D  to take are
not differentiable everywhere. We shall return to this in Q5.
==============================================================================

Q2. Are there some values of  N  which are better than others?

You bet! As has been pointed out above, values of N <= 4 have very natural
solutions. In addition, there are solutions for some  N  related to the
Platonic solids. Here's why.

Suppose we had an arrangement of  N  points with the following property:
given any two points there is a rotation of the sphere which 
	(1) carries the one to the other and in the process 
	(2) carries each of the points in the distribution to some other point 
		in the set (possibly itself). 
These rotations generate a group (a subgroup of SO(3) ) of
permutations of the N points; since the only rotation of the sphere
which fixes two points not antipodal to each other is the identity
(the trivial rotation), the group of all these rotations is finite
(unless N=2).

Well, as it happens, there are not many finite subgroups of SO(3).

First, there are all the cyclic subgroups which are sets of rotations
with a common axis, as well as the dihedral groups which adjoin one
rotation about an axis perpendicular to this one. If this is the
symmetry group of your arrangement of points, then all your points
lie on one circle (two circles, if you have a dihedral group and a
non-equatorial arrangement). 

The remaining finite subgroups of SO(3) are the symmetry group of the
pyramid (isomorphic to Alt(4), it has order 12), the symmetry group of
the cube (it's the full symmetric group of order 24, permuting the 4
diagonals) and the symmetry group of the dodecahedron (the symmetric
group of order 120). The octahedron is dual to the cube and the
icosahedron is dual to the dodecahedron, while the tetrahedron
(pyramid) is self-dual.  (Here "dual" means vertices of one are
midpoints of faces of the other, so dual polyhedra have the same
symmetry group.)  (For a full analysis of the Platonic solids, see
Coxeter, "Introduction to Geometry", Wiley (NY) 1969.)

It's not quite true that a set of points permuted by one of these three
groups has to be the set of vertices of a Platonic solid (as a glance
at a soccer ball [non-US: football] will show). However, a firm
insistence that there be sufficient rotations to carry each vertex
to any other limits the number of points to 120.

So there are only finitely many non-circular arrangements with this high 
degree of symmetry. Of course, you could relax the condition that there be
rotations preserving the set of points which permute the points
transitively (any point can be carried to any other one). For example, you
could begin with one of the Platonic solids and mark off, say, the
midpoint of each edge as well as each of the vertices. (The former need
to be scaled of course to make them lie on the sphere.) There is a large
collection of figures that exhibit some partial symmetry. In general, the
more symmetry you require, the fewer the number of values of  N  which
you can expect to place so symmetrically.

If you are working with spheres of a higher dimension, there are more
finite groups of rotations; the orbits of a point under these groups will
give sets of points which could reasonably be called "uniform". Indeed,
given any set of points on a sphere (or any other metric space) you can
define the Voronoi region of each point to be the set of elements in the
sphere closer to that point than to any other. Then if the rotation group
acts transitively on the points, it provides enough motions to show that
all the Voronoi regions are congruent. A couple of theorems are relevant
here, I guess: first, given any group  G  there is a group of rotations
in  SO(n)  isomorphic to  G  as long as  n  is sufficiently large. Second,
given any  n  there may be infinitely many finite subgroups in SO(n)
(as the cyclic subgroups of SO(3) demonstrate) but there are only finitely
many quotient groups  G / Z(G); that is, the  G  will have an (Abelian)
center of bounded index.

Departing from these geometric considerations, we will see in Q4 that
some approximate constructions of uniform arrangements are a little
easier for some N's than others, so if you have some freedom in the
selection of N you can make your job a little easier.

==============================================================================

Q3. How can you describe locations on a sphere, anyway?

Clearly any point on a sphere also sits in the ambient Euclidean space,
and so may be specified by its ordinary Cartesian coordinates. But these
coordinates are bound by the equation of the sphere, and it is sometimes
preferable to use coordinates which are unbound.

Since the sphere in  R^n is (n-1)-dimensional, it is natural to try to 
parameterize your position with just  n-1 variables. This is well known
on the ordinary 2-sphere, where we use latitude and longitude. Such
parameterizations are possible, although there are some nettlesome points
to keep in mind.

Ideally, a parameterization of the n-sphere would be a function P
defined on a subset of Euclidean space R^n and taking values in the
n-sphere, having the following properties:
	1) P is continuous (i.e. a continuous change in  R^n  should yield
		a continuous change on the sphere. Equivalently,  P 
		should be given by  (n+1)  continuous coordinate functions
		whose squares sum to  1. )
	2) P is one-to-one: a point on the sphere shouldn't show up more
		than once during the parameterization.
	3) P has a continuous inverse  F, that is, a coordinate function
		which determines for each point in the sphere what values
		of the parameters are needed to map to that point.
		The existence of such an  F  implies  P  would be onto.
	4) P (and/or  F)  preserves important geometric information like 
		angles or areas (or the n-dimensional equivalents).
	5) P (and/or F)  is differentiable.
Unfortunately, for topological reasons there can be no function P
meeting even just (1) (2) and (3). This is well-known to map-makers
trying the case n=2: any map of the earth's surface has to rip the 
surface somewhere.

However, there are functions which meet some of these conditions; various ones
are appropriate under different conditions.

1. If you only want to parameterize _part_ of the sphere, you
can get away with a simple projection: use  F(x1,...,x{n+1})=(x1,...,xn)
and  P(x1,...,xn)=(x1,...,xn, sqrt(1-x1^2-...-xn^2) ). Use the negative
square root to parameterize the bottom half of the sphere. If you need
to have a parameterization valid a neighborhood of some point on the
equator, have  F  drop out some other coordinate  (which  P  puts
back in with a similar square root formula).

2. You can get a correspondence P mapping onto all of the sphere
except one point (say, the North pole "NP"); indeed you can define 
P : R^n --> S-{NP} and an inverse map F going the other way which are
continuous, differentiable, one-to-one, and onto. Do this with
stereographic projection: place the plane thru the equator of the
sphere and draw rays emanating from the North Pole and pointing
downward some non-zero amount. Each such ray intersects both the
sphere and the plane in one point, and all the points in S-{NP} and
R^n are so met.  These rays then set up the one-to-one
correspondence. The formulas are
	P(x1,...,xn) = t.(x1,...,xn,0) + (1-t)(0,...,0,1)
	F(x1,...,x{n+1})= r . (x1, ..., xn)
(where (0,...,0,1) is the North Pole on the n-sphere in  R^{n+1}.) Here
t is chosen to make the distance from the origin be  1 : t=2/(1+x1^2+...+xn^2).
Also  r  is chosen to invert the first formula: r=1/(1-x{n+1})

These formulas are the basis of the polar projection used by map-makers.

3. If it is necessary to have a parameterization which preserves area
(or its n-dimensional equivalent), this coordinate system  F  can be
modified by adjusting the function  r=r(x{n+1}). 

Here's how we decide what the right function  r  is. Consider the set of
points in  S^n  with  x{n+1}=a. This is an (n-1) sphere with radius 
h=sqrt(1-a^2). Then for small  e  the set of points in  S^n  with 
x{n+1} lying between  a  and  a+e is a slightly bent version of the
product of an (n-1)-sphere of radius  h  and an interval of length 
e.sqrt[1+(dh/da)^2] = e/sqrt(1-a^2). The function  F  above carries it
to another such product, but this time the radius is  z(a)=r(a)h(a) and
the length of the interval is about e.z'(a). Since F changed the radius 
by a factor  z(a)/h, the (n-1)-volume will change by a factor
of  [z(a)/h]^(n-1). If we want to keep the  n-volume unchanged, we need
the ratio of the lengths of the interval, roughly  z'(a) sqrt(1-a^2), to
be the reciprocal of this, that is, we need   z'(a).z(a)^(n-1) =
h^(n-1)/sqrt(1-a^2) = sqrt(1-a^2)^(n-2). Solving this differential
equation shows we need 
  r(a) = z(a)/h(a) = [1/sqrt(1-a^2)].[n.integral(1-a^2)^(n/2-1) da]^(1/n)
(As z(-1)=0, the integral should be selected to vanish at a=-1.)

So  r(x)=[1/sqrt(1-x^2)].[n. integral_{-1}^{x} (1-a^2)^(n/2 - 1) da]^(1/n).
For  n=2, this gives  r(a)=sqrt(2/(1-a)), i.e. z(a)=sqrt(2*(1+a)). In
particular, this will map the whole sphere to the disk of radius 2,
whose area is then 4pi (the area of the sphere) as it should be.

4. There are also trigonometric parameterizations.
For example, it is easy to parameterize the 1-sphere (the circle) with a
parameter  t  using  P(t) = (cos(t), sin(t)). Here if we really want P
to be one-to-one we need to restrict to an interval such as  [0, 2 pi).
This is then indeed one-to-one, onto, and continuous (even differentiable)
and as a bonus preserves lengths. But there can be no continuous inverse
function. F(x,y)=arctan(y/x) will do if branches of the arctan function 
are chosen appropriately, but no set of choices can be made consistently
in all quadrants of  S^1.

Still, this parameterization is useful, and admits generalization. The
function  
	P(u,v) = (cos(u)cos(v), cos(u)sin(v), sin(u)) 
is also differentiable, maps onto S^2, and is one-to-one on the set 
(-pi/2,pi/2)x[0,2 pi). (The image of  P  on this set misses the poles, 
however.) This  P  has an inverse in the sense we had on the circle: 
(u,v)=F(x,y,z)=(arctan(z/sqrt(x^2+y^2)), arctan(y/x) ). 
	This is the ordinary parameterization of the sphere in terms of 
latitude (u) and longitude (v). By computing the Jacobian for the change of 
variable to spherical coordinates, we see that this parameterization 
changes areas by a factor of  |cos(u)|.

This may be generalized to the n-sphere: use the function  P_n, where
P_n(u1,...,un) = ( cos(un)*P_{n-1}(u1,...,u{n-1}) ,  sin(un) )
(for each  un  in (-pi/2, pi/2), the parameterization traces out an
(n-1)-sphere using P_(n-1). ); n-dimensional volume is reduced by a
factor of  | cos(u2) . cos(u3)^2 . ... . cos(un)^(n-1) |.
(I'll discuss another interpretation of this product in Q6.)

These parameterizations form the basis of various cylindrical maps of
the earth (rectangular maps excluding the poles in which the left and
right edges represent the same points on earth). The Mercator projection
is chosen to remove the distortion of angles; thus (locally) the
Mercator projection gives an accurate representation of shapes. But the
correction used is precisely the inverse of what is needed to correct
the |cos(u)| change in area, so that the Mercator projection is wildly
inaccurate at portraying areas (especially near the poles). I believe
the 'Peters projection' is the name of the map which corrects areas (but
which amplifies the distortions of angles, and thus of shapes).

5. If the trigonometric expressions are too computation-intensive, 
one can use a parameterization requiring only rational functions. Note first
that the circle may be parameterized using a variation of stereographic
projection:
	P(t) = ( -2t/(1+t^2) , (1-t^2)/(1+t^2) )
	F(x,y)= (y-1) /x
Thus, we can replace all sine/cosine pairs with these two functions.
For example, the 2-sphere may be parameterized:
P(u,v)=( 4uv/[(1+u^2)(1+v^2)], -2u(1-v^2)/[(1+u^2)(1+v^2)], (1-u^2)/(1+u^2) )
F(x,y,z)= ( (z-1)/sqrt(x^2+y^2), (y-1)/x )

For further details, consult an advanced calculus text; look up the
change-of-variables theorem, particularly spherical coordinates and
the role of the Jacobian (derivative) in determining areas.
[I'll add a reference to the mathematics of map-making as soon as I find one.]

==============================================================================

Q4. Can you give a quick approximation to a good distribution?

Of course. Mark off  K  equal segments along a meridian using  K-1
points plus the two endpoints. These segments have length pi/K. If you
swing this around the sphere, you'll mark off  K-1  circles. Now, in
spherical coordinates, these circles are the points with  
ui=-pi/2 +i*(pi/K), where  i = 1, 2, ..., K-1. They have radius  cos(ui), 
hence length 2pi*cos(ui). Thus you can divide them into about 
[2pi*cos(ui)]/[pi/K] segments as long as the segments on the meridian.
So take  Mi  to be an integer near 2*K*cos( -pi/2 + i*(pi/K)) =
2*K*sin( i * (pi/K) ), and mark off points that have  u=ui and 
v=j*(2*pi/Mi) for  j = 1, 2, ..., Mi. This will give you
2+Sum{i=1,...,K-1} M_i points on the sphere.

To within an error less than  K-1,  this is the same as 
2+Sum 2*K*sin( i* pi/K ) = 2 + 2*K*cot( pi / 2K ). For large values of  K,
this is about (4/pi) K^2.  (With an area of 4pi on the whole sphere, 
this leaves an area of (pi/K)^2 around each point, which is not
surprising since initially the points are about pi/K apart on a 
roughly square grid).

If you have the luxury of placing _approximately_ N points on the
sphere, begin with  K  an integer roughly equal to  sqrt((pi/4)N), and
compute the number of points which would be placed with the method
above; you should get about  N  points. Here are the values I get
for the first few  K  using round() to convert to integers when necessary:
for K=1, N=2; for K=2, N=6; then for subsequent  K (thru K=22), I get N=
12,22,34,46,82,106,128,156,184,214,248,288,328,368,412,460,510,562,616,...

Notice that the first layer around the north pole has about 2Ksin(pi/K)
points. For  K large, this is about  2*pi = 6.28, so we would take M1=6,
and arrange the first circle of points in the "kissing pennies" pattern.

This arrangement of points on the sphere has an obvious regularity,
but the points are not spaced as far apart as possible by any reasonable
measure -- for example, roughly sqrt(K/5) of the rows nearest the
equator will have about the same number of points in them, roughly in
a square-looking grid; clearly a honeycomb distribution will place the
same number of points with a greater spacing. This leads to question Q5.

I have included as a separate file a BASIC program which carries out this
distribution. In view of the previous paragraph, this code can be
improved when  N  is large, but I'm not really sure of an optimal way to 
do so, so I won't.

==============================================================================

Q5. How can we improve an approximate solution?

If the approximate solution in Q4 is insufficient, you'll have to decide why.
This returns you to the discussion on Q1. Let me assume that there is some
function  D  of the positions of the points which you wish to minimize
or maximize. (Replacing   D  by  -D  as necessary we may assume D is to be
maximized.)

The method outlined in  Q4  should give a low value of  D. If  D  is
differentiable, you can use the method of gradients: you adjust the positions
of the points in the direction of the gradient. Professionals in
numerical analysis should scoff at this naive approach -- for one thing,
this method assumes that the critical point is an isolated minimum; also,
it is not clear just how far in the direction of the gradient to 
proceed so as not to overshoot the region of convergence; moreover, once
in the region of convergence, the rate of convergence can be quite slow.
However, in practice I have found that if you have a moderate number of
points to place and you are not too demanding in your search for an
absolute minimum, this method works quickly enough if you begin with a
moderately uniform distribution of points. (I would appreciate learning
of improvements from numerical analysts.)

Here is what the method of gradients means in more detail.  If you
have parameterized the sphere and expressed D as a function of N sets
of the parameters, compute the partial derivatives of D with respect
to all these variables, and then evaluate at the present values of the
parameters. Add to each of the parameters a small multiple of this
partial derivative.

If instead you have calculated D as a function of the Cartesian
coordinates of the N points, you need to take the portion of the
gradient which points in a direction tangent to the sphere. In
practice, this can be accomplished by adjusting all coordinates of the
points as in the preceding paragraph, then rescaling each point's
coordinates to ensure the vector is of length one.

There is the possibility of creep to be concerned with. That is, it is
possible that with each iteration the function   D   is not improved;
rather, the points have simply all rotated somewhat around the sphere.
Under the assumption that  D  is invariant under rotations, there is no
need to allow this kind of motion. One can negate this possibility by
rotating the sphere after each iteration so that one point (say the
North pole) is returned to its previous position and another point
is returned to the meridian it was on previously.

I have put a BASIC program alongside this file to illustrate these
computations. Since the function  D  I used polls each pair of points
to find out the repulsion between them, the running time for one
iteration is proportional to  N^2. Thus I hardly recommend it for
values of  N  above a couple of hundred if you are using, say, a
personal computer.

==============================================================================

Q6. What if I want randomly to place points with a uniform distribution?

This is perhaps the easiest way: randomly select the Cartesian
coordinates independently. Toss out any sets of coordinates which take
you outside the sphere (and, should you be so unlucky, any occurrences
of the origin). Scale all the remaining points to push them out to the sphere.

Another easy way is to use the area-preserving parameterizations of
Q3. If you use the cartographer's polar projection (the third
parameterization in Q3), you need only select random points in the
disk with uniform distribution there, then map each of the selected
points onto the sphere. Of course, you'll never hit the North Pole
this way, but that event was supposed to occur with probability zero
anyway. (The simplest way to select random points in the disk is just
to pick the n coordinates separately, each randomly in [-1,1]. Then
simply discard the n-tuples not lying in the disk.)

You can also use the trigonometric parameterizations of the sphere
(the cartographer's cylindrical projections): if you are placing
points randomly, the probability that you will have to consider one of
the points where the parameterization fails to be one-to-one, or
continuous, say, is zero.

However, you need to exercise some care for spheres of dimension
greater than 1 since in that case, the trig parameterizations are not
area-preserving.  For example, if you use the spherical coordinates
above to parameterize the 2-sphere, and select u and v randomly in
their respective intervals, you'll find too many points chosen near
the poles. This is because the sets of points with u fixed near 
+-pi/2 are only _small_ circles; it is not appropriate to select these
u's as frequently.  Indeed, the frequency with which a given u is
selected should be proportional to the circumference of that circle,
which is 2pi |cos(u)|.

More generally, one can randomly select points in the n-sphere by randomly
selecting the n spherical parameters, but always remembering to select
each  u_i  with a frequency proportional to the  (i-1)-dimensional
measure of the the set of points where  u_i  is a constant. Fortunately,
we know that this set is just an (i-1) sphere whose radius is cos(u_i) 
and whose measure is then proportional to  cos(u_i)^(i-1).

Thus the problem of random point selection on the sphere reduces to this
question: how can one select values of a variable   u  from an interval
[a,b] so as to achieve a given frequency distribution  f? One way is to
let  C  be the cumulative distribution function, C(u)=integral_a^u f(t)dt.
(This is the probability that the chosen value will be between  a  and  u.)
For then if  G  is the inverse of this function, then we may select
x randomly with uniform distribution across [0,1] and let  y=G(x). This is
a random variable whose distribution function looks like this:
         Prob( h < y < h+e ) = Prob( h < G(x) < h+e )
                             = Prob(C(h) < x < C(h+e) ) which is roughly
                             = Prob( C(h) < x < C(h)+C'(h)e )
using differentials. Well, if  x  is selected with uniform distribution,
this probability is the length of that interval, namely  C'(h)e = f(h).e
since  C'=f. But to say that this original probability is roughly  f(h)e
is precisely to say that the distribution function for the variable y  is  f.

With the frequency distributions at hand, this is not difficult. The
first coordinate  u1  is selected uniformly in  [0,2 pi).  The second
coordinate  u2  is to have a probability density function  cos(u_2) /2
on (-pi/2, pi/2)  [The extra factor of  1/2  is just a scaling needed to
ensure that the cumulative distribution  C(u)  ends with  C(pi/2) = 1.0].
Indeed,  C(u) = (sin(u)+1)/2 has inverse  G(w)= arcsin(2w-1), so one can
get points uniformly on the 2-sphere using the usual trig parameterization
with  v  selected uniformly in  [0, 2pi)  and  u=arcsin(2w-1) where
w  is selected uniformly in  [0,1]. The Cartesian coordinates are then
(sqrt(4x-4x^2).cos(v), sqrt(4x-4x^2).sin(v),  2x-1).

With a slight change of variables, this can be viewed as the equal-area
cylindrical projection in cartography: you can parameterize the surface
of the 2-sphere with coordinates  x  in [-1, 1]  and  v  in [0,2 pi) 
in such a way as to preserve area by mapping  (x,v) to
(sqrt(1-x^2) cos(v), sqrt(1-x^2) sin(v), x). This is the projection 
which carries points on the sphere (minus the poles) to points on a 
cylinder wrapped around the equator by shining a light straight out from
the axis through the sphere to the cylinder.

On the 3-sphere (and higher) the next variable is selected as  u3=G(x3)
where  x3  is selected uniformly in [0,1] and  G  is the inverse of
the function  C(u) = (1/2)(u+pi/2+sin(u)cos(u)). The next variable
after that is selected similarly using  C(u) = ( cos(u) - sin^3(u)/3 - 1/3).
And so on.

Observe that if  C  can be computed, it is not necessary to be able to
solve for its inverse  G  explicitly. Instead, each of the computations of
y=G(x)  may be written  x=C(y), an equation to be solved for  y  when  x
is known. This is easily handled with Newton's method.

I believe a method of generating numbers randomly with a given distribution
is treated in Knuth's Art of Computer Programming.

==============================================================================
Q7. Can this be generalized to higher-dimensional spheres?

I have melded this into the previous questions -- anyone reading this
who can think of questions particular to higher dimensions should let me
know what ought to go in here.

==============================================================================

Q8. How is this related to collections of linear subspaces?

I put this question here because someone asked me recently about how
to parameterize the set of planes and other linear subspaces of Euclidean
space. I can't quite remember the question, so I'll not make an
answer at this point.

One comment to make is that points on the sphere (or, more precisely,
pairs of antipodal points) correspond to lines through the origin in 
R^n. The planes in  R^n  correspond similarly to great circles (circles
of maximal circumference). If  n=3,  the planes can be parameterized in
a natural way by finding the line perpendicular to them. If you
trace these correspondences through, you'll see that there is a 
natural one-to-one correspondence between great circles on the 2-sphere
and pairs of antipodal points. You can get the circle from the points
as the set of points equidistant from the pair; you can get the pair from
the circle as the only points equidistant from all elements of the circle.

More generally, there is a correspondence between the  k-dimensional
and the n-k dimensional subspaces of  R^n. The family of all k-dimensional
subspaces in  R^n  (or  n-k dimensional subspaces) is known as the
Grassmannian manifold; it is indeed a manifold and has dimension
k(n-k). When  k=1 or k=n-1, this is also known as projective n-1 space;
there is a two-to-one mapping  S^{n-1} --> RP^{n-1}  which simply sends
a point to the line it's on (this map sends antipodal points of  S^{n-1}
to the same element of  RP^{n-1} of course. This map turns  S^{n-1}
into a two-fold cover of  RP^{n-1}; for  n>2  this is the universal
covering of projective space.)

This material is often treated in graduate topology courses, particularly
in a discussion on vector bundles in an algebraic topology course.
You may wish to consult Milnor's book "Characteristic Classes"
(Princeton Univ Press), which is however not elementary.

==============================================================================

Q9. Where can I get the coordinates of the vertices of the Platonic solids?

There are 5 Platonic solids. An interesting but brief discussion (with
pictures) may be found, for example, in Gallian's  "Contemporary
Abstract Algebra",  D C Heath 1986.

Solid		Number of Vertices	# Edges		# Faces
Tetrahedron		4		6		4
Cube			8		12		6
Octahedron		6		12		8
Dodecahedron		20		30		12
Icosahedron		12		30		20

Notice the duality between certain pairs. Also note that V-E+F=2 in
all cases. This is deep, and may be thought of as the first fact in
homology theory.

I will give coordinates of these points (and in indication of the rest
of the structure) in the most compact way I know; if you want the
coordinates so that, for example, the North Pole is one of the vertices,
you'll have to rotate the coordinates (the BASIC program I include has
in it an application of this procedure.)
I have scaled the coordinates so that they lie in the unit sphere, but
this is not always the prettiest form. I have however set it up so that
the coordinates of the dual pairs reflect this duality.

Tetrahedron
The points are (0,0,1), (1/3)(2sqrt(2), 0, -1), and both points
(1/3)(-sqrt(2), +-sqrt(6), -1). All pairs are joined by an edge; all
triples (sets of three points) lie on a common face.

Cube
The 8 points are (+-c, +-c, +-c) where  c=1/sqrt(3) and the plus/minus signs
may be chosen independently. 
The 12 edges join pairs of points which have 2 coordinates equal.
The 6 faces are quadruples of points for which one of the coordinates is 
	constant.

Octahedron
The 6 vertices are of three types: (+-1, 0, 0) (0, +-1, 0) and (0, 0, +-1).
The 12 edges join all pairs except the three pairs of antipodal points.
The 8 faces consist of all triples which include one point of each type.

Icosahedron
(using some information in a post by cjhenrich@delphi.com)
The 12 vertices are of three types: (+-a, +-b, 0), (0, +-a, +-b), and
	(+-b, 0, +-a), where a=sqrt((5+sqrt(5))/10) and b=sqrt((5-sqrt(5))/10)
The 30 edges come in two flavors: there are 24 edges joining points of
	different types such that their common non-zero coordinate is of
	the same sign (e.g., (a, -b, 0) and (0, -a, b) have negative 2nd
	coordinates). There are also 6 edges joining pairs of points of
	the same type for which the sign in front of the  a  are equal
	(e.g.  (a, b, 0)  and  (a, -b, 0).)
The 20 faces are also of two general sorts: There are 8 triplets consisting
	of one point of each type such that whenever two of the points
	have a common non-zero coordinate, those coordinates are of the	
	same sign. Also, there are 12 triplets which contain two points of
	the same type having the same sign 'X' in front of the  a,  and a
	third point having   'X'.b  in that coordinate (e.g., given the
	two points at the end of the last paragraph, the third point on
	a face with them is  (b,0,+-a). )

Dodecahedron: This is dual to the icosahedron
I adapted these coordinates from a post by David Seal.
The 20 vertices include 8 vertices (+-c, +-c, +-c)  (c=1/sqrt(3)) and
	12 of the forms (+-x, +-y, 0), (0, +-x, +-y), (+-y, 0, +-x) where
	x=(sqrt(5)+1)/(2*sqrt(3)) and y=(sqrt(5)-1)/(2*sqrt(3)).
I will leave it to the reader to dualize the construction of the edges
	and vertices of the icosahedron to get the edges and faces of	
	the dodecahedron. (That means I started it but it took too long.
	The edges are the pairs of points of distance sqrt( (2/9)(sqrt(5)-1) )
	from each other.)

==============================================================================

Q10. How come this sounds like sphere packing?

Very observant of you! Actually, there are a lot of questions whose 
answers sound like an enumeration of the Platonic solids. Here is one
way to see a connection.

Suppose you have a packing of Euclidean space with spheres of radius  1.
There is a way to get evenly spaced points on the unit sphere from it.

For any r>0 let a_r be the number of spheres in the packing which are
contained in the ball of radius r centered at the origin.  Note that
if V is the volume of the ball of radius 1 in R^n, then the ball of
radius r has volume V.r^n, so we have an upper bound of a_r <= r^n.
The limit of a_r to r^n as r increases without bound is the 'packing
density' d. Thus for large r we have a_r is roughly d r^n. In
particular, there are roughly d.n.r^(n-1) balls which fit in the
sphere of radius r+1 but not in the sphere of radius r. If we take the
centers of just these balls and scale them back just a bit, we will
get roughly d.n.r^(n-1) points on the sphere of radius r.  Since the
sphere centers are of distance at least 2 from each other, the points
on the sphere will be almost 2 units apart, or further.

Scaling this picture by a factor of r,  we get about  d.n.r^(n-1) points
on the unit sphere, with distances between them not much less than
2/r. This is not really better than we achieved with the method in Q4,
but it has the advantage that we can also place points on the sphere 
corresponding to spheres in the packing which, for example, fit in
the ball of radius  r+1.5, or r+2. Possibly these points, when projected
to the sphere of radius  r, will lie close to other points already
placed, but then again, maybe not.

It is not possible, so far as I know, to go backwards and create a
sphere packing from a distribution on a sphere. The difficulty is that
a sphere packing implies a distribution of arbitrarily many points on
the sphere, and gives these distributions in a coherent way, whereas
an individual distribution is done with just one fixed number of points.

There is abundant literature and a fair amount of controversy about
sphere packings. Certainly the easiest sphere packings to understand
and use are the ones with great regularity: one places a sphere
centered at each point in a crystallographic lattice. An introduction
to these may be found, for example, in Durbin's "Modern algebra"
(Wiley, 1985). One looks at a subgroup of the group of translations in
R^n which is discrete (each group element is far from any other one);
the translates of a single point under this group form a lattice. The
group of symmetries of such a lattice is called a crystallographic
group. Note that there may be some symmetries which leave a point
fixed; the group of these is finite, and indeed there are only a few
possible groups: dropping, if necessary, to a subgroup of index two,
we can assume the group contains only rotations, at which point it
must be cyclic of order 1, 2, 3, 4, or 6; dihedral of order 4, 6, 8,
or 12, or the symmetry groups of the tetrahedron or octahedron.

This topic comes up from time to time in the popular press, during
which an interview with the inimitable John Conway is de rigueur.
There is also some very interesting work on lattices in higher
dimensions, particularly dimensions which are a multiple of 8, such as
the important Leech lattice. The book by Conway and Sloane is full of
such tidbits.

==============================================================================

```
