def preenche_divisores(indice, coef):
    divisores = list()
    i = (coef[indice]**2)**0.5
    while i >= (-(coef[indice]**2)**0.5):
        if coef[indice] == 0:
            divisores.append(0)
            break
        if i != 0 and coef[indice]%i == 0:
            divisores.append(i)
        i -= 1
    return divisores

def descobre_raiz(divisores_i, divisores_d):
    global grau
    global coef
    global coef2
    global raizes
    i = ii = c = 0
    y = float()
    pos_raiz = float()
    while ii < len(divisores_i):
        c = 0
        coef2.clear()
        if i < len(divisores_d):
            coef2.append(coef[0])
            pos_raiz = divisores_i[ii]/divisores_d[i]
            y = pos_raiz*coef[c] + coef[c+1]
            coef2.append(y)
            c += 1
            while c < grau:
                y = pos_raiz*y + coef[c+1]
                if y != 0 or (y == 0 and c != grau-1):
                    coef2.append(y)
                c += 1
            if y == 0:
                raizes.append(pos_raiz)
                grau -= 1
                break
            i += 1
        else:
            ii += 1
            i = 0


opcao=1
while opcao == 1:
    grau_inicial = grau = int(input('Informe o grau do polinômio: '))

    coef = list()
    print('Informe os coeficientes:')
    for i in range(0, grau+1):
        coef.append(float(input()))

    divisores = list()
    divisores_i = preenche_divisores(grau, coef)
    divisores_d = preenche_divisores(0, coef)

    coef2 = list()
    raizes = list()
    for i in range(0, grau_inicial):
        descobre_raiz(divisores_i, divisores_d)
        coef.clear()
        for j in range(0,len(coef2)):
            coef.append(coef2[j])
        divisores_i = preenche_divisores(grau, coef)
        divisores_d = preenche_divisores(0, coef)

    print(f'\nAs raízes são: {raizes}')

    opcao=int(input('\nDeseja reiniciar o programa? sim(1) não(0) '))
