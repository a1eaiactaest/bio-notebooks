# Notes on Haber Bosch Optimisation
----------------

## First of all, what is Haber Bosch Process?

It is a process used for creation of ammonia. It takes gases: N<sub>2</sub> (nitrogen) and H<sub>2</sub> (hydrogen) and creates NH<sub>3</sub> (ammonia).

The heat this reaction producess is (Δ*H*<sub>rxn</sub> = −91.8 kJ/mol). Which means it is exothermic, because value is negative.

### How to calculate equilibrium constant (K) given temperature (T)?

**Note:** Temperature unit is Kelvin

First calculate delta H which is enthalpy:
```python
delta_H  = lambda T: (405000/T)-55.169*T + 0.024928*(T**2)-6.587*(10**(-7))*(T**3)-78988.22
```

delta S, entropy:
```python
delta_S = lambda T: -55.169*(math.log(T)) + 0.049856*T + 202500/T**2 - 9.88*10**(-7) * T**2 + 99.185
```

Then Gibbs free energy using delta H and delta S:
```python
delta_G =  lambda T: delta_H(T) - T * delta_S(T)
```

Next step is to calculate equilibrium constant itself.   
Known is that `ln(K) = -(delta_G(T)/RT)` for *R* = `8.3143`:.   
Now to calculate `K` having natural logarithm of it.  
Well, natural log has a base of *e*, which is `2.718281...`:   
Hence `K` is:  

```python3
R = 8.314 # Gas constant
ln_K = delta_G(T)/(-R*T)
K  = math.e**ln_K
```


### Notes

>
> rxn = denotes that this change is the enthalpy of reaction
>

>
> enthalpy = Enthalpy ( H ) is the sum of the internal energy ( U ) and the product of pressure and volume ( PV ) given by the equation:
> H = U + PV
>
> It's represented by ΔG


>
> ## Entropy
> Entropy is a state function that is often erroneously referred to as the 'state of disorder' of a system. Qualitatively, entropy is simply a measure how much the energy of atoms and molecules become more spread out in a process and can be defined in terms of statistical probabilities of a system or in terms of the other thermodynamic quantities. Entropy is also the subject of the Second and Third laws of thermodynamics, which describe the changes in entropy of the universe with respect to the system and surroundings, and the entropy of substances, respectively.
>
> It's represented by ΔS


### Useful sources

[https://pl.wikipedia.org/wiki/Sta%C5%82a_r%C3%B3wnowagi]()
