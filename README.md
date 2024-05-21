# G/SL2 complementary code 

This is complementary code for the paper "Topological rigidity of $SL_2$-quotients", which was joint work with my PhD supervisor Dmitiry Rumynin.
The paper may be found on arxiv: https://arxiv.org/abs/2309.07238.

## Contents of readme 

1. Overview
2. K-theory-GmodSL2.ipynb - light discussion and how to use
3. KoszulComplex.ipynb - light discussion

## 1. Overview

The paper concerns distinugishing topologial spaces of the form $G/SL_2$, where $G$ is a simply connected simple complex Lie group. Such spaces are obtained as follows:

Let $u$ be a nilpotent element of the lie algebra $\mathfrak{g}$. Then we have an associated map $\phi: \mathfrak{sl}_2(\mathbb{C}) \rightarrow \mathfrak{g}$, and a map of Lie groups $\Phi: SL_2 \rightarrow G$. 

For simply connected $G$, the representation ring $R(G)$ is a polynomial ring. $R(SL_2)$ can be viewed as a $R(G)$ module via restriction of characters (along the map $\Phi$ above).
Also $R(e) = \mathbb{Z}$ is a $R(G)$ module via characters acting by their dimension.

Hodgkins showed there is a spectral sequence $E_2^{-p,0} = Tor^{p}_R(G)(\mathbb{Z},R(SL_2))$ converging to $K^*(G/SL_2)$. Minami showed this sequence collapses on the second page!

By grading considerations we have $K^0(G/SL_2) = \text{Tor}^0 + \text{Tor}^2 + \text{Tor}^4 + \ldots$ and $K^1(G/SL_2) = \text{Tor}^1 + \ldots$.

As discussed, for a given nilpotent element $u \in \mathfrak{g}$ and associated $\Phi$ as above, we get a homogenous space $X_u(G) = G/SL_2$. We have $K^{0,0}(X_u) = \mathbb{Z}[x]/I_u$ for some ideal $I_u$. This ideal turns out to be a topological invariant, that is, $X_u(G) \cong X_v(G) \implies I_u = I_v$. Calculating this ideal is the focus of the code.

## 2. K-theory-GmodSL2.ipynb - light discussion and how to use

As mentioned above, this code aims to calculate $K^{0,0}(X_u) = \mathbb{Z}[x]/I_u$ for a given nilpotent $u \in \mathfrak{g}$. 

When run, the code asks for a group. This is the $'G'$ and should be input in the form [Upper case letter][Group Rank] e.g. $'A2'$ , $'D7'$, $'F4'$, $'E6'$, etc. 

You will then be prompted to input how the neutral element $H \in \mathfrak{sl}_2(\mathbb{C})$ acts on the simple roots of $\mathfrak{g}$. This is an equivalent way of specifying the nilpotent (and hence the copy of $\mathfrak{sl}_2(\mathbb{C})$ ) of $\mathfrak{g}$. This is in turn equivalent to specifiying which sopy of $SL_2 \subset G$ is being considered. More information on how to go from nilpotent elements to actions of $H \in \mathfrak{sl}_2(\mathbb{C})$ can be found in, for example, Collingwood McGovern - Nilpotent Orbits In Semisimple Lie Algebra.

Finally, you will be asked for a characteristic... this is explained now. 

For computational reasons, we do not calculate $\mathbb{Z}[x]/I_u$ but instead $\mathbb{Z}[x]/I_u \otimes \mathbb{F} = \mathbb{F}[x]/(I_u \otimes \mathbb{F})$ for a given prime field $\mathbb{F}$. Of course, this is still an invariant (granted a slightly weaker one). However, in most cases calculation of $ \mathbb{F}[x]/(I_u \otimes \mathbb{F})$ is sufficient (as long as you try enough prime fields $\mathbb{F}$. 

### How to use

K-theory-GmodSL2.ipynb is a file format to be used within a Jupyter Notebook. The code was produced here as it was the easiest way to work with SageMath on my windows machine. To use, download the .ipynb file, open it on a Jupyter Notebook with a sagemath kernel. **This was origianlly run using SageMath-9.2**, however I see no reason why other versions would not work out of the box.


### A final note

The time-consuming part of the code is retreiving the fundamental characters for the given group $G$ and extracting their coefficients and exponents into a format which can be used later in the code. This part of the code is executed after you state the group $G$ and before you are asked to state how $H \in \mathfrak{sl}_2(\mathbb{C})$ acts on the simple roots. 

Once $\mathbb{F}[x]/(I_u \otimes \mathbb{F})$ is printed you will be asked if you wish to give another list of action of $H \in \mathfrak{sl}_2(\mathbb{C})$ on the simple roots of $G$ i.e. do the calculation again for another copy of $SL_2 \subset G$. 'n' is for no and
will stop the code, typing anything else (including 'N') will run the code again and prompt you for the new list and characteristic

Therefore, if you wish to compute $\mathbb{F}[x]/(I_u \otimes \mathbb{F})$ for many nilpotent elements $u \in \mathfrak{g}$ (or many characteristics), you may have an initial wait before inputting the first action on $H$ on the simple roots, but then the calculations will be quick.

## 3. KoszulComplex.ipynb - light discussion 

(For information on how to use see the 'how to use' subsection of '2. K-theory-GmodSL2.ipynb - light discussion and how to use'.)

The spectral sequence $E_2^{-p,0} = Tor^{p}_R(G)(\mathbb{Z},R(SL_2))$ may be calculated using a Koszul Complex. This is done by viewing the $R(G)$ module $\mathbb{Z}$ as $Z[x_1,\ldots,x_n]/(x_1-d_1,\ldots,x_n-d_n)$ where $n$ is the rank of $G$, $x_i$ is the $i^{th}$ fundamental character of $G$ and $d_i$ is its dimension.

The code itself will display a Koszul Complex for a given regular sequence. It is merely for interest in how these Koszul Complexes look and does not do any explicit calculations. 

