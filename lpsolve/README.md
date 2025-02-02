**NOTE:** The following text is an excerpt from [the official website](http://lpsolve.sourceforge.net).

# lp_solve
lp_solve is a **free** (see [LGPL](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.txt) for the GNU lesser general public license) linear (integer) programming solver based on the revised simplex method and the Branch-and-bound method for the integers.

lp_solve solves pure linear, (mixed) integer/binary, semi-continuous and special ordered sets (SOS) models. Note the word linear. This means that equations must be of the first order. `5 * x - 3 * y` is an example. However `x * y` is not linear and cannot be handled by lp_solve. Both the objective function and the constraints have this restriction.

Via the Branch-and-bound algorithm, it can handle integer variables, semi-continuous variables and Special Ordered Sets.

lp_solve has no limit on model size and accepts standard both lp or mps input files, but even that can be extended. Note however that some models could give lp_solve a hard time and will even fail to solve. The larger the model the likely the chance for that. But even commercial solvers have problems with that.
