Let u be a nilpotent element of sl2(C). Then we have an associated map phi: sl(2) --> g, Phi: SL2 --> G. 

For simply connected G, R(G) is a polynomial ring. 
R(SL2) is a R(G) module via restriction of characters (along the map above).
Also R(e) = Z is a R(G) module via a character acting via it's dimension.

Hodgkins showed there is a spectral sequence E_2^{-p,0} = Tor^{p}_R(G)(Z,R(SL2)) converging to K^*(G/SL2).
Minami showed this sequence collapses on the second page!

By grading considerations we have K^0(G/SL2) = Tor^0 + Tor^2 + Tor^4 + ... and K^1(G/SL2) = Tor^1 + ...

This code computes E_2^{0,0} \otimes F = Tor^0 \otimes F for a given nilpotent u (and thus its associated Phi: SL2 --> G)
where F is a prime field of characteristic 0 or p>0.
