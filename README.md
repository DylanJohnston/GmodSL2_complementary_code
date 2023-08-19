Let u be a nilpotent element of sl2(C). Then we have an associated map phi: sl(2) --> g, Phi: SL2 --> G. 

For simply connected G, R(G) is a polynomial ring. 
R(SL2) is a R(G) module via restriction of characters (along the map above).
Also R(e) = Z is a R(G) module via a character acting via it's dimension.

Hodgkins showed there is a spectral sequence E_2^{-p,0} = Tor^{p}_R(G)(Z,R(SL2)) converging to K^*(G/SL2).
Minami showed this sequence collapses on the second page!

By grading considerations we have K^0(G/SL2) = Tor^0 + Tor^2 + Tor^4 + ... and K^1(G/SL2) = Tor^1 + ...

This code computes E_2^{0,0} \otimes F = Tor^0 \otimes F for a given nilpotent u (and thus its associated Phi: SL2 --> G)
where F is a prime field of characteristic 0 or p>0.

Upon running the code the user will first be asked for a group (e.g. A4, B6, D7, G2). Coefficients and exponents
of the rankG fundamental characters will then calculated and stored in list format ready to be used later. 
(Warning: for rank > 7 this can take a while. This part of the code is likely far from optimised.)

label (R)

Then the user is prompted to give a labelling of the Dynkin diagram i.e. state how the simple roots act on the neutral element
H of sl2 (after mapping along our map phi). Finally the user states the characteristic of the field they want Tor^0 computed over. 

Once the answer is printed the user is asked if they wish to give another labelling of the Dynkin diagram. 'n' is for no and
will stop the code. Anything else will run the code again for the new labelling, resuming from label (R). (Thus, for each group the
time consuming set-up only has to be done once).
