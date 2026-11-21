# Can split and inert primes expose a zero near the centre?

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24415590.svg)](https://doi.org/10.5281/zenodo.24415590)

This result is now maintained in [quadratic-mertens-first-crossings](https://github.com/leecrossley/quadratic-mertens-first-crossings/tree/main/results/split-inert-prime-test-obstruction). This repository is archived and keeps its releases and DOI.

A proposed route to a negative Mertens average uses two inequalities for signed prime sums. If the average stays nonnegative through a long interval, both inequalities must hold. Reversing either one with enough margin would give a negative start. [Original tests](https://github.com/leecrossley/quadratic-mertens-first-crossings/blob/ef3e53c/results/signed-prime-tails/PRIME-TEST.md)

For a genuine positive quadratic discriminant $`d`$, assume RH for the Riemann zeta function and GRH for $`L(s,\chi_d)`$. Alpöge's announced Dirichlet GRH theorem supplies this input. A central zero or a conjugate pair with positive ordinate at most $`\pi/H`$ forces the first sum **below −0.52** for every sufficiently large $`d`$ and $`H\ge4\log(3d)`$. The proposed contradiction would require a value above a threshold near −0.5. [Scalar estimate](PROOF.md#the-scalar-test-in-genuine-fields) · [Announcement](https://alpo.ge/remark.pdf) · [Independent formal checks](https://math.mit.edu/~drew/grh/)

For every sufficiently large packet spacing $`P`$, the second test admits an assignment of split and inert signs to ordinary primes. The proof does not quantify how large $`P`$ must be. The construction assumes RH for the zeta function and GRH for $`L(s,\chi_5)`$. With a double central zero, its weighted average stays positive at every real start $`y\ge2`$, and every finite matrix of the tested frequencies meets the necessary bound. Given any fixed $`a>0`$, one can instead choose a close pair so that positivity holds throughout $`2\le y\le D^a`$, where $`D`$ is the reference parameter. These signs extend completely multiplicatively. The comparison with actual fields also uses GRH for the quadratic twists by $`\chi_5`$. A bound for all sufficiently large Yokoi fields remains open. [Construction and comparison](PROOF.md) · [Prior work and scope](PRIOR-WORK.md)

## Reproduce the checks

~~~sh
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -r requirements.txt
sh verify-release.sh
~~~

The program selects ordinary primes of the prescribed signs and checks two independent evaluations of the local product changes. For packets 2, 3 and 4 it tests the prime-power sums at two frequencies against allowances with fixed coefficients 12 and 8. A second program sums the actual grid ordinates and compares them with the triangular Fourier polynomial, including a cut at a grid frequency. The estimates uniform in the parameter and starting point are proved analytically. [Finite check output](evidence/check.txt)

Two Lean lemmas verify positivity of cosine difference matrices and preservation of any positive kernel under multiplication by such a cosine. Use Lean 4.33.1 and Mathlib revision 0df444a360eaa60ab8c11dca51a86af692955474. From that Mathlib checkout run the following, replacing the path with the local file. [Lean source](PrimeSigns.lean) · [Kernel output](evidence/lean.txt)

~~~sh
lake env lean /absolute/path/to/PrimeSigns.lean
~~~
