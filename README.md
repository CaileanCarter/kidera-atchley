# Tables of amino acid properties, Kidera factors and Atchley factors.


## Amino acid properties

From here: https://github.com/mikessh/vdjtools/blob/master/src/main/resources/profile/aa_property_table.txt

References: PMID:18946038, PMID:14872534, PMID:16301309, http://arxiv.org/pdf/1502.03136v2.pdf

Copy this code to make an `aa_prop` pandas data frame.

R:
```r
aa_prop = t(data.frame(lapply(strsplit("A,1.29,0.9,0,0.049,1.8,0,0,0.047,0.065,0.78,67,1,0,0,1,1;C,1.11,0.74,0,0.02,2.5,-2,0,0.015,0.015,0.8,86,1,1,-1,0,1;D,1.04,0.72,-1,0.051,-3.5,-2,1,0.071,0.074,1.41,91,1,0,1,1,NA;E,1.44,0.75,-1,0.051,-3.5,-2,1,0.094,0.089,1,109,1,0,1,0,1;F,1.07,1.32,0,0.051,2.8,0,0,0.021,0.029,0.58,135,1,1,-1,0,1;G,0.56,0.92,0,0.06,-0.4,0,0,0.071,0.07,1.64,48,1,0,1,1,1;H,1.22,1.08,0,0.034,-3.2,1,1,0.022,0.025,0.69,118,1,0,-1,0,1;I,0.97,1.45,0,0.047,4.5,0,0,0.032,0.035,0.51,124,1,1,-1,0,1;K,1.23,0.77,1,0.05,-3.9,2,1,0.105,0.08,0.96,135,1,0,1,0,1;L,1.3,1.02,0,0.078,3.8,0,0,0.052,0.063,0.59,124,1,1,-1,1,1;M,1.47,0.97,0,0.027,1.9,0,0,0.017,0.016,0.39,124,1,1,1,0,1;N,0.9,0.76,0,0.058,-3.5,0,1,0.062,0.053,1.28,96,1,0,1,1,1;P,0.52,0.64,0,0.051,-1.6,0,0,0.052,0.054,1.91,90,1,0,1,0,1;Q,1.27,0.8,0,0.051,-3.5,1,1,0.053,0.051,0.97,114,1,0,1,0,1;R,0.96,0.99,1,0.066,-4.5,2,1,0.068,0.059,0.88,148,1,0,1,1,1;S,0.82,0.95,0,0.057,-0.8,-1,1,0.072,0.071,1.33,73,1,0,1,1,1;T,0.82,1.21,0,0.064,-0.7,-1,0,0.064,0.065,1.03,93,1,0,0,1,1;V,0.91,1.49,0,0.049,4.2,0,0,0.048,0.048,0.47,105,1,1,-1,0,1;W,0.99,1.14,0,0.022,-0.9,1,1,0.007,0.012,0.75,163,1,1,-1,0,1;Y,0.72,1.25,0,0.07,-1.3,-1,1,0.032,0.033,1.05,141,1,1,-1,1,1", ";")[[1]], function (x) { strsplit(x, ",")[[1]] } ))); aa_prop = data.frame(aa_prop[,1], apply(aa_prop[, 2:17], 2, as.numeric)); aa_prop[,1] = as.character(aa_prop[,1]); row.names(aa_prop) = aa_prop[,1]; names(aa_prop) = c("amino.acid", 'alpha','beta','charge','core','hydropathy','pH','polarity','rim','surface','turn','volume','count','strength','disorder','high_contact','count')
```

