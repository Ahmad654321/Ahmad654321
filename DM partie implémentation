def is_powersmooth(x, B):
    dec_fp = list(factor(x))
    for f in dec_fp:
        if f[0]**f[1] > B:
            return false
    return true

def ppcm(a, b):
    return (a * b /gcd(a, b))

def compute_bound(B):
    args = range(2,B+1)
    r = 1
    for i in args:
        r = ppcm(r,i)
    return r

def tronc(M):
    x = M
    T = []
    while x > 1:
        T.append(x)
        x = floor(x>>1)
    T.append(x)
    T.reverse()
    return T

def calcul_x(x1, M, N):
    d = dict([("1", x1)])
    n_dec = Integer(M).digits(base=2) # Decomposition base 2
    n_dec.pop()
    n_dec.reverse()
    e = 1
    d[str(2*e)] = (2*d[str(e)]**2 - 1)%N
    for c in n_dec:
        if c == 0:
            d[str(e*2)] = (2*d[str(e)]**2 - 1)%N # Calcul de x_{2n}
            d[str(e*2+1)] = (2*mul_mod_P(d[str(e)],d[str(e+1)],N) - x1)%N # Calcul de x_{2n+1}
            e = e*2
        else:
            d[str(e*2+1)] = (2*mul_mod_P(d[str(e)],d[str(e+1)],N) - x1)%N # Calcul de x_{2n+1}
            d[str((e+1)*2)] = (2*d[str(e+1)]**2 - 1)%N # Calcul de x_{2n+2}           
            e = e*2+1
    return d[str(M)]

def williams(B,N):
    d = N
    M = compute_bound(B)
    e = tronc(M)
    print(e)
    while d == N:
        x1 = randint(1,N-1)
        d1 = gcd(x1,N)
        if d1 != 1:
            return d1
        xM = calcul_x(x1,M,N)
        d1 = gcd(xM - 1, N)
        print(d1)
        if d1 != 1:
            d = d1
    return d


