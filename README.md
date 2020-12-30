# singular_cubic_threefolds
Given a (possibly singular) projective cubic threefold X := V(F) over a finite field k = GF(q,'a'),
we provide algorithms to compute the "error count" E_X(q) := |X(k)| - |P^3(k)|.

We also compute related objects of interest
(which may help to provide useful theoretical upper bounds on |E_X(q)|).
Most of our functions are geared specifically towards the family of hyperplane sections V_c := V(x_1^3+...+x_6^3, c_1x_1+...+c_6x_6),
but the underlying techniques are more general.

Our methods range from naive "for loops"
(general but inefficient for all but small q's)
to more refined techniques based on writing X as a "conic bundle"
(as in https://github.com/alaface/CubLin, but more generally).

## Main functions
The file finder
https://github.com/wangyangvictor/singular_cubic_threefolds/find/main
links to the following functions,
which we have listed below in a "logically valid" order
(respecting the dependencies between the functions):
- **LazyErrorRatio**(c,k),
computing the "ratio" E_X(q)/q for arbitrary V_c:
based on the internal naive counting function **LazyErrorCount**(F,k) for arbitrary V(F).
- **AbsFactorType**(P, mult, k),
giving the *absolute* factorization of an arbitrary polynomial P (raised to the power of mult),
over a *finite* field k.
- **StdConicBundleErrorCount**(F,k,**print_options),
computing the "count" E_X(q) for most F in a "standard conic bundle form" (described in the file).
Includes "print options" (described in the file) that can sometimes provide theoretically useful data,
but which require loading **AbsFactorType**(P, mult, k).
- **CleanLineErrorRatio**(c,k),
computing the "ratio" E_X(q)/q for most V_c:
reducing to **StdConicBundleErrorCount**(F,k),
by using a specific line L coming from a 2-plane on V(x_1^3+...+x_6^3).
- **ConvenientLineErrorRatio**(c,k,**print_options),
computing the "ratio" E_X(q)/q for most *singular* V_c:
reducing to **StdConicBundleErrorCount**(F,k,**print_options),
by using a ("theoretically convenient") line L passing through as many singularities of V_c as possible.
Includes "print options" (described in the file) that can sometimes provide theoretically useful data,
but which require loading **AbsFactorType**(P, mult, k).

("Archive of ideas for ConvenientLineErrorRatio..." sketches possible alternative versions of ConvenientLineErrorRatio.)

## Tests and data (preliminary)
- Data for F_q-points on singular cubic threefolds V_c (hyperplane sections of Fermat).xlsx
ensures that LazyErrorRatio, CleanLineErrorRatio, and ConvenientLineErrorRatio are consistent
(i.e. give the same answer for E_X(q)/q).
- Data for F_q-points on singular cubic threefolds X (in general).xlsx
ensures that LazyErrorCount and StdConicBundleErrorCount are consistent.
- Singular cubic threefold test 1.txt
was used to produce part of "Data for F_q-points on singular cubic threefolds V_c (hyperplane sections of Fermat).xlsx".
- Singular cubic threefold test 2.txt
was used to produce part of "Data for F_q-points on singular cubic threefolds X (in general).xlsx".
- Singular cubic threefold tests 3.?
use CleanLineErrorRatio to provide some preliminary data on V_c.
- Singular cubic threefold tests 4.?
use ConvenientLineErrorRatio to provide some preliminary data on V_c
(including some useful theoretical data not detected by CleanLineErrorRatio).

Disclaimer: Some of the data was produced using earlier versions of the functions,
so for safety, a "double consistency check"
(i.e. attempting to reproduce some old data using the updated functions)
would be useful at some point.