Python:
```python
aa_prop = pd.DataFrame(map(lambda x: x.split(","), "A,1.29,0.9,0,0.049,1.8,0,0,0.047,0.065,0.78,67,1,0,0,1,1;C,1.11,0.74,0,0.02,2.5,-2,0,0.015,0.015,0.8,86,1,1,-1,0,1;D,1.04,0.72,-1,0.051,-3.5,-2,1,0.071,0.074,1.41,91,1,0,1,1;E,1.44,0.75,-1,0.051,-3.5,-2,1,0.094,0.089,1,109,1,0,1,0,1;F,1.07,1.32,0,0.051,2.8,0,0,0.021,0.029,0.58,135,1,1,-1,0,1;G,0.56,0.92,0,0.06,-0.4,0,0,0.071,0.07,1.64,48,1,0,1,1,1;H,1.22,1.08,0,0.034,-3.2,1,1,0.022,0.025,0.69,118,1,0,-1,0,1;I,0.97,1.45,0,0.047,4.5,0,0,0.032,0.035,0.51,124,1,1,-1,0,1;K,1.23,0.77,1,0.05,-3.9,2,1,0.105,0.08,0.96,135,1,0,1,0,1;L,1.3,1.02,0,0.078,3.8,0,0,0.052,0.063,0.59,124,1,1,-1,1,1;M,1.47,0.97,0,0.027,1.9,0,0,0.017,0.016,0.39,124,1,1,1,0,1;N,0.9,0.76,0,0.058,-3.5,0,1,0.062,0.053,1.28,96,1,0,1,1,1;P,0.52,0.64,0,0.051,-1.6,0,0,0.052,0.054,1.91,90,1,0,1,0,1;Q,1.27,0.8,0,0.051,-3.5,1,1,0.053,0.051,0.97,114,1,0,1,0,1;R,0.96,0.99,1,0.066,-4.5,2,1,0.068,0.059,0.88,148,1,0,1,1,1;S,0.82,0.95,0,0.057,-0.8,-1,1,0.072,0.071,1.33,73,1,0,1,1,1;T,0.82,1.21,0,0.064,-0.7,-1,0,0.064,0.065,1.03,93,1,0,0,1,1;V,0.91,1.49,0,0.049,4.2,0,0,0.048,0.048,0.47,105,1,1,-1,0,1;W,0.99,1.14,0,0.022,-0.9,1,1,0.007,0.012,0.75,163,1,1,-1,0,1;Y,0.72,1.25,0,0.07,-1.3,-1,1,0.032,0.033,1.05,141,1,1,-1,1,1".split(";")), columns=['aminoacid', 'alpha', 'beta', 'charge', 'core', 'hydropathy', 'pH', 'polarity', 'rim', 'surface', 'turn', 'volume', 'count', 'strength', 'disorder', 'high_contact', 'count'], index=['A', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'K', 'L', 'M', 'N', 'P', 'Q', 'R', 'S', 'T', 'V', 'W', 'Y'])
```


## Kidera factors
Free paper with kidera factors table: http://www.jbsdonline.com/mc_images/category/4308/14-scheraga_jbsd_28_4.pdf

Copy this code to make a `kidera` R data frame / pandas data frame.

R:
```r
kidera = t(data.frame(lapply(strsplit("A,-1.56,-1.67,-0.97,-0.27,-0.93,-0.78,-0.2,-0.08,0.21,-0.48;R,0.22,1.27,1.37,1.87,-1.7,0.46,0.92,-0.39,0.23,0.93;N,1.14,-0.07,-0.12,0.81,0.18,0.37,-0.09,1.23,1.1,-1.73;D,0.58,-0.22,-1.58,0.81,-0.92,0.15,-1.52,0.47,0.76,0.7;C,0.12,-0.89,0.45,-1.05,-0.71,2.41,1.52,-0.69,1.13,1.1;Q,-0.47,0.24,0.07,1.1,1.1,0.59,0.84,-0.71,-0.03,-2.33;E,-1.45,0.19,-1.61,1.17,-1.31,0.4,0.04,0.38,-0.35,-0.12;G,1.46,-1.96,-0.23,-0.16,0.1,-0.11,1.32,2.36,-1.66,0.46;H,-0.41,0.52,-0.28,0.28,1.61,1.01,-1.85,0.47,1.13,1.63;I,-0.73,-0.16,1.79,-0.77,-0.54,0.03,-0.83,0.51,0.66,-1.78;L,-1.04,0,-0.24,-1.1,-0.55,-2.05,0.96,-0.76,0.45,0.93;K,-0.34,0.82,-0.23,1.7,1.54,-1.62,1.15,-0.08,-0.48,0.6;M,-1.4,0.18,-0.42,-0.73,2,1.52,0.26,0.11,-1.27,0.27;F,-0.21,0.98,-0.36,-1.43,0.22,-0.81,0.67,1.1,1.71,-0.44;P,2.06,-0.33,-1.15,-0.75,0.88,-0.45,0.3,-2.3,0.74,-0.28;S,0.81,-1.08,0.16,0.42,-0.21,-0.43,-1.89,-1.15,-0.97,-0.23;T,0.26,-0.7,1.21,0.63,-0.1,0.21,0.24,-1.15,-0.56,0.19;W,0.3,2.1,-0.72,-1.57,-1.16,0.57,-0.48,-0.4,-2.3,-0.6;Y,1.38,1.48,0.8,-0.56,0,-0.68,-0.31,1.03,-0.05,0.53;V,-0.74,-0.71,2.04,-0.4,0.5,-0.81,-1.07,0.06,-0.46,0.65", ";")[[1]], function (x) { strsplit(x, ",")[[1]] } ))); kidera = data.frame(kidera[,1], apply(kidera[, 2:11], 2, as.numeric)); kidera[,1] = as.character(kidera[,1]); row.names(kidera) = kidera[,1]; names(kidera) = c("amino.acid", "f1", "f2", "f3", "f4", "f5", "f6", "f7", "f8", "f9", "f10")
```

Python:
```python
kidera = pd.DataFrame(map(lambda x: x.split(","), "A,-1.56,-1.67,-0.97,-0.27,-0.93,-0.78,-0.2,-0.08,0.21,-0.48;R,0.22,1.27,1.37,1.87,-1.7,0.46,0.92,-0.39,0.23,0.93;N,1.14,-0.07,-0.12,0.81,0.18,0.37,-0.09,1.23,1.1,-1.73;D,0.58,-0.22,-1.58,0.81,-0.92,0.15,-1.52,0.47,0.76,0.7;C,0.12,-0.89,0.45,-1.05,-0.71,2.41,1.52,-0.69,1.13,1.1;Q,-0.47,0.24,0.07,1.1,1.1,0.59,0.84,-0.71,-0.03,-2.33;E,-1.45,0.19,-1.61,1.17,-1.31,0.4,0.04,0.38,-0.35,-0.12;G,1.46,-1.96,-0.23,-0.16,0.1,-0.11,1.32,2.36,-1.66,0.46;H,-0.41,0.52,-0.28,0.28,1.61,1.01,-1.85,0.47,1.13,1.63;I,-0.73,-0.16,1.79,-0.77,-0.54,0.03,-0.83,0.51,0.66,-1.78;L,-1.04,0,-0.24,-1.1,-0.55,-2.05,0.96,-0.76,0.45,0.93;K,-0.34,0.82,-0.23,1.7,1.54,-1.62,1.15,-0.08,-0.48,0.6;M,-1.4,0.18,-0.42,-0.73,2,1.52,0.26,0.11,-1.27,0.27;F,-0.21,0.98,-0.36,-1.43,0.22,-0.81,0.67,1.1,1.71,-0.44;P,2.06,-0.33,-1.15,-0.75,0.88,-0.45,0.3,-2.3,0.74,-0.28;S,0.81,-1.08,0.16,0.42,-0.21,-0.43,-1.89,-1.15,-0.97,-0.23;T,0.26,-0.7,1.21,0.63,-0.1,0.21,0.24,-1.15,-0.56,0.19;W,0.3,2.1,-0.72,-1.57,-1.16,0.57,-0.48,-0.4,-2.3,-0.6;Y,1.38,1.48,0.8,-0.56,0,-0.68,-0.31,1.03,-0.05,0.53;V,-0.74,-0.71,2.04,-0.4,0.5,-0.81,-1.07,0.06,-0.46,0.65".split(";")), index=["A","R","N","D","C","Q","E","G","H","I","L","K","M","F","P","S","T","W","Y","V"], columns=["aminoacid"] + list(map(lambda x: "f"+str(x), range(1,11))))
```


## Atchley factors
Atchley factors paper:
http://www.pnas.org/content/102/18/6395.full


http://www.pnas.org/content/106/34/14345.full


